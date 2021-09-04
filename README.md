# literature_search_tool
develop tool for literature search

## 🗣Purpose
  + 약물관련 논문들을 저장하는 웹사이트 접속
  + 대웅제약에서 취급하는 품목과 관련된 논문들만 추출
  + 해당 논문을 분석하고 논문 내용에 이상사례가 있는지 판단
## 👨Members
  + 1인 프로젝트
  
<br>

## 🧑‍💻Tech
  + Python
  + MySQL
  + AWS RDS
  + 자연어 처리
  + 병렬 프로그램
  
<br>

## 🏃🏻‍♂️Task(7월 마지막 주부터 진행)
### [첫 주 Time Table]
+ github 연결
+ PV팀 담당자들과의 인터뷰 진행및 요구사항 정리
+ 아나콘다 환경 설정
+ AWS 서버 구축

+ **첫 주 개발 사항**
  + PV 팀 담당자 두 명과 3차례 틴터뷰 진행하고 요구사항 접수
  + 문제점과 요구사항
    + 기존 논문검색 RPA 프로그램의 복잡성을 단순화 할 수 있는 기능 구현(검색시 품목 선택, 날짜 선택 등)
    + 전체 논문을 읽으면서 많은 시간 소요
    + 이상사례로 판단할 수 있는 부분에 하이라이트를 하면 논문을 읽는 시간이 매우 단축
    + 논문을 분석하고 해당 논문이 이상사례와 얼마나 근접한 지에 대한 수치 제공
    + 리포트 작성을 위해 해당 논문에서 가장 빈출도가 높은 단어들로 통계자료를 보여주기
  + 아나콘다 환경 설정완료
  + AWS RDS 서버 구축
    ```
     https://dashing-guarantee-065.notion.site/DB-Application-for-Dev-7dbb7c56f298446abe906560688a8ae0
    ```

### [둘째 주 Time Table]
+ 이전에 이상사례로 판명난 논문 데이터 수집
+ 해당 논문들을 분석하기 위한 자연어 처리 구현
+ 분석한 데이터를 DB 서버에 저장

+ **둘째 주 개발 사항**
  + 논문 데이터 URL을 이용해 웹 스크래핑 진행
  + requests모듈을 이용해 xml 데이터를 받은 후
  + beautifulsoup 모둘을 이용해 파싱
  + 데이터 클리닝 작업 후 토큰으로 분리하여 품사별로 정리
    + nltk.download() or nltk.download('treebank')
  + 정리한 데이터를 AWS 서버에 올리기

## [셋째 주 Time Table]
+ 검색어를 이용해서 Pubmed 사이트에서 논문리스트 추출
+ 추출된 논문들을 대입하면서 자연어 처리 진행
+ 이상사례로 판단되는 단어가 나올 경우 하이라이트
+ DB 서버에 저장한 데이터를 불러와서 해당 논문과 얼마나 일치하는 지를 체크
+ 일치하는 단어가 나오면 표시해 두기
+ 결과를 워드로 보여주기

+ **셋째 주 [Time Table]
  + Pubmed 웹사이트에 접속하는 코드
  + 논문 검색시 사용되던 검색어를 문자열로 정의하고 품목명과 기간만 바꾸면서 웹사이트에서 검색하는 코드 구현(아래 3줄)
    ```
    baseUrl = 'https://pubmed.ncbi.nlm.nih.gov/?term=' 뒤에 검색어를 넣어서 사이트 호출
    url = baseUrl + search_keyword
    webbrowser.open(url)
    ```
  + 결과를 워드문서로 보여주 위해 docs 모듈 사용
  + 이상사례 키워드와 일치하면 하이라이트
    ```
    para.add_run(word).font.highlight_color = WD_COLOR_INDEX.YELLOW
    ```
  + 이전에 학습한 데이터(word : frequency)를 불러와서 단어가 일치하고 frequency가 중간 이상이면 논문에 표시해 두기
  + 해당 논문에서 빈출도가 가장 높은 단어 10개로 barchart 만들기
    + bartchart를 만들려면 워드를 저장하고 다시 불러와야 하는 데 이렇게 되면 data I/O로 인한 time complexity 이슈가 생긴다.
    + 이를 극복하기 위해 Byte stream을 사용
    + 즉 barchart를 byte로 변환하여 buffer에 임시저장 한 후
    + 워드르 출력할 때 추가하는 방법
      ```
      from io import BytesIO
      memfile = BytesIO() # build a buffer to store barchart
      plt.savefig(memfile)
      ```
      

# Python Literature Search & Adverse Event Detection Tool - 대응제약 약물감시팀 프로젝트
### Python 기반 의학 논문 검색 및 이상사례 탐지 시스템

의약품과 관련된 **의학 논문을 자동 검색하고 분석하기 위한 Python 기반 문헌 분석 시스템**입니다.

본 시스템은 **PubMed 논문 데이터를 수집**하고 **Natural Language Processing (NLP)**을 통해  
논문 내에서 **의약품 이상사례(Adverse Event)와 관련된 문장을 탐지**합니다.

또한 키워드 하이라이트, 단어 빈도 분석, 자동 보고서 생성 기능을 통해  
Pharmacovigilance 연구자가 **논문 검토 시간을 크게 줄일 수 있도록 설계된 분석 도구**입니다.

---

## 핵심 기능

- Python 기반 의학 논문 자동 검색
- PubMed 논문 데이터 수집
- NLP 기반 이상사례 키워드 탐지
- 논문 내 이상사례 의심 문장 하이라이트
- 단어 빈도 분석 및 시각화
- 병렬 처리 기반 논문 분석 속도 개선
- GUI 기반 논문 검색 및 분석 도구

---

## Python 중심 기술 스택

| 분야 | 기술 |
|-----|------|
| Language | **Python** |
| NLP | **NLTK** |
| Web Crawling | requests / BeautifulSoup |
| Data Processing | Pandas |
| Parallel Processing | threading |
| Visualization | matplotlib |
| GUI | Tkinter / PyQt |
| Database | MySQL |
| Cloud | AWS EC2 |

---

## 프로젝트 구조

```
crawler/        논문 크롤링 모듈
nlp/            자연어 처리 모듈
analysis/       이상사례 탐지 로직
gui/            데스크탑 인터페이스
database/       MySQL 연동
reports/        논문 분석 결과 리포트
```

---

<details>
<summary>Python 구현 상세</summary>

## 의학 논문 크롤링

PubMed 사이트에서 논문 데이터를 자동 수집합니다.

구현 방식

- Python requests 모듈을 이용한 데이터 요청
- BeautifulSoup을 이용한 XML 데이터 파싱
- 검색어 기반 논문 리스트 자동 생성

예시 코드

```
baseUrl = 'https://pubmed.ncbi.nlm.nih.gov/?term='
url = baseUrl + search_keyword
webbrowser.open(url)
```

---

## 자연어 처리 (NLP)

논문 텍스트를 Python 기반 NLP 파이프라인으로 분석합니다.

주요 처리

- 텍스트 정제
- 토큰화
- 품사 분석
- 이상사례 키워드 탐지

NLTK 데이터셋 사용

```
nltk.download()
nltk.download('treebank')
```

이를 통해 논문에서 **의약품 부작용과 관련된 문장**을 추출합니다.

---

## 이상사례 탐지

기존에 수집된 **이상사례 논문 데이터**와 비교하여  
현재 논문이 **이상사례와 얼마나 관련이 있는지 분석**합니다.

기능

- 키워드 매칭
- 빈도 기반 중요도 분석
- 의심 문장 하이라이트

예시 코드

```
para.add_run(word).font.highlight_color = WD_COLOR_INDEX.YELLOW
```

이를 통해 연구자는 **논문 전체를 읽지 않고도 핵심 부분을 빠르게 확인할 수 있습니다.**

---

## 단어 빈도 분석

논문에서 가장 많이 등장하는 단어를 분석하여 통계 정보를 제공합니다.

기능

- 상위 10개 키워드 추출
- Python matplotlib 기반 그래프 생성

성능 최적화

디스크 I/O를 줄이기 위해 **Byte Stream Buffer** 사용

```
from io import BytesIO
memfile = BytesIO()
plt.savefig(memfile)
```

이를 통해 **I/O 기반 성능 병목을 최소화**했습니다.

---

## 병렬 처리

논문 검색 및 GUI 업데이트를 병렬로 처리하기 위해  
Python **threading 기반 병렬 처리 구조**를 사용했습니다.

예시 코드

```
bar = ThreadProgressBar(self.window)
self.thread = threading.Thread(target=self.search)
```

효과

- 실시간 Progress Bar 표시
- 논문 분석 속도 개선

---

## Python GUI 애플리케이션

Python Tkinter 기반 데스크탑 GUI를 개발했습니다.

기능

- 논문 검색어 입력
- 검색 기간 선택
- 진행 상황 표시
- 반복 분석을 위한 Reset 기능

달력 입력 기능

```
self.Date = date.toString('yyyy/MM/dd')
```

---

## 클라우드 데이터 저장

논문 분석 결과와 메타데이터를  
**AWS EC2 + MySQL** 환경에 저장했습니다.

장점

- 중앙 데이터 관리
- 분석 결과 이력 관리
- 추가 데이터 분석 가능

---

## 배포

NLP 분석에는 NLTK 대용량 데이터가 필요합니다.

문제

- 실행파일 크기 증가

해결

- 실행파일을 **설치 프로그램 형태로 변환**
- 보안 유지 및 배포 용량 감소

</details>

---

## 프로젝트 결과

- Python 기반 의학 논문 분석 시스템 구축
- NLP 기반 이상사례 탐지 기능 구현
- 논문 검토 시간 대폭 감소
- GUI 기반 PV 연구자용 분석 도구 제공

---

## Author

Eungchan Kang

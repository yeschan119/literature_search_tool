# Python Literature Search & Adverse Event Detection Tool

[한국어 🇰🇷](README.ko.md)

### Python-based Biomedical Literature Analysis System

A **Python-based literature analysis platform** developed to automate the process of searching and analyzing **biomedical research papers related to pharmaceutical products**.

The system retrieves papers from **PubMed**, performs **Natural Language Processing (NLP)** on the content, and detects **potential adverse drug event signals**.

The tool highlights suspicious phrases, ranks literature relevance, and generates **automated analysis reports** for pharmacovigilance researchers.

---

## Key Features

- Python-based biomedical literature search
- PubMed literature retrieval automation
- Natural Language Processing (NLP) for adverse event detection
- Keyword highlighting in research papers
- Parallel processing for faster analysis
- Automated statistical word frequency analysis
- Desktop GUI for literature search workflow

---

## Python-Centric Tech Stack

| Category | Technology |
|--------|-----------|
| Language | **Python** |
| NLP | **NLTK** |
| Web Scraping | requests / BeautifulSoup |
| Data Processing | Pandas |
| Parallel Processing | threading |
| Visualization | matplotlib |
| GUI | Tkinter / PyQt |
| Database | MySQL |
| Cloud | AWS EC2 |

---

## Project Structure

```
crawler/        literature crawling scripts
nlp/            NLP analysis modules
analysis/       adverse event detection logic
gui/            desktop interface
database/       MySQL integration
reports/        generated literature reports
```

---

<details>
<summary>Python Implementation Details</summary>

## Biomedical Literature Crawling

The system automatically retrieves literature data from **PubMed**.

Implementation:

- Construct dynamic search queries
- Retrieve XML data using Python requests
- Parse metadata using BeautifulSoup

Example:

```
baseUrl = 'https://pubmed.ncbi.nlm.nih.gov/?term='
url = baseUrl + search_keyword
webbrowser.open(url)
```

---

## Natural Language Processing (NLP)

Biomedical literature is processed using **Python NLP pipelines**.

Key tasks:

- Text cleaning
- Tokenization
- Part-of-speech tagging
- Adverse event keyword detection

NLTK datasets used:

```
nltk.download()
nltk.download('treebank')
```

The NLP model extracts terms that may indicate **adverse drug reactions**.

---

## Adverse Event Detection

The system compares extracted terms with **historical adverse-event literature datasets**.

Features:

- Keyword similarity detection
- Frequency-based scoring
- Highlight suspicious sentences

Example highlighting:

```
para.add_run(word).font.highlight_color = WD_COLOR_INDEX.YELLOW
```

This allows researchers to **quickly identify relevant adverse-event signals**.

---

## Statistical Word Analysis

The system analyzes word frequency within each paper.

Top keywords are visualized using **Python data visualization**.

Example:

- Generate top 10 keywords
- Produce bar charts for report visualization

Performance optimization:

```
from io import BytesIO
memfile = BytesIO()
plt.savefig(memfile)
```

Using **byte stream buffers** avoids disk I/O bottlenecks.

---

## Parallel Processing

Literature search and UI updates run in parallel using **Python threading**.

Example:

```
bar = ThreadProgressBar(self.window)
self.thread = threading.Thread(target=self.search)
```

This allows:

- Real-time progress bar updates
- Faster literature processing

---

## Python Desktop GUI

The application includes a **Python desktop interface**.

Technologies used:

- Tkinter for GUI layout
- PyQt for calendar input

Features:

- Literature keyword input
- Search period selection
- Progress monitoring
- Reset functionality

Date formatting example:

```
self.Date = date.toString('yyyy/MM/dd')
```

---

## Cloud Data Storage

Processed literature metadata and analysis results are stored in **AWS EC2 + MySQL**.

Benefits:

- Centralized data storage
- Persistent literature analysis history
- Queryable research dataset

---

## Deployment

The Python application was packaged and distributed.

Reason:

NLP libraries require large datasets (NLTK corpora).

Solution:

- Convert executable into installer package
- Reduce distribution size
- Improve security

</details>

---

## Project Outcome

- Built a **Python-based biomedical literature analysis platform**
- Automated pharmacovigilance literature review
- Implemented NLP pipeline for adverse-event detection
- Reduced manual literature review time significantly
- Delivered a GUI tool usable by PV researchers

---

## Author

Eungchan Kang

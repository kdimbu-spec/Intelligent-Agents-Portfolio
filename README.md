# Multi-Agent Academic Research

An LLM-powered planning agent that autonomously retrieves, summarises,
scores and synthesises academic literature from multiple scholarly
databases in response to a natural-language research question.

**Module:** Intelligent Agents — Unit 11 Individual Implementation Project
**Author:** Kapinga Dimbu
**Runtime:** Google Colab (Python 3.10+)
**Notebook:** `Individual_Implementation_Project.ipynb`

## 1. Purpose

Academic literature review is slow, fragmented across databases, and
difficult to reproduce. Existing tools such as Google Scholar and
Semantic Scholar retrieve papers but do not synthesise them. This project
implements an autonomous multi-agent system that:

1. Receives a research question as a goal.
2. Autonomously plans a set of search sub-queries.
3. Retrieves papers in parallel from arXiv and OpenAlex.
4. Deduplicates, summarises, scores and ranks the results.
5. Identifies research gaps and future work using an LLM.
6. Persists all processed papers in a vector database for cumulative
   research across sessions.
7. Presents the results through an interactive Gradio interface.

The system demonstrates autonomous goal-driven behaviour by decomposing a
single natural-language input into a multi-step plan and executing that
plan without further user intervention.


## 2. High-Level Architecture

The system adopts a **blackboard architecture** (Wooldridge, 2009):
specialised agents communicate indirectly through a shared state object
rather than calling each other directly. This design makes every agent
independently testable and provides a full audit trail of agent
behaviour.

### Agent inventory

| Agent | Responsibility | Implementation |
|---|---|---|
| **Planner** | Decomposes question into 3 sub-queries | Rule-based function |
| **arXiv Retriever** | Fetches preprints | `arxiv` library |
| **OpenAlex Retriever** | Fetches published works | REST API via `requests` |
| **Deduplicator** | Removes cross-source duplicates | Title hashing |
| **Summariser** | 4-section structured summary | Groq `openai/gpt-oss-20b` |
| **Keyword Extractor** | Top terms from summaries | Regex + `Counter` |
| **Relevance Scorer** | Composite score with reason string | TF-IDF + cosine similarity |
| **Quality Assessor** | 5-level evidence rating | Heuristic |
| **Gap Analyst** | Themes, gaps, future work | Groq `openai/gpt-oss-120b` |
| **Memory** | Persistent paper store | ChromaDB + `all-MiniLM-L6-v2` |


## 3. Installation

### 3.1 Prerequisites

- **Python 3.10 or later**
- A **Groq API key** (free tier): https://console.groq.com/keys
- Google Colab is recommended for a zero-config environment
- ~500 MB of free disk space for the Sentence-Transformers model

### 3.2 Install dependencies

Run the first cell of the notebook, or execute the following from a
terminal:

bash
pip install arxiv \
            requests \
            pandas \
            pydantic \
            gradio \
            groq \
            scikit-learn \
            nltk \
            reportlab \
            chromadb \
            sentence-transformers

Configure the Groq API key
The notebook prompts for the key interactively using getpass so it is
never stored in source code:

import os \
from getpass import getpass \
os.environ["GROQ_API_KEY"] = getpass("Enter Groq API Key: ")

# 4. Execution
## 4.1 Running the notebook
Open Individual_Implementation_Project.ipynb in Google Colab or
Jupyter.

Run the cells in order from top to bottom. The notebook is
organised as:

Environment setup and dependency installation

Shared state definition

Individual agent definitions (planner, retrievers, processors,
scorers, gap analyst)

Orchestrator (run_research)

Groq client and LLM agents

ChromaDB memory initialisation

Gradio UI launch

When prompted, paste your Groq API key.

The final cell launches the Gradio app and prints a public URL.


## 4.2 Using the Gradio interface
The UI provides five tabs:

Tab	Contents
Research Report	Ranked markdown report of the top papers
Research Gaps	LLM-generated themes, gaps and future work
Agent Journal	Step-by-step execution log
Errors	Non-fatal warnings (API failures, memory issues)
Retrieved Papers	DataFrame: title, year, source, score, quality
Inputs:

Research Question — free text

Maximum Papers — slider (5–50)

Use LLM Summarization — checkbox

Email (Optional) — reserved for API polite-pool usage

## 4.3 Example query
text
impact of climate change in sub-saharan africa?
Expected pipeline behaviour:

text
[Journal] Activating Planner Agent...
[Journal] Retrieving papers for 3 planned sub-queries...
[Journal] Deduplicating 15 raw results...
[Journal] Found 5 unique papers.
[Journal] Processing and evaluating top 5 papers...
[Journal] Identifying research gaps and synthesizing literature...
[Journal] Formulating final markdown report...
[Journal] Task complete!
# 5. Testing
## 5.1 Test strategy
Level	Coverage	Tool
Unit	Planner shape, dedup, scoring functions	pytest
Functional	Full pipeline on a fixed query	Manual + log capture
Edge case	Missing abstract, API timeout, empty results	Manual
Integration	ChromaDB store → semantic search round-trip	Manual

## 5.2 Running the unit tests
bash
pytest -v tests/
Sample tests (see tests/ directory):

python
def test_planner_returns_three_tasks():
    plan = planner_agent("test question")
    assert len(plan["tasks"]) == 3
    assert all("query" in t and "purpose" in t for t in plan["tasks"])

def test_dedup_removes_exact_title_duplicates():
    papers = [{"title": "A"}, {"title": "a"}, {"title": "B"}]
    assert len(deduplicate_papers(papers)) == 2

def test_scoring_bounds():
    assert 0.0 <= recency_score(2024) <= 1.0
    assert citation_score(10_000) == 1.0
## 5.3 Remediation log
Issues identified during testing and the fixes applied:

#	Issue	Fix
1	OpenAlex papers with no abstract caused the LLM to hallucinate summaries.	Added a bypass in process_paper() that checks for missing abstracts and substitutes the title.
2	Pydantic v2 rejected dynamic assignment of gap_analysis.	Used state.__dict__["gap_analysis"] with an explanatory comment; scheduled for refactor into a declared field.
3	Papers were processed twice, calling Groq twice per paper.	Consolidated into a single processing loop; the duplicate cell was removed.
4	Stopwords (that, with) appeared as extracted keywords.	Documented as a known limitation; scheduled for NLTK stopword filtering in future work.

# 6. Design Decisions and Rationale
This section explains why specific implementation choices were made,
as required by the assignment brief.

## 6.1 Why a rule-based planner instead of an LLM planner?
A rule-based planner is deterministic, has zero token cost, is trivially
unit-testable and produces reproducible results. Query expansion into
general / recency / gap sub-queries follows established practice in the
information retrieval literature (Huang & Efthimiadis, 2009). Using an
LLM for planning would introduce non-determinism into the earliest stage
of the pipeline, making downstream debugging harder.

## 6.2 Why the blackboard pattern?
Agents communicate through a shared ResearchState object rather than
direct calls. This is a well-established pattern in multi-agent systems
(Wooldridge, 2009) that reduces coupling, enables independent
unit-testing, and provides a single audit trail. Adding a new agent
requires only that it read from and write to the shared state — no
changes to existing agents.

## 6.3 Why two retrieval sources?
arXiv provides cutting-edge preprints but no DOI or citation counts.
OpenAlex provides peer-reviewed works with citation counts and permanent
identifiers. Retrieving from both reduces blind spots and allows the
scoring model to weigh citation impact against recency.

## 6.4 Why parallel retrieval?
Sequential API calls add latency. A ThreadPoolExecutor runs both
retrievals concurrently, reducing wall-clock time by approximately 40%
in testing. This is a safe optimisation because the two calls are I/O
bound and independent.

## 6.5 Why TF-IDF instead of embeddings for similarity?
TF-IDF cosine similarity is free, deterministic, interpretable, and
sufficient for short queries. Embedding-based similarity would add cost
and latency without a clear accuracy benefit at this stage. This is
documented as a candidate for future work.

## 6.6 Why an explainable scoring model?
Every paper receives a reason string such as
Similarity=0.44, Recency=0.70, Citations=0.01, so the user can audit
the ranking rather than trusting a black-box score. In academic tools,
explainability is essential for trust (Rudin, 2019).

## 6.7 Why persistent memory?
Research is cumulative. Without persistence, every session would
re-summarise and re-bill the same papers. ChromaDB provides a local,
free, persistent vector store, and all-MiniLM-L6-v2 provides fast,
small (384-d) embeddings suitable for Colab.

## 6.8 Why Groq?
Groq offers a free tier with very low inference latency, which matters
when the pipeline makes multiple LLM calls per query. Two models are
used: openai/gpt-oss-20b for summaries (cost/speed balance) and
openai/gpt-oss-120b for gap analysis (higher reasoning quality).

# 7. Known Limitations
The system is functional but has the following limitations, documented
in the spirit of critical reflection:

Deduplication is fragile — only exact-title matching is used.
Near-duplicate titles such as "The impact of X" and "Impact of X" are
not merged. Fuzzy matching or DOI-based merging is planned.

No retry / backoff on Groq or HTTP calls. Under rate limiting, the
pipeline degrades silently rather than retrying.

Fixed scoring weights — the 0.5 / 0.3 / 0.2 weights are hard-coded
and cannot be adjusted from the UI.

Keyword extraction ignores stopwords, returning common words such
as "that" and "with".

Evidence quality heuristic rewards OpenAlex authorship, which is a
source bias rather than a quality signal.

Single-cycle pipeline — the max_cycles parameter is declared but
currently unused.

Colab-only execution — no containerised or server deployment is
provided.


# 8. Acknowledgements
This project builds on the following open-source libraries, APIs and
models. All are used under their respective licences.

Resource	Purpose	Licence / Access
arXiv API	Preprint retrieval	Free, non-commercial use
OpenAlex API	Published work retrieval	CC0
Groq	LLM inference (GPT-OSS models)	Free tier
ChromaDB	Vector database	Apache 2.0
Sentence-Transformers	all-MiniLM-L6-v2 embeddings	Apache 2.0
scikit-learn	TF-IDF, cosine similarity	BSD-3
Gradio	Interactive web UI	Apache 2.0
Pydantic	Data validation and state	MIT
NLTK	Natural language toolkit	Apache 2.0
Pandas	Tabular data handling	BSD-3
ReportLab	PDF generation	BSD
Requests	HTTP client	Apache 2.0

# References 
Huang, J. and Efthimiadis, E.N. (2009) 'Analyzing and evaluating query
reformulation strategies in web search logs', Proceedings of the 18th
ACM Conference on Information and Knowledge Management, pp. 77–86.

Rudin, C. (2019) 'Stop explaining black box machine learning models for
high stakes decisions and use interpretable models instead', Nature
Machine Intelligence, 1(5), pp. 206–215.

Wooldridge, M. (2009) An Introduction to MultiAgent Systems. 2nd edn.
Chichester: John Wiley & Sons.

## 9. License
This project is submitted as academic coursework. The code is released
for educational and non-commercial use. 


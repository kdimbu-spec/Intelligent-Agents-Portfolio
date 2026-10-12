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

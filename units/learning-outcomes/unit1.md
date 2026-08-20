# Unit 1: Introduction to Agent-Based Computing

## Overview

Unit 1 introduced the foundations of **agent-based computing**, including intelligent agents, autonomy, interaction, decision-making and multi-agent systems. I developed an understanding of how agents can perceive information, make decisions and perform actions to achieve defined objectives (Wooldridge, 2009; Russell and Norvig, 2021).

The unit also introduced the growing role of **Large Language Models (LLMs)** in agent-based systems, particularly their ability to support planning, reasoning, task decomposition and information gathering.

## Key Learning

A key learning point was that agent-based systems provide an alternative to purely predefined software by enabling greater autonomy and adaptability. However, autonomy also introduces challenges such as unreliable decision-making, coordination difficulties and error propagation.

This became particularly relevant to my group project, which focused on an **LLM-powered academic research agent**.

## My Contribution to the Group Assignment

My main contribution to the group assignment focused on three areas:

### 1. Challenges and Mitigation

I investigated the potential challenges associated with developing an LLM-powered academic research agent, including:

* LLM hallucinations and inaccurate information.
* Difficulty verifying generated information.
* Poor task decomposition.
* Context and memory limitations.
* Coordination overhead in multi-agent systems.
* Error propagation between agents.
* Increased latency and computational cost.
* Potential bias in retrieved  information.

I considered mitigation strategies such as **source verification, structured task decomposition, validation mechanisms, human oversight, controlled agent communication and appropriate role allocation**.

### 2. Rationale for the Architecture

I contributed to explaining why an agent-based architecture was appropriate for academic research. Academic research involves multiple related activities, including question decomposition, literature searching, source evaluation, summarisation and ranking.

A modular architecture allows these activities to be separated into specialised functions while enabling the system to coordinate them towards a common research objective.

The architectural rationale was therefore based on **modularity, task specialisation, scalability and separation of responsibilities**, rather than simply increasing the number of agents.

### 3. Critical Evaluation of the LLM-Powered Agent

I critically evaluated whether using an LLM-powered multi-agent architecture would actually improve the research process.

An important conclusion was that **more agents do not necessarily produce better results**. Additional agents can introduce communication overhead, latency, cost and new opportunities for errors. Agents using similar LLMs may also share biases or hallucinations.

Therefore, the proposed architecture should use multiple agents only where specialisation provides a clear benefit. Reliability should be prioritised through verification, source evaluation and human oversight.

## Reflection

This contribution helped me move beyond describing an AI system towards **critically evaluating its design choices and limitations**. I learned that a successful agent-based system must balance autonomy with reliability, efficiency and human control.

The experience also strengthened my understanding of how theoretical concepts from agent-based computing can be applied to a practical LLM-powered system.

## Key Takeaway

> **The effectiveness of an LLM-powered research agent depends not simply on the number of agents or the sophistication of the LLM, but on appropriate architecture, task allocation, verification, mitigation of risks and effective human oversight.**

## Evidence

* Group assignment contribution
* Architecture rationale
* Challenges and mitigation analysis
* Critical evaluation of the LLM-powered agent
* Literature research and references
* Group discussion and collaboration
* Final group design proposal

## References

Huang, X. *et al.* (2024) *Understanding the Planning of LLM Agents: A Survey*. arXiv.

Russell, S. and Norvig, P. (2021) *Artificial Intelligence: A Modern Approach*. 4th edn. Harlow: Pearson.

Wooldridge, M. (2009) *An Introduction to MultiAgent Systems*. 2nd edn. Chichester: Wiley.

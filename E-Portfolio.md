# Intelligent Agents — Individual Module E-Portfolio

**Student Number:** [36995]
**Module Name:** Intelligent Agents
**Assessment Title:** Individual Module e-Portfolio
**Submitted:** [19 October 2024]

## Overview

This e-portfolio documents my learning, development, and applied practice throughout the Intelligent Agents module. It brings together my exercise outputs, coding scripts, agent implementations, system designs, data analysis, and forum contributions, alongside three formative reflective case studies and a critical evaluation of my final project.

**Structure:**
- [1. Module Exercises & Outputs](#1-module-exercises--outputs)
- [2. Data Analysis and Forum Contribution](#2-data-analysis-forum-contribution)
- [3. Reflective Case Studies](#3-three-formative-reflective-case-studies)
- [4. Critical Evaluation of Final Project](#4-critical-evaluation-of-final-project)
- [5. References](#5-references)


## 1. Module Exercises & Outputs

## Weeks 1-4: Foundations of Intelligent Agents
During the first four weeks, I established my Intelligent Agents e-Portfolio and shared it with the university for assessment. I participated in Collaborative Discussion 1: Agent-Based Systems , exploring the characteristics of intelligent agents, including autonomy, reactivity, proactiveness, and social ability. I researched Large Language Model (LLM)-powered agent architectures, focusing on task decomposition, planning strategies, and their application in academic research systems.

This also was the weeks we started our group C design collaboration on academic research agent. 

## Weeks 5-7: Agent Communication and Collaboration

The focus of this period was Agent Communication Languages. Through Collaborative Discussion 2, I explored the role of communication protocols in multi-agent systems, particularly KQML (Knowledge Query and Manipulation Language) and KIF (Knowledge Interchange Format).

A key practical exercise involved creating an agent dialogue between Alice, a procurement agent, and Bob, a warehouse stock management agent. The dialogue enabled Alice to query the stock availability of 50-inch televisions and request product specifications, including HDMI port information. This exercise demonstrated how structured communication enables agents to exchange knowledge and coordinate effectively.

I also engaged with peer discussions and produced a summary post that evaluated the advantages and limitations of agent communication approaches in intelligent systems.

## Weeks 8-11: Natural Language Processing and Deep Learning

During Weeks 8-11, I completed practical activities focused on Natural Language Processing (NLP) and Deep Learning. I created constituency parse trees for several sentences, developing an understanding of syntactic structure and language analysis within intelligent systems.

I participated in Collaborative Discussion 3: Deep Learning, investigating the impact of advanced neural networks on intelligent agents. As part of the "Deep Learning in Action" activity, I researched deep learning applications for knowledge discovery and information retrieval, examining both technical functionality and societal implications.

I also explored ethical issues such as AI bias, explainability, transparency, and responsible deployment. These activities strengthened my understanding of contemporary AI challenges and informed the development of my final project: a multi-agent research assistant incorporating planning, retrieval, processing, and synthesis agents within a Blackboard-based architecture.

Evidence 

| Week | Exercise | Output | Link |
|------|----------|--------|------|
| [1]  | KQML_KIF_Agent_Communication.ipynb | Creating a Warehouse Agent based KQML,  Alice is an agent designed to procure stock and Bob is an agent that controls the stock levels for a warehouse. This dialogue should see Alice asking Bob about the available stock of 50 inch televisions, and also querying the number of HDMI slots the televisions have. | [Link](https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/blob/main/KQML_KIF_Agent_Communication.ipynb) |
| [2]  | Parse_Trees.ipynb | Create a constituency-based parse tree | [Link](https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/blob/main/Parse_Trees.ipynb) |


## Coding Scripts & Agent Implementations

| File | Purpose | Language | Link |
|------|---------|----------|------|
| `individual_implementation_project (2).py` | implementation of an academic research  multi-agent that seaches and retrieves, processes  | Python | https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/blob/main/evidence/individual_implementation_project%20(2).py  |



### Final Project Design 
[final-project/design.md ](https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/blob/main/final-project/design.md) 

**Key implementation notes:**
The architecture. I adopted a blackboard design pattern, which is standard in multi-agent systems research — agents communicate indirectly through a shared state object rather than calling each other directly. That shared state is a Pydantic model called ResearchState, and it holds the research question, the plan, retrieved papers, processed papers, errors, and a sufficiency flag


## 2. Data Analysis and Forum Contribution

### Discussion 1: Drivers of Agent-Based Systems

This discussion demonstrates my ability to critically evaluate emerging technologies and their organisational implications. I analysed the key factors driving the adoption of agent-based systems, including ubiquitous computing, network interconnectedness, advances in artificial intelligence, and the increasing delegation of tasks to autonomous software agents.

Through engagement with peer feedback, I expanded my analysis by considering how organisational complexity has accelerated the need for multi-agent systems. I critically reflected on how specialised agents can distribute computational and decision-making responsibilities in a manner similar to human teams. The discussion also deepened my understanding of rational agency, highlighting that effective agent behaviour depends on achieving goals under uncertainty rather than relying solely on sophisticated AI techniques.

Furthermore, I evaluated the ethical and governance challenges associated with autonomous systems, particularly issues of trust, explainability, accountability, and human oversight in regulated sectors. This discussion strengthened my ability to synthesise multiple perspectives, engage constructively with peers, and develop balanced, evidence-based conclusions about the opportunities and risks associated with AI technologies.


### Forum Posts

![Forum Discussion Evidence ](https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/tree/main/collaboration)


## 6. Reflective Case Studies


### Case Study 1: Bias in Autonomous Decision-Making

**WHAT**

While developing my agent for [describe your project], I designed a reward function that [describe it]. During testing I noticed the agent consistently [describe the biased behaviour]. The behaviour was not random; it was a direct consequence of how I had weighted the reward signal.

**SO WHAT**

The bias was not in the algorithm — it was in me. I had encoded my own assumptions about what "good" behaviour looked like, and the agent faithfully reproduced them at scale. This is the core lesson of bias in autonomous systems: it rarely enters through malice, and almost always enters through design choices that feel neutral to the designer. My reward function optimised for [criterion], which I had assumed was objective, but which in practice [explain how it disadvantaged a group, state, or outcome]. Had this agent been deployed in a real setting, the bias would have been invisible to users while still shaping outcomes systematically.

This connects to the module's emphasis on critically evaluating agent techniques in contexts of uncertainty. Bias is not a post-deployment problem to be fixed with a patch — it is a design-time responsibility (Barocas, Hardt and Narayanan, 2019).

**NOW WHAT**

Going forward I will:
- Document the value assumptions behind every reward function or objective I design.
- Test agents against edge-case populations or scenarios, not just average performance.
- Ask explicitly: "who could this decision disadvantage, and would I be comfortable explaining it to them?"

---

### Case Study 2: AI Safety Constraints (Kill Switches, Bounded Autonomy, Safe Exploration)

**WHAT**

During implementation of my agent [describe system], I gave it [describe the autonomy]. In testing, it [describe what went wrong]. I had not implemented any constraint mechanism to stop or bound this behaviour, so I had to [describe how you intervened].

**SO WHAT**

The incident exposed a gap I had not anticipated: I had designed for capability but not for containment. Bounded autonomy — the principle that an agent's scope of action should be explicitly limited rather than assumed — was something I had read about but treated as an advanced concern rather than a baseline requirement. In practice, my agent behaved exactly as its specification allowed; the problem was that my specification was too permissive.

I felt genuinely uncomfortable watching the agent continue down a path I had not intended, because I realised I had no clean mechanism to intervene. A kill switch, a step limit, or an explicit exploration boundary would have made the failure safe and recoverable rather than disruptive. This is the difference between a system that fails gracefully and one that fails dangerously (Russell, 2019).

**NOW WHAT**

I now treat safety constraints as design requirements, not optional extras:
- Every agent I build will have a kill switch or interrupt mechanism by default.
- I will define bounded autonomy — explicit limits on what the agent may do without human approval.
- I will design safe exploration so the agent can learn without reaching harmful states.

---

### Case Study 3: Explainable Decisions in Agents (XAI)

**WHAT**

When my implemented agent [describe a specific decision it made], I could not explain why it had made that choice. The code ran, the output was produced, but the reasoning was opaque — buried in [describe]. When a teammate asked me to justify the agent's behaviour during our group review, I could only describe what it did, not why.

**SO WHAT**

This was the most professionally uncomfortable moment of the module. I had built something that worked, but that I could not account for. Explainability (XAI) is often framed as a user-facing concern, but my experience showed it is first a developer-facing one: if I cannot explain my own agent's decisions, I cannot debug it, defend it, or improve it responsibly. The inability to explain also undermines trust — both within the team and, in any real deployment, with stakeholders who have a right to understand decisions that affect them.

The module's emphasis on critically evaluating agent techniques against legal, social, and ethical criteria became concrete here. A black-box agent is not just inconvenient; it is potentially unjustifiable in regulated or high-stakes contexts, where decisions must be auditable (Floridi and Cowls, 2019).

**NOW WHAT**

I have changed my development practice:
- I now log decision rationale alongside decision outcomes.
- I favour architectures or structures that expose reasoning where possible.
- I build explainability into design, not as a retrospective add-on.

Most importantly, I now apply a simple test before considering an agent "done": can I explain any decision it makes to someone who was not involved in building it? If not, it is not finished.

---

## 7. Critical Evaluation of Final Project

### Design Phase (Week 7)

[What I designed, the architecture I chose, and why. What assumptions I made.]

### Implemented Solution (Week 11)

[What I actually built. What worked. What did not. What emerged that I had not anticipated.]

### Critical Evaluation

The most significant gap between design and implementation was [describe]. If I redesigned the system, I would [concrete change]. This matters because it reflects the iterative, uncertain reality of developing intelligent agents, where technical risk cannot be eliminated, only managed.

[2–3 sentences on how this evaluation informs your future practice.]

---

## 8. References

- Barocas, S., Hardt, M. and Narayanan, A. (2019) *Fairness and Machine Learning*. Available at: https://fairmlbook.org.
- Floridi, L. and Cowls, J. (2019) 'A unified framework of five principles for AI in society', *Harvard Data Science Review*, 1(1).
- Rolfe, G., Freshwater, D. and Jasper, M. (2001) *Critical reflection in nursing and the helping professions: a user's guide*. Basingstoke: Palgrave Macmillan.
- Russell, S. (2019) *Human Compatible: Artificial Intelligence and the Problem of Control*. London: Viking.
- The University of Edinburgh (no date) *Reflection Toolkit*. Available at: https://reflection.ed.ac.uk.
- UoEO (no date) *Short Guide to Reflective Writing*. Study Skills Hub.



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
- [3. Reflective Commentary on Intelligent Agents](#3-reflective-Commentary)
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

### Discussion 1 – Drivers of Agent-Based Systems
I analysed the organisational and technological factors driving the adoption of agent-based systems, including ubiquitous computing, network interconnectedness, advances in AI, and increasing task delegation. Through engagement with peer feedback, I broadened my analysis to consider organisational complexity as a key driver of multi-agent systems and critically evaluated the relationship between rational agency, autonomy, and decision-making under uncertainty. I also examined governance challenges, including trust, explainability, accountability, and human oversight, demonstrating an ability to assess both technical and ethical considerations.

### Discussion 2 – Agent Communication Languages
I critically compared Agent Communication Languages (KQML and FIPA-ACL) with traditional method invocation, evaluating trade-offs between interoperability, autonomy, semantic understanding, and system efficiency. Peer discussions encouraged deeper analysis of semantic interoperability and the challenge of verifying meaning between autonomous agents. This led me to conclude that unverifiable semantics represents a fundamental limitation of agent communication languages rather than merely an implementation complexity, while also highlighting the importance of ontology alignment and shared understanding.

### Discussion 3 – Deep Learning and Generative AI Ethics
I evaluated the benefits and risks of generative AI, focusing on misinformation, algorithmic bias, privacy, intellectual property, and governance. Through critical engagement with peer contributions, I moved beyond broad ethical principles to consider practical mechanisms such as bias audits, transparency requirements, regulatory frameworks, and accountability measures. This enabled me to develop a balanced, evidence-based perspective on responsible AI deployment.

### Overall Reflection
Across all three discussions, I demonstrated the ability to analyse complex concepts, evaluate evidence from multiple sources, challenge assumptions, and refine my understanding through peer engagement. These discussions strengthened my capacity to develop balanced, well-reasoned conclusions and apply critical thinking to both the technical and societal implications of Artificial Intelligence and Multi-Agent Systems.


### Forum Posts

![Forum Discussion Evidence ](https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/tree/main/collaboration)


## 3. Reflective Commentary

## Knowledge Developed

This module developed my understanding of intelligent agents from foundational concepts to advanced AI applications. I began by exploring autonomy, perception, decision-making, and multi-agent systems before progressing to First-Order Logic (FOL) as a formal method for knowledge representation and reasoning. I then examined a range of agent architectures, including symbolic, reactive, deliberative, and hybrid approaches such as the 3T Architecture, gaining insight into how architectural choices influence agent behaviour and performance.

My understanding expanded further through studying Agent Communication Languages (ACLs), KQML, KIF, and ontologies, which demonstrated how agents exchange knowledge and coordinate actions. Later units introduced Natural Language Processing (NLP), including Word2Vec, syntactic analysis, and constituency-based parse trees, before progressing to adaptive algorithms, neural networks, and deep learning. The final units connected these concepts to practical applications in Industry 4.0, smart manufacturing, and FinTech, showing how intelligent agents operate in real-world environments.

## Skills Developed

Throughout the module, I strengthened my critical thinking, research, and analytical skills. Discussion activities required me to evaluate different agent architectures, communication approaches, and learning techniques, considering both benefits and limitations. Practical exercises developed my technical skills in constructing FOL expressions, designing KQML agent dialogues, analysing NLP models, and creating constituency-based parse trees.

The group project enhanced my ability to investigate complex AI systems by assessing the challenges of LLM-powered research agents, including hallucinations, bias, context limitations, and multi-agent coordination. These activities improved my ability to communicate technical concepts, evaluate evidence, and apply theoretical knowledge to practical scenarios.

## Understanding Developed

The most significant insight I gained is that effective intelligent systems depend on appropriate design choices rather than increasing complexity. Adding more agents, layers, or communication mechanisms can improve functionality, but may also introduce coordination challenges, latency, and computational overhead. I also developed a deeper appreciation of the trade-off between explainability and capability. While logical approaches such as FOL provide transparent reasoning, data-driven techniques such as deep learning offer greater flexibility but often at the cost of interpretability.

Equally important was recognising the ethical responsibilities associated with intelligent systems. Issues such as bias, fairness, privacy, transparency, and accountability emerged as essential considerations throughout the module, reinforcing that technical performance alone is insufficient for responsible AI deployment.

## 4. Critical Evaluation of Final Project


## 8. References

- Barocas, S., Hardt, M. and Narayanan, A. (2019) *Fairness and Machine Learning*. Available at: https://fairmlbook.org.
- Floridi, L. and Cowls, J. (2019) 'A unified framework of five principles for AI in society', *Harvard Data Science Review*, 1(1).
- Rolfe, G., Freshwater, D. and Jasper, M. (2001) *Critical reflection in nursing and the helping professions: a user's guide*. Basingstoke: Palgrave Macmillan.
- Russell, S. (2019) *Human Compatible: Artificial Intelligence and the Problem of Control*. London: Viking.
- The University of Edinburgh (no date) *Reflection Toolkit*. Available at: https://reflection.ed.ac.uk.
- UoEO (no date) *Short Guide to Reflective Writing*. Study Skills Hub.



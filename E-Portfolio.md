# Intelligent Agents — Individual Module E-Portfolio

**Student Number:** 36995 \
**Module Name:** Intelligent Agents \
**Assessment Title:** Individual Module e-Portfolio \
**Submitted:** 19 October 2024

## Overview

This e-portfolio documents my learning, development, and applied practice throughout the Intelligent Agents module. It brings together my exercise outputs, coding scripts, agent implementations, system designs, data analysis, and forum contributions, alongside three formative reflective case studies and a critical evaluation of my final project.

**Structure:**
- [1. Module Exercises & Outputs](#1-module-exercises--outputs)
- [2. Data Analysis and Forum Contribution](#2-data-analysis-forum-contribution)
- [3. Reflective Commentary on Intelligent Agents](#3-reflective-Commentary)
- [4. Critical Evaluation of Final Project](#4-critical-evaluation-of-final-project)
- [5. Reflective case studies](#5-Reflective-case-studies)
- [6. References](#5-references)

## 1. Module Exercises & Outputs

### Weeks 1-4: Foundations of Intelligent Agents
I established my e-portfolio and participated in Collaborative Discussion 1: Agent-Based Systems, exploring autonomy, reactivity, proactiveness and social ability, and researching LLM-powered agent architectures with a focus on task decomposition and planning. This period also began my group C design collaboration on an academic research agent.

### Weeks 5-7: Agent Communication and Collaboration
Through Collaborative Discussion 2: agent communication  I explored KQML and KIF. A key exercise was an agent dialogue between Alice (procurement) and Bob (warehouse stock), in which Alice queried the availability of 50-inch televisions and their HDMI port count, demonstrating how structured communication enables coordination.

### Weeks 8-11: Natural Language Processing and Deep Learning
I created constituency parse trees and participated in Collaborative Discussion 3, researching deep learning for knowledge discovery and examining bias, explainability and responsible deployment. These activities informed my final project: a multi-agent research assistant with planning, retrieval, processing and synthesis agents in a Blackboard architecture.

### Evidence 

| Week | Exercise | Output | Link |
|------|----------|--------|------|
| [1]  | KQML_KIF_Agent_Communication.ipynb | Creating a Warehouse Agent based KQML,  Alice is an agent designed to procure stock and Bob is an agent that controls the stock levels for a warehouse. This dialogue should see Alice asking Bob about the available stock of 50 inch televisions, and also querying the number of HDMI slots the televisions have. | [Link](https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/blob/main/KQML_KIF_Agent_Communication.ipynb) |
| [2]  | Parse_Trees.ipynb | Create a constituency-based parse tree | [Link](https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/blob/main/Parse_Trees.ipynb) |

### Project Agent Design 
[final-project/design.md ](https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/blob/main/final-project/design.md) 

### Agent Implementation Project

| File | Purpose | Language | Link |
|------|---------|----------|------|
| `individual_implementation_project (2).py` | implementation of an academic research  multi-agent that seaches and retrieves, processes  | Python | https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/blob/main/evidence/individual_implementation_project%20(2).py  |

## 2. Data Analysis and Forum Contribution 

### Discussion 1 – Drivers of Agent-Based Systems
I analysed the organisational and technological factors driving the adoption of agent-based systems, including ubiquitous computing, network interconnectedness, advances in AI, and increasing task delegation. Through engagement with peer feedback, I broadened my analysis to consider organisational complexity as a key driver of multi-agent systems and critically evaluated the relationship between rational agency, autonomy, and decision-making under uncertainty. I also examined governance challenges, including trust, explainability, accountability, and human oversight, demonstrating an ability to assess both technical and ethical considerations.

### Discussion 2 – Agent Communication Languages
I critically compared Agent Communication Languages (KQML and FIPA-ACL) with traditional method invocation, evaluating trade-offs between interoperability, autonomy, semantic understanding, and system efficiency. Peer discussions encouraged deeper analysis of semantic interoperability and the challenge of verifying meaning between autonomous agents. This led me to conclude that unverifiable semantics represents a fundamental limitation of agent communication languages rather than merely an implementation complexity, while also highlighting the importance of ontology alignment and shared understanding.

### Discussion 3 – Deep Learning and Generative AI Ethics
I evaluated the benefits and risks of generative AI, focusing on misinformation, algorithmic bias, privacy, intellectual property, and governance. Through critical engagement with peer contributions, I moved beyond broad ethical principles to consider practical mechanisms such as bias audits, transparency requirements, regulatory frameworks, and accountability measures. This enabled me to develop a balanced, evidence-based perspective on responsible AI deployment.

### Forum Posts

![Forum Discussion Evidence ](https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/tree/main/collaboration)


## 3. Reflective Commentary

### Knowledge. 
I progressed from foundational agent concepts to First-Order Logic, then to symbolic, reactive, deliberative and hybrid architectures such as the 3T Architecture, gaining insight into how architectural choices shape behaviour. ACLs, KQML, KIF and ontologies showed how agents exchange knowledge; NLP units (Word2Vec, syntactic analysis, parse trees) and later neural networks and deep learning connected these concepts to Industry 4.0 and FinTech applications.

### Skills. 
Discussions strengthened my critical evaluation of architectures and communication approaches; practicals developed technical skills in FOL, KQML dialogues, NLP analysis and parse trees. The group project improved my ability to assess LLM-powered research agents, including hallucinations, bias and coordination.

### Understanding 
My key insight is that effective systems depend on appropriate design choices rather than added complexity; more agents and layers bring coordination costs and latency. I also deepened my appreciation of the explainability–capability trade-off: FOL offers transparent reasoning, deep learning offers flexibility at the cost of interpretability.

Reaching this was uncomfortable. Midway through, I felt genuine frustration when my system produced confident but wrong recommendations and I could not tell which agent was responsible. That frustration was productive — it forced me to stop adding capability and start adding observability, which is why the final design centres on a shared, inspectable state. I also noticed a less flattering emotion: relief when relevance scores "looked right" on a small test set. On reflection that relief was a warning sign, not a success — it was confirmation bias, the same mindset that lets developers ship biased ranking logic unchallenged. Naming it changed how I test: I now deliberately look for outputs that look correct but may be systematically skewed (Case Study 1). Floridi and Cowls' (2019) five-principle framework gave me vocabulary to say precisely which principle a design choice serves or violates.

Changed actions. Three changes to my practice, the first already applied at work: design for observability before adding agents; default to multi-criteria, user-adjustable ranking rather than a single hidden heuristic; and treat "it looks right" as a hypothesis to falsify, writing adversarial tests targeting systematic skew.

## 4. Critical Evaluation of Final Project

Designed a multi-agent research assistant using a modular architecture, allowing specialised agents to perform planning, retrieval, analysis, and ranking tasks independently. 
Adopted a blackboard design pattern with shared state management, which improved coordination between agents and provided a clear workflow.

A key strength of the design phase was its focus on scalability, maintainability, and explainability, ensuring that system decisions could be traced and justified.
During implementation, the architecture successfully enabled agents to collaborate, validating the original design decisions and demonstrating practical application of intelligent agent principles.

The use of Pydantic state models and structured workflows improved reliability, reduced errors, and supported easier debugging and testing.

The system enhanced transparency by providing relevance scores, evidence-quality ratings, and rationales for paper selection.

However, the solution remained dependent on the quality of retrieved literature, meaning weak input data could affect output quality.

The paper-ranking mechanism relied on predefined heuristics rather than machine learning models, limiting adaptability across domains.

Scalability challenges were also identified when processing larger datasets. 

## 5. Reflective case studies

### Case Study 1 Bias in Autonomous Decision-Making
What? 

My paper-ranking agent scored relevance and evidence quality via recency and citation count. Testing showed it consistently favoured highly cited and recent papers, sometimes overlooking niche studies offering important alternative perspectives.

So what? 

Developer-defined rules can introduce bias into autonomous decision-making; bias is not limited to datasets but arises from algorithm design and weighting. This maps onto Barocas, Hardt and Narayanan's (2019) distinction between allocative and representational harm: recency weighting produced representational harm by under-representing older or non-mainstream scholarship, even though no individual decision looked wrong. My initial relief that rankings "looked sensible" was itself confirmation bias, and recognising that feeling prompted me to interrogate the weights. A peer's Discussion 1 comment that autonomy is a relationship reinforced that my weighting choices were an exercise of my judgement delegated to the agent, and therefore my responsibility.

Now what? 

I now treat ranking weights as ethical design decisions requiring justification. Future improvements include multiple criteria and user-adjustable preferences. In practice for example, a workplace document recommender I would default to transparent, adjustable weighting and document each weight's rationale so bias is visible and contestable.

### Case Study 2 Explainable Decisions in Agents (XAI)
What? 

I implemented relevance scores, quality ratings and rationales for each recommendation, so every ranking carried an explanation of why a paper was surfaced.

So what? 

Transparency made outputs verifiable and helped trace unexpected results. Read through Floridi and Cowls (2019), my rationales satisfied explicability but not fully transparency or accountability: they said what the agent did, not what it could not see (e.g. papers it failed to retrieve). An explanation of a decision is not an explanation of the system's limitations "explainable" is not binary.

Now what? 

I now design explanations to disclose limitations as well as decisions, surfacing retrieval gaps alongside rankings, and would define an explicit per-agent rationale schema so this is enforced systematically.

### Case Study 3 Responsible Deployment and Emergent Behaviour
What? 

With agents sharing a Blackboard, testing showed inaccurate output from one agent could degrade subsequent agents, producing misleading final recommendations even when each agent behaved as specified.

So what? 

This is unintended emergent behaviour: the system failing in a way no single agent would — precisely the failure mode Russell (2019) warns of when control is not designed in. My initial feeling was helplessness, because the bug was in no single agent and there was no obvious place to fix it; that pushed me toward a systems-level view of responsibility.

Now what? 

I introduced validation checks and state monitoring throughout the workflow, improving reliability. Responsible deployment requires monitoring inter-agent interactions, not just individual performance; I now treat these as non-negotiable requirements built in from design, not retrofitted after failure.

## 6. References

- Barocas, S., Hardt, M. and Narayanan, A. (2019) *Fairness and Machine Learning*. Available at: https://fairmlbook.org.
- Floridi, L. and Cowls, J. (2019) 'A unified framework of five principles for AI in society', *Harvard Data Science Review*, 1(1).
- Rolfe, G., Freshwater, D. and Jasper, M. (2001) *Critical reflection in nursing and the helping professions: a user's guide*. Basingstoke: Palgrave Macmillan.
- Russell, S. (2019) *Human Compatible: Artificial Intelligence and the Problem of Control*. London: Viking.
- The University of Edinburgh (no date) *Reflection Toolkit*. Available at: https://reflection.ed.ac.uk.
- UoEO (no date) *Short Guide to Reflective Writing*. Study Skills Hub.



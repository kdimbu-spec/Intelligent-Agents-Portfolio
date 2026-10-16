# Intelligent Agents — Individual Module E-Portfolio

**Student Number:** [36995]
**Module Name:** Intelligent Agents
**Assessment Title:** Individual Module e-Portfolio
**Submitted:** [19 October 2024]

## Overview

This e-portfolio documents my learning, development, and applied practice throughout the Intelligent Agents module. It brings together my exercise outputs, coding scripts, agent implementations, system designs, data analysis, and forum contributions, alongside three formative reflective case studies and a critical evaluation of my final project.

**Structure:**
- [1. Module Exercises & Outputs](#1-module-exercises--outputs)
- [2. Coding Scripts & Agent Implementations](#2-coding-scripts--agent-implementations)
- [3. System Designs](#3-system-designs)
- [4. Data Analysis](#4-data-analysis)
- [5. Forum Contributions & Collaboration Evidence](#5-forum-contributions--collaboration-evidence)
- [6. Three Formative Reflective Case Studies](#6-three-formative-reflective-case-studies)
- [7. Critical Evaluation of Final Project](#7-critical-evaluation-of-final-project)
- [8. References](#8-references)


## 1. Module Exercises & Outputs

Summarise each exercise and link to its file or notebook.

| Week | Exercise | Output | Link |
|------|----------|--------|------|
| [1]  | KQML_KIF_Agent_Communication.ipynb | Creating a Warehouse Agent based KQML,  Alice is an agent designed to procure stock and Bob is an agent that controls the stock levels for a warehouse. This dialogue should see Alice asking Bob about the available stock of 50 inch televisions, and also querying the number of HDMI slots the televisions have. | [Link](https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/blob/main/KQML_KIF_Agent_Communication.ipynb) |
| [2]  | Parse_Trees.ipynb | Create a constituency-based parse tree | [Link](https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/blob/main/Parse_Trees.ipynb) |


## 2. Coding Scripts & Agent Implementations

| File | Purpose | Language | Link |
|------|---------|----------|------|
| `individual_implementation_project (2).py` | implementation of an academic research  multi-agent that seaches and retrieves, processes  | Python | https://github.com/kdimbu-spec/Intelligent-Agents-Portfolio/blob/main/evidence/individual_implementation_project%20(2).py  |


**Key implementation notes:**
The architecture. I adopted a blackboard design pattern, which is standard in multi-agent systems research — agents communicate indirectly through a shared state object rather than calling each other directly. That shared state is a Pydantic model called ResearchState, and it holds the research question, the plan, retrieved papers, processed papers, errors, and a sufficiency flag


## 3. System Designs

### Final Project Design (Week 7)

![System Design Diagram](./images/system_design.png)

[Brief description of the architecture, agent roles, environment, and design rationale.]

### Implemented Solution (Week 11)

![Implemented System](./images/implemented_system.png)

[Brief description of what changed between design and implementation, and why.]

---

## 4. Data Analysis

[Brief description of data gathered during testing — e.g. performance metrics, behaviour logs, comparison of architectures.]

| Metric | Design (Week 7) | Implementation (Week 11) |
|--------|-----------------|--------------------------|
| [Metric 1] | [Value] | [Value] |
| [Metric 2] | [Value] | [Value] |

[2–3 sentences interpreting these results — what they reveal about the agent's behaviour, limitations, or emergent properties.]

---

## 5. Forum Contributions & Collaboration Evidence

### Forum Posts

![Forum Contribution 1](./images/forum_post_1.png)
*[Caption: Discussion of [topic] — [date]]*

![Forum Contribution 2](./images/forum_post_2.png)
*[Caption: Response to teammate on [topic] — [date]]*

### Team Contribution Evidence

![Commit History](./images/commits.png)
*[Caption: GitHub commit history showing my contributions]*

![Task Board](./images/task_board.png)
*[Caption: Task board showing completed tasks and ownership]*

**My role in the team:** [Describe your role — e.g. architecture design, coding, testing, documentation, coordination.]
**Key contributions:** [Bullet list of 2–4 concrete contributions.]

---

## 6. Three Formative Reflective Case Studies

Each case study follows Rolfe et al.'s (2001) WHAT / SO WHAT / NOW WHAT framework and is grounded in my own module experience.

---

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

---

*This e-portfolio forms part of the assessment for the Intelligent Agents module. The 1,000-word final reflection is submitted separately via Turnitin and is not duplicated here. Content on this page sits within the 1,500-word e-portfolio allowance.*

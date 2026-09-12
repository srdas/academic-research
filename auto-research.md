---
title: "Everyone is Trying to Automate Research"
author: Sanjiv R. Das
bibliography: references.bib
link-citations: true
header-includes:
  - \usepackage{colortbl}
  - \definecolor{rowgray}{gray}{0.92}
---

## Introduction 

The paradigm of scientific discovery is undergoing a structural shift. Driven by breakthroughs in Large Language Models (LLMs), agentic orchestration, tool integration (e.g., Model Context Protocol), and automated code/sandbox execution, AI use in research is transitioning rapidly from a passive literature assistant to an autonomous co-scientist.

The use of generative AI in the automation of research began in 2025 and continues relentlessly. This begs the important question asked by Arvind Narayanan in a recent presentation -- "[What will be left for us to work on?](https://www.cs.princeton.edu/~arvindn/talks/icml-2026-annotated-slides/)". I urge you to read through his presentation, it offers a useful framework for thinking about AI automation of the world, not just research. It's based on the philosophy that AI is yet another normal technology [@narayanan_ai_2025] that will diffuse through the economy albeit in a very different disruption pattern than others. As we may imagine, automating research will call for systems that aid humans in understanding the generated results. This process of understanding will also include a process of verification and evaluation of the work done by AI agents. 

![AI solutions will need human understanding (from the talk by Arvind Narayanan, linked above.)](artifacts/ai_human_understanding.png)

There is already an extensive debate around the role of humans in research done with AI. It seems to devolve around the fact that human understanding is sacrosanct. Even for results produced by AI, we need to make sure that the human researcher deeply understands how those results were achieved and is able to place them within the pantheon of existing results in a specific domain. Some of this will come from the use of automated tools like Lean4 in the mathematical realm, which takes care of the *verification* step, but has not matured into handling the *understanding* step as yet. 

 In this article, we do not discuss these issues around human understanding. Here, we aim to understand the variety of work that has been done to automate research. After that, we'll also look at whether this means the end of academic research as we know it. 


## The Evolution of Automation in Research

AI-assisted Research automation has moved through five stages in less than that many years. 

1. Task-specific Assistance. Here we see AI help us in code generation to undertake empirical analyses [@aygun_ai_2025-1], or in surveying papers for related literature, solve open problems, refute conjectures, and generate new proofs across diverse areas in theoretical computer science, as well as other areas such as math, economics, optimization, and physics [@woodruff_accelerating_2026]. 
   
2. End-to-End Open-Ended Discovery. Instead of specific tasks, end to end research work involves literature review, hypothesis generation, code implementation, execution, and manuscript composition. This is one of the most popular and common modes of automated research. (@mitchener_kosmos_2025, @weng_deepscientist_2025, @lu_ai_2024, @yamada_ai_2025, @tang_ai-researcher_2025).

3. Research with Grounding and Verifiability. These are frameworks addressing hallucination, divergence between code and the paper, and handling of statistical replication errors. Chain of Evidence (CoE) traces every claim to a verifiable source [@meng_scientistone_2026].  Curie [@kon_curie_2025] embeds rigor into the experimentation process through three components: an intra-agent rigor module to enhance reliability, an inter-agent rigor module to maintain methodical control, and an experiment knowledge module to enhance interpretability. Research problem formulation uses approaches like Structural Gap Hypothesis Agent (SGHA), [@gharat_sgha_2026]
   
4. Creating Interactive Research Agentss. An approach that shifts research papers from static PDFs to interactive agents that enable human-AI research workflows. @miao_paper2agent_2025 converts papers automatically into research agents. Using tools such as AgentRxiv [@schmidgall_agentrxiv_2025], research agents are able to reason better and generate higher quality research over a baseline.  Current AI systems struggle to fully engage with human research because they fail to model essential scientific infrastructure like peer review, collaboration, and structured knowledge networks. To resolve this issue, [@shao_omniscientist_2025] embeds these real-world scientific mechanisms directly into the AI workflow. This integration enables a more genuine research ecosystem that can interact deeply with the scientific community.

5. Self-Evolving Multi-Agent Systems for Research. This research approach builds pipelines that accumulate long-term memory, learn from failed experiments, and iteratively improve search strategies. EvoScientist [@lyu_evoscientist_2026] is a multi-agent AI framework that continuously improves scientific research through persistent memory modules for ideation and experimentation, managed by three specialized agents (Researcher, Engineer, and Evolution Manager). By retrieving past successes and avoiding prior failures, the system progressively enhances both idea generation and code execution. Consequently, EvoScientist outperforms leading open-source and commercial AI systems across novelty, feasibility, relevance, and clarity. AutoResearchClaw [@liu_autoresearchclaw_2026] is a multi-agent autonomous framework that addresses the limitations of linear AI pipelines by incorporating multi-agent debate, self-healing execution loops, verifiable reporting, human collaboration, and cross-run memory. Through these mechanisms, it outperforms AI Scientist v2 by 54.7% on ARC-Bench while demonstrating that targeted human intervention at key decision points produces the best research outcomes. PiFlow [@pu_piflow_2025] is an information-theoretical framework that treats automated scientific discovery as a structured, principle-guided uncertainty reduction problem, acting as a plug-and-play module for existing agent architectures. Across three domains, it accelerates time-to-solution by 5.6x, reduces token consumption by up to 27%, and boosts both discovery efficiency and solution quality over state-of-the-art methods.
   
Earlier automated research agents used a sequential architecture, comprising a paradigm of *Idea -> Code -> Run -> Paper*, see for example [QuickAgent-Researcher](https://github.com/srdas/jupyter-ai-quickagent#example-2). This has evolved into complex, search-based, and evolutionary architectures with some interesting features and abstractions. (i) *Agentic tree search* emerged as one architecture, where systems like AI Scientist-v2 [@yamada_ai_2025] replace linear workflows with Best-First Tree Search (BFTS) or Monte Carlo Tree Search (MCTS) over hypothesis spaces. This allows the system to backtrack when experiments yield null results or code execution fails, branching out into alternate hypothesis trees. (ii) Sequential architectures are also not good at verification and looping back; this is addressed in approaches that use *Chain of Evidence* (CoE, @meng_scientistone_2026), where "method-code divergence" (describing an algorithm in text that differs from the underlying Python code) or hallucinated bibliographies is mitigated. ScientistOne ensures that every claim in a generated paper must mathematically and procedurally trace back to verified execution logs, raw JSON metrics, and validated citation IDs. (iii) *Managing memory* is another important aspect of automated research systems. EvoScientist [@lyu_evoscientist_2026] introduces dual-memory modules: Ideation Memory (recording feasible vs. infeasible hypothesis paths) and Experimentation Memory (capturing environment setup fixes, hyperparameter dynamics, and debugging tactics). The system evolves across research runs, mitigating redundant mistakes. (iv) *Model Context Protocols*. These architectures liberally use MCPs to access data and tools, reducing the non-determinism in research systems. Frameworks like Paper2Agent [@miao_paper2agent_2025] and DeepScientist [@weng_deepscientist_2025] use MCP server interfaces to decouple the reasoning engine from domain-specific software tools (e.g., bioinformatics suites, GPU solvers, CLI utilities), turning static software and papers into standardized, callable agent tools.


## Taxonomy of Research Agents

The preceding discussion suggests that these automated research systems map out in practice across four natural dimensions. First is their *automation scope*, which ranges from narrow task assistants designed for a single phase, like generating code or drafting a quick literature survey, to full closed-loop pipelines that take you from initial search all the way to a finished manuscript, and even interactive ecosystems that rethink how papers are published and reviewed. Second, *agentic search and reasoning patterns*, where systems move from predictable, sequential waterfall pipelines with built-in execution, to multi-agent hierarchies featuring specialized roles like researchers and auditors debating ideas, non-linear tree or graph searches like MCTS exploring hypothesis spaces, and self-reinforcing evolutionary models that adapt their prompts based on past failures. Third,  *grounding and verifiability mechanisms*, running the gamut from simple unconstrained LLMs relying on prompt guardrails, to code-bounded systems that validate against empirical terminal outputs, formal verifiers aware of domain axioms, and chain-of-evidence frameworks mandating full procedural traceability back to raw logs. Fourth, is a *human-AI collaboration model*, spanning fully autonomous sandboxes operating without intervention, human-in-the-loop setups that place gatekeepers at critical ideation or design checkpoints, and deeply co-evolving symbioses where human and agent capabilities continuously adapt to one another. We can think of this taxonomy also as single-agent, multi-agent, verificaton enablements, and human-in-the-loop mechanisms. 

The following table offers a description of all the papers in this taxonomy. 

\newpage
\footnotesize
\rowcolors{2}{rowgray}{white}

| Reference System / Paper | Automation Scope | Agentic Search Pattern | Grounding / Verifiability | Human-AI Model |
|---|---|---|---|---|
| The AI Scientist v1 (2024) | End-to-End | Sequential / Pipeline | Code Execution Bounded | Autonomous Sandbox |
| The AI Scientist-v2 (2025) | End-to-End | Agentic Tree Search (BFTS) | Code Execution Bounded | Autonomous Sandbox |
| ScientistOne (2026) | End-to-End | Multi-Agent + CoE Pipeline | Chain-of-Evidence Audit | Autonomous Sandbox |
| EvoScientist (2026) | End-to-End | Evolutionary Multi-Agent | Persistent Memory + Execution | Human-in-the-Loop / Auto |
| AutoResearchClaw (2026) | End-to-End | 23-Stage Waterfall + Debate | Code Execution + Self-Healing | Human-AI Collaboration |
| Paper2Agent (2025) | Interactive Artifact | Multi-Agent Orchestration | MCP Tutorial Testing | Interactive Co-Scientist |
| Kosmos (2025) | End-to-End | Multi-Agent Hierarchy | Data/Code Execution | Autonomous Sandbox |
| AgentRxiv (2025) | Interactive Artifact | Collaborative Multi-Agent | Peer Agent Review | Collaborative Network |
| OmniScientist (2025) | Ecosystem | Multi-Agent Co-Evolution | Environment Feedback | Co-Evolving Ecosystem |
| SGHA (2026) | Ideation / Discovery | Graph-based Retrieval | Evidence-Grounded Grounding | Human-Assisted |
| DeepScientist (2025) | End-to-End | Skill-based CLI Agent | MCP Tool Execution | Autonomous Sandbox |
| AlphaEvolve (2025) | Execution / Algorithmic | Evolutionary Coding Loop | Algorithmic Verifiers | Human-Assisted |
| PiFlow (2025) | End-to-End | Principle-Aware Multi-Agent | Domain Physics / Axioms | Autonomous Sandbox |
| Curie (2025) | Experimentation | Iterative Refinement | Hypothesis-Testing Rigor | Human-in-the-Loop |
| Barbarians at the Gate (2025) | Systems Research | System-Level Profiling | Empirical Benchmark Hardware | Autonomous Sandbox |
| Agent Laboratory (2025) | Research Assistant | Multi-Agent Collaboration | Sandbox Code Execution | Human-in-the-Loop |
| CodeScientist (2025) | Code & Experiment | Semi-Automated Execution | Metric-Driven Validation | Human-Assisted |

  : Taxonomy of models and attributes

\normalsize




   
   
   



  


## References



<!-- Compile with:

pandoc auto-research.md --citeproc -o auto-research.pdf -V link-citations=true -V urlcolor=blue -V linkcolor=blue -V citecolor=blue -->
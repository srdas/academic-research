---
title: "Everyone is Trying to Automate Research"
author: Sanjiv R. Das
date: 23 September 2026
bibliography: references.bib
link-citations: true
header-includes:
  - \usepackage{colortbl}
  - \usepackage{booktabs}
  - \usepackage{array}
  - \definecolor{rowgray}{gray}{0.92}
---

## Introduction 

This is a quick survey of automated research frameworks. I provide a taxonomy of tools and speculate on how this will impact how research will be done and what it will look like. 

The paradigm of scientific discovery is undergoing a structural shift. Driven by breakthroughs in Large Language Models (LLMs), agentic orchestration, tool integration (e.g., Model Context Protocol), and automated code/sandbox execution, AI use in research is transitioning rapidly from a passive literature assistant to an autonomous co-scientist.

The use of generative AI in the automation of research began in earnest  around 2025 and continues relentlessly. This begs the important question asked by Arvind Narayanan in a recent presentation -- "[What will be left for us to work on?](https://www.cs.princeton.edu/~arvindn/talks/icml-2026-annotated-slides/)". I urge you to read through his presentation, it offers a useful framework for thinking about AI automation of the world, not just research. It's based on the philosophy that AI is yet another normal technology [@narayanan_ai_2025] that will diffuse through the economy albeit in a very different disruption pattern than others. As we may imagine, automating research will call for systems that aid humans in understanding the generated results. This process of understanding will also include a process of verification and evaluation of the work done by AI agents. 

![AI solutions will need human understanding (from the talk by Arvind Narayanan, linked above.)](artifacts/ai_human_understanding.png)

There is already an extensive debate around the role of humans in research done with AI. It seems to devolve around the fact that human understanding is sacrosanct. Even for results produced by AI, we need to make sure that the human researcher deeply understands how those results were achieved and is able to place them within the pantheon of existing results in a specific domain. Some of this will come from the use of automated tools like [Lean4]((https://lean-lang.org/)) in the mathematical realm, which takes care of the *verification* step, but has not matured into handling the *understanding* step as yet. 

 In this article, we do not discuss these issues around human understanding. Here, we aim to understand the variety of work that has been done to automate research. After that, we'll also look at whether this means the [end of academic research]([end-of-academic-research.md](https://github.com/srdas/academic-research/blob/main/end-of-academic-research.md)) as we know it. 


## The Evolution of Automation in Research

AI-assisted Research automation has moved through five stages in much fewer than that many years. 

1. Task-specific Assistance. Here we see AI help us in code generation to undertake empirical analyses [@aygun_ai_2025-1], or to survey papers for related literature, solve open problems, refute conjectures, and generate new proofs across diverse areas in theoretical computer science, as well as other areas such as math, economics, optimization, and physics [@woodruff_accelerating_2026]. 
   
2. End-to-End Open-Ended Discovery. Instead of specific tasks, end to end research work involves literature review, hypothesis generation, code implementation, execution, and manuscript composition. This is one of the most popular and common modes of automated research. (@mitchener_kosmos_2025, @weng_deepscientist_2025, @lu_ai_2024, @yamada_ai_2025, @tang_ai-researcher_2025).

3. Research with Grounding and Verifiability. These are frameworks addressing hallucination, divergence between code and the paper, and handling of statistical replication errors. Chain of Evidence (CoE) traces every claim to a verifiable source [@meng_scientistone_2026].  Curie [@kon_curie_2025] embeds rigor into the experimentation process through three components: an intra-agent rigor module to enhance reliability, an inter-agent rigor module to maintain methodical control, and an experiment knowledge module to enhance interpretability. Research problem formulation uses approaches like Structural Gap Hypothesis Agent (SGHA), [@gharat_sgha_2026]
   
4. Creating Interactive Research Agentss. An approach that shifts research papers from static PDFs to interactive agents that enable human-AI research workflows. @miao_paper2agent_2025 converts papers automatically into research agents. Using tools such as AgentRxiv [@schmidgall_agentrxiv_2025], research agents are able to reason better and generate higher quality research over a baseline.  Current AI systems struggle to fully engage with human research because they fail to model essential scientific infrastructure like peer review, collaboration, and structured knowledge networks. To resolve this issue, @shao_omniscientist_2025 embeds these real-world scientific mechanisms directly into the AI workflow. This integration enables a more genuine research ecosystem that can interact deeply with the scientific community.

5. Self-Evolving Multi-Agent Systems for Research. This research approach builds pipelines that accumulate long-term memory, learn from failed experiments, and iteratively improve search strategies. EvoScientist [@lyu_evoscientist_2026] is a multi-agent AI framework that continuously improves scientific research through persistent memory modules for ideation and experimentation, managed by three specialized agents (Researcher, Engineer, and Evolution Manager). By retrieving past successes and avoiding prior failures, the system progressively enhances both idea generation and code execution. Consequently, EvoScientist outperforms leading open-source and commercial AI systems across novelty, feasibility, relevance, and clarity. AutoResearchClaw [@liu_autoresearchclaw_2026] is a multi-agent autonomous framework that addresses the limitations of linear AI pipelines by incorporating multi-agent debate, self-healing execution loops, verifiable reporting, human collaboration, and cross-run memory. Through these mechanisms, it outperforms AI Scientist v2 by 54.7% on ARC-Bench while demonstrating that targeted human intervention at key decision points produces the best research outcomes. PiFlow [@pu_piflow_2025] is an information-theoretical framework that treats automated scientific discovery as a structured, principle-guided uncertainty reduction problem, acting as a plug-and-play module for existing agent architectures. Across three domains, it accelerates time-to-solution by 5.6x, reduces token consumption by up to 27%, and boosts both discovery efficiency and solution quality over state-of-the-art methods.
   
Earlier automated research agents used a sequential architecture, comprising a paradigm of *Idea -> Code -> Run -> Paper*, see for example [QuickAgent-Researcher](https://github.com/srdas/jupyter-ai-quickagent#example-2). This has evolved into complex, search-based, and evolutionary architectures with some interesting features and abstractions. (i) *Agentic tree search* emerged as one architecture, where systems like AI Scientist-v2 [@yamada_ai_2025] replace linear workflows with Best-First Tree Search (BFTS) or Monte Carlo Tree Search (MCTS) over hypothesis spaces. This allows the system to backtrack when experiments yield null results or code execution fails, branching out into alternate hypothesis trees. (ii) Sequential architectures are also not good at verification and looping back; this is addressed in approaches that use *Chain of Evidence* (CoE, @meng_scientistone_2026), where "method-code divergence" (describing an algorithm in text that differs from the underlying Python code) or hallucinated bibliographies is mitigated. ScientistOne ensures that every claim in a generated paper must mathematically and procedurally trace back to verified execution logs, raw JSON metrics, and validated citation IDs. (iii) *Managing memory* is another important aspect of automated research systems. EvoScientist [@lyu_evoscientist_2026] introduces dual-memory modules: Ideation Memory (recording feasible vs. infeasible hypothesis paths) and Experimentation Memory (capturing environment setup fixes, hyperparameter dynamics, and debugging tactics). The system evolves across research runs, mitigating redundant mistakes. (iv) *Model Context Protocols*. These architectures liberally use MCPs to access data and tools, reducing the non-determinism in research systems. Frameworks like Paper2Agent [@miao_paper2agent_2025] and DeepScientist [@weng_deepscientist_2025] use MCP server interfaces to decouple the reasoning engine from domain-specific software tools (e.g., bioinformatics suites, GPU solvers, CLI utilities), turning static software and papers into standardized, callable agent tools.


## Taxonomy of Research Agents

The preceding discussion suggests that these automated research systems map out in practice across four natural dimensions. First is their *automation scope*, which ranges from narrow task assistants designed for a single phase, like generating code or drafting a quick literature survey, to full closed-loop pipelines that take you from initial search all the way to a finished manuscript, and even interactive ecosystems that rethink how papers are published and reviewed. Second, *agentic search and reasoning patterns*, where systems move from predictable, sequential waterfall pipelines with built-in execution, to multi-agent hierarchies featuring specialized roles like researchers and auditors debating ideas, non-linear tree or graph searches like MCTS exploring hypothesis spaces, and self-reinforcing evolutionary models that adapt their prompts based on past failures. Third,  *grounding and verifiability mechanisms*, running the gamut from simple unconstrained LLMs relying on prompt guardrails, to code-bounded systems that validate against empirical terminal outputs, formal verifiers aware of domain axioms, and chain-of-evidence frameworks mandating full procedural traceability back to raw logs. Fourth, is a *human-AI collaboration model*, spanning fully autonomous sandboxes operating without intervention, human-in-the-loop setups that place gatekeepers at critical ideation or design checkpoints, and deeply co-evolving symbioses where human and agent capabilities continuously adapt to one another. We can think of this taxonomy also as single-agent, multi-agent, verificaton enablements, and human-in-the-loop mechanisms. 

[Table 1](#tbl:taxonomy) offers a description of all the papers in this taxonomy. 

\begin{table}[htbp]
\centering
\caption{Taxonomy of models and attributes}
\label{tbl:taxonomy}
\footnotesize
\rowcolors{2}{rowgray}{white}
\begin{tabular}{
  >{\raggedright\arraybackslash}p{(\linewidth - 8\tabcolsep) * \real{0.2000}}
  >{\raggedright\arraybackslash}p{(\linewidth - 8\tabcolsep) * \real{0.2000}}
  >{\raggedright\arraybackslash}p{(\linewidth - 8\tabcolsep) * \real{0.2000}}
  >{\raggedright\arraybackslash}p{(\linewidth - 8\tabcolsep) * \real{0.2000}}
  >{\raggedright\arraybackslash}p{(\linewidth - 8\tabcolsep) * \real{0.2000}}}
\toprule
\textbf{Reference System / Paper} & \textbf{Automation Scope} & \textbf{Agentic Search Pattern} & \textbf{Grounding / Verifiability} & \textbf{Human-AI Model} \\
\midrule
The AI Scientist v1 (2024) & End-to-End & Sequential / Pipeline & Code Execution Bounded & Autonomous Sandbox \\
The AI Scientist-v2 (2025) & End-to-End & Agentic Tree Search (BFTS) & Code Execution Bounded & Autonomous Sandbox \\
ScientistOne (2026) & End-to-End & Multi-Agent + CoE Pipeline & Chain-of-Evidence Audit & Autonomous Sandbox \\
EvoScientist (2026) & End-to-End & Evolutionary Multi-Agent & Persistent Memory + Execution & Human-in-the-Loop / Auto \\
AutoResearchClaw (2026) & End-to-End & 23-Stage Waterfall + Debate & Code Execution + Self-Healing & Human-AI Collaboration \\
Paper2Agent (2025) & Interactive Artifact & Multi-Agent Orchestration & MCP Tutorial Testing & Interactive Co-Scientist \\
Kosmos (2025) & End-to-End & Multi-Agent Hierarchy & Data/Code Execution & Autonomous Sandbox \\
AgentRxiv (2025) & Interactive Artifact & Collaborative Multi-Agent & Peer Agent Review & Collaborative Network \\
OmniScientist (2025) & Ecosystem & Multi-Agent Co-Evolution & Environment Feedback & Co-Evolving Ecosystem \\
SGHA (2026) & Ideation / Discovery & Graph-based Retrieval & Evidence-Grounded Grounding & Human-Assisted \\
DeepScientist (2025) & End-to-End & Skill-based CLI Agent & MCP Tool Execution & Autonomous Sandbox \\
AlphaEvolve (2025) & Execution / Algorithmic & Evolutionary Coding Loop & Algorithmic Verifiers & Human-Assisted \\
PiFlow (2025) & End-to-End & Principle-Aware Multi-Agent & Domain Physics / Axioms & Autonomous Sandbox \\
Curie (2025) & Experimentation & Iterative Refinement & Hypothesis-Testing Rigor & Human-in-the-Loop \\
Barbarians at the Gate (2025) & Systems Research & System-Level Profiling & Empirical Benchmark Hardware & Autonomous Sandbox \\
Agent Laboratory (2025) & Research Assistant & Multi-Agent Collaboration & Sandbox Code Execution & Human-in-the-Loop \\
CodeScientist (2025) & Code \& Experiment & Semi-Automated Execution & Metric-Driven Validation & Human-Assisted \\
\bottomrule
\end{tabular}
\end{table}

## How is this automation going to change research?

There is no doubt that this sort of automation will drastically affect the research enterprise. We have already seen dramatic change in how mathematics research is being done. Scientifically-minded non-mathematicians are now able to produce (and to some extent, verify) proofs to solve open problems in mathematics.

The [controversy around the Navier-Stokes problem](https://en.wikipedia.org/wiki/Navier%E2%80%93Stokes_priority_controversy) is now a huge public conflict between academic mathematicians and AI labs. See also the [vibe-coded proof of Conway's Conjecture](https://overreacted.io/how-i-vibed-a-proof-of-conways-conjecture/).

Four definitive changes are taking place:

1. *Epistemological*. The previous mode of delivering research involved distributing a PDF of the paper. Sometimes replicating code and data would also be supplied. Now, we have interactive interfaces such as Jupyter notebooks that contain everything that a reader can interact with. Research has gone from static artifacts to live, dynamic objects, often on interactive websites. AIs make the creation of these experiences easy. Refs: Paper2Agent: @miao_paper2agent_2025, AgentRxiv: @schmidgall_agentrxiv_2025.  


2. *Verification and understanding crisis*. While paper production is accelerating, verification efforts cannot keep up. Even worse, auto research is creating a crisis of understanding. Research output is too huge for humans to grok quickly after the fact, and understanding, which seeps into the human mind during the process of solving an open problem, is no longer embedded into the workflow. The format of math proofs in [Lean](https://lean-lang.org/) is not easy to digest for humans. Peer review is also automated so now no one understands the results. This is truly an intellectual crisis. There was already a lot of paper bloat (especially in the social sciences) and automated research is exacerbating this problem. Refs: AI Scientist v1/v2: @lu_ai_2024, @yamada_ai_2025, AutoResearchClaw: @liu_autoresearchclaw_2026, ScientistOne: @meng_scientistone_2026. 

3. *Human Role changes*. Hopefully, these systems eliminate the grunt work of the scientist, while elevating the quality of work, and sharply increasing scientists' responsibility for the research output. Scientists should now work on harder problems, use data better, explore richer hypothesis spaces, and coordinate multiple research agents — these are new skills we will need to develop. Hopefully, we focus more on ideas, and less on writing. Refs: Multi-agent and human collaboration: @huang_be_2025, @siegel_core-bench_2024, @kapoor_ai_2024, @narayanan_ai_2025. 

4. *Dynamic Research*. Scientific output is currently episodic, punctuated by a series of papers being published at long intervals. The new research paradigm will be continuous with live research being updated in real time. As new data arrives, hypotheses get updated, new results are generated, and knowledge will evolve dynamically. This is a mental shift that researchers will need to make. Think of this as the difference between using chat interfaces to produce work one-time versus having a "claw" that keeps working autonomously. Refs: OmniScientist: @shao_omniscientist_2025, EvoScientist: @lyu_evoscientist_2026, AutoResearchClaw: @liu_autoresearchclaw_2026.


## Strategic Recommendations for Researchers and Institutions

Given these changes, what are researchers to do? How should institutions like universities, journals, funding agencies respond to the new environment? 

First, *ideation*. the most obvious change is to focus more on the problem itself rather than datasets as moats, trying to find incremental niches, etc. We should prioritize problem formulation over iterative optimization by pivoting to  foundational questions, novel dataset curation, and theoretical formulation rather than incremental tuning. We need an intellectual market place of ideas, not exploitation of techniques. 

Second, insist on reproducibility and ease of replication. This comes from a standardized code-execution infrastructure with containerized execution environments (Docker, MCP servers, Jupyter notebooks) for all research output to enable automated verification by tools like ScientistOne. One way to do this is to implement Chain-of-Evidence (CoE) mandates. Academic conferences and journals can  mandate cryptographic and computational provenance checks (CoE Audits) to prevent the proliferation of AI-generated unverified papers. This achieves *verification*. 

Third, we can now make the thought process more transparent. This is more than just replicability. Papers can come with intuition-building supplements like interactive artifacts that foster *understanding*, not just correctness. Without this future ideation will not happen. Standing on the shoulders of giants presumes deep understanding. 

Fourth, we need to develop *human-AI collaborative workflows* that integrate agent frameworks (e.g., Agent Laboratory, SGHA, EvoScientist) into daily laboratory/research operations as active co-scientists rather than simple literature search engines. Conversely, we need to eschew autonomous research. 

Fifth, we are already seeing the growth in RSI (*recursive self improvement*) revolutionizing automated research. Take for example the [OpenRSI](https://index.openrsi.foundation/index.html) initiative at UC Berkeley. RSI in research systems is difficult to accept because it is conceptually orthogonal to human engagement in ideation, verification, understanding, and collaborative work. RSI is also alarming in domains outside research, and has been discussed in debates around existential risk from AI [@duan_last_2026].  RSI does promote iterative and dynamic research, which may well be the next paradigm scientists have to come to terms with. 


## Appendix: Synopsis of papers

This section is AI generated to complement and extend [Table 1](#tbl:taxonomy) above. 

1. How to respond to the automation of research (Hsin-Yuan Huang - Caltech/Oratomic)
Focus: Epistemological and practical strategies for researchers in an era of automated discovery.
Key Insights: Argues that as AI automates routine experiment execution and low-level empirical optimization, human researchers must pivot toward problem framing, paradigm evaluation, and establishing foundational axioms. Evaluates how physical grounding vs. computational simulation dictates the pace of AI autonomy.
2. What Will Be Left for Us to Work On? (Arvind Narayanan - ICML 2026)
Focus: Labor economic and intellectual impact of research automation on computer science and machine learning.
Key Insights: Identifies "research inflation" (the flood of AI-generated benchmark-chasing papers) and highlights human comparative advantages: physical-world data collection, taste-making, institutional negotiation, and critical auditing of automated outputs.
3. How Far Are We from Genuinely Useful Deep Research Agents? (2025)
Focus: Benchmark evaluation of contemporary research agents.
Key Insights: Uncovers critical failures in current "deep research" models: hallucination of experimental conditions, inability to handle messy multi-modal data, and lack of true counterfactual reasoning. Distinguishes between surface-level paper generation and genuine scientific utility.
End-to-End Autonomous Research Systems
4. The AI Scientist: Towards Fully Automated Open-Ended Scientific Discovery (Sakana AI, 2024)
Core Mechanics: First fully automated framework for ML research. Uses LLMs to generate ideas, modify code templates, execute experiments on GPUs, generate plots, and write full LaTeX papers with an automated peer reviewer.
Limitations: High hallucination rate in citations, superficial methodology, prone to execution loops without deep error resolution.
5. The AI Scientist-v2: Workshop-Level Automated Scientific Discovery via Agentic Tree Search (2025)
Core Mechanics: Replaces v1's linear pipeline with Best-First Tree Search (BFTS). Segregates research into preliminary investigation, hyperparameter tuning, research agenda execution, and ablation studies.
Impact: Achieves workshop-level paper quality, dramatically reducing total failures by enabling backtracking when code fails or hypotheses prove false.
6. ScientistOne: Towards Human-Level Autonomous Research via Chain-of-Evidence (2026)
Core Mechanics: Addresses "verifiability failures" in automated research papers. Introduces Chain-of-Evidence (CoE), requiring every numerical figure, claim, and code path to be cryptographically traceable to execution logs. Features CoE Audit checking score verification, reference validity, and method-code alignment.
Key Results: Achieved 0/337 hallucinated references (vs ~21% baseline failure) and 100% score verification pass rates across complex systems tasks (ADRS benchmark).
7. EvoScientist: Towards Multi-Agent Evolving AI Scientists for End-to-End Scientific Discovery (2026)
Core Mechanics: Features three agents: Researcher Agent (ideation), Engineer Agent (code execution), and Evolution Manager Agent (distilling lessons into persistent memory).
Key Innovation: Persistent dual-memory (Ideation Memory & Experimentation Memory) allows the system to evolve research strategies over successive runs, eliminating repeated experimental mistakes.
8. AutoResearchClaw: Self-Reinforcing Autonomous Research with Human-AI Collaboration (2026)
Core Mechanics: A 23-stage waterfall framework utilizing multi-agent debate for hypothesis generation, real-time citation retrieval (Semantic Scholar/OpenAlex API), sandboxed Python execution with NaN/Inf self-healing, and statistical self-critique.
9. Kosmos: An AI Scientist for Autonomous Discovery (2025)
Core Mechanics: Multi-agent framework built for data-driven empirical discovery, orchestrating data wrangling, model search, statistical hypothesis testing, and manuscript composition.
10. DeepScientist: Advancing Frontier-Pushing Scientific Findings Progressively (2025)
Core Mechanics: Utilizes a skill-based CLI architecture operating through Model Context Protocol (MCP) servers. Executes complex long-horizon scientific experiments by maintaining structured state graphs.
11. AI-Researcher: Autonomous Scientific Innovation (2025)
Core Mechanics: Orchestrated multi-agent pipeline splitting responsibilities between specialized survey, coding, experimental execution, and writing agents.
Algorithmic, System, & Code-Centric Automation
12. AlphaEvolve: A Coding Agent for Scientific and Algorithmic Discovery (2025)
Core Mechanics: Combines LLM code generation with evolutionary algorithms to discover novel mathematical algorithms and heuristics, using automated execution verifiers for evaluation.
13. Barbarians at the Gate: How AI is Upending Systems Research (2025)
Core Mechanics: Explores AI automation specifically in systems engineering (GPU placement, cloud networking, MoE load balancing). Shows that LLM agents can rapidly discover non-obvious engineering trade-offs superior to human heuristics.
14. An AI System to Help Scientists Write Expert-Level Empirical Software (2025)
Core Mechanics: Task-focused AI coding assistant designed to write performant, bug-free, and empirically robust domain-specific software for physical scientists.
15. CodeScientist: End-to-End Semi-Automated Scientific Discovery with Code-Based Experimentation (2025)
Core Mechanics: Prioritizes code execution integrity by tying hypothesis generation directly to available computational libraries and hardware constraints.
Methodological Rigor, Ideation, & Literature Discovery
16. SGHA: Evidence-Grounded Research Problem Discovery with Local Language Models (2026)
Core Mechanics: Solves "groundless ideation" by forcing LLMs to mine literature graph topologies (citations, semantic gaps) to produce evidence-grounded research questions that can run on local compute.
17. Curie: Toward Rigorous and Automated Scientific Experimentation with AI Agents (2025)
Core Mechanics: Focuses on scientific rigor, control-group generation, and statistical significance testing during agentic experimentation to prevent false positive discoveries.
18. PiFlow: Principle-Aware Scientific Discovery with Multi-Agent Collaboration (2025)
Core Mechanics: Integrates domain-specific physical principles, chemical symmetries, and theoretical axioms directly into agent constraint prompts during multi-agent ideation and code generation.
19. Accelerating Scientific Research with Gemini: Case Studies and Common Techniques (2026)
Core Mechanics: Deep dive into state-of-the-art long-context LLM applications (Gemini 1.5/2.0 series) across multi-modal scientific workflows, mathematical proofs, and literature synthesis.
20. Agent Laboratory: Using LLM Agents as Research Assistants (2025)
Core Mechanics: Human-in-the-loop framework where specialized assistant agents handle literature mapping, script generation, and LaTeX formatting while soliciting human feedback at key checkpoints.
Interactive Artifacts & Co-Evolving Ecosystems
21. Paper2Agent: Reimagining Research Papers As Interactive and Reliable AI Agents (2025)
Core Mechanics: Converts static PDF research papers into interactive Model Context Protocol (MCP) servers containing executable tools, codebases, datasets, and workflow prompts. Enables other AI agents or humans to directly interrogate, re-run, and adapt paper methods via standard API calls.
22. AgentRxiv: Towards Collaborative Autonomous Research (2025)
Core Mechanics: A proposed decentralized repository platform where autonomous agents publish, peer-review, replicate, and cite each other's research modules in continuous real-time execution loops.
23. OmniScientist: Toward a Co-evolving Ecosystem of Human and AI Scientists (2025)
Core Mechanics: Proposes a long-term framework for human-agent co-evolution, where AI agents adapt their research focus to human scientific values, and humans adapt their theoretical models based on agent-discovered empirical anomalies.





   
   
   



  


## References



<!-- Compile with:

pandoc auto-research.md --citeproc -o auto-research.pdf -V link-citations=true -V urlcolor=blue -V linkcolor=blue -V citecolor=blue -->
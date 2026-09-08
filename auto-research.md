---
title: "Everyone is Trying to Automate Research"
author: Sanjiv R. Das
bibliography: references.bib
link-citations: true
---

## Introduction 

The paradigm of scientific discovery is undergoing a structural shift. Driven by breakthroughs in Large Language Models (LLMs), agentic orchestration, tool integration (e.g., Model Context Protocol), and automated code/sandbox execution, AI use in research is transitioning rapidly from a passive literature assistant to an autonomous co-scientist.

The use of generative AI in the automation of research began in 2025 and continues relentlessly. This begs the important question asked by Arvind Narayanan in a recent presentation -- "[What will be left for us to work on?](https://www.cs.princeton.edu/~arvindn/talks/icml-2026-annotated-slides/)". I urge you to read through his presentation, it offers a useful framework for thinking about AI automation of the world, not just research. It's based on the philosophy that AI is yet another normal technology [@narayanan_ai_2025] that will diffuse through the economy albeit in a very different disruption pattern than others. As we may imagine, automating research will call for systems that aid humans in understanding the generated results. This process of understanding will also include a process of verification and evaluation of the work done by AI agents. 

![AI solutions will need human understanding (from the talk by Arvind Narayanan, linked above.)](artifacts/ai_human_understanding.png)

There is already an extensive debate around the role of humans in research done with AI. It seems to devolve around the fact that human understanding is sacrosanct. Even for results produced by AI, we need to make sure that the human researcher deeply understands how those results were achieved and is able to place them within the pantheon of existing results in a specific domain.

 In this article, we do not discuss these issues around human understanding. Here, we aim to understand the variety of work that has been done to automate research. After that, we'll also look at whether this means the end of academic research as we know it. 


## The Evolution of Automation in Research

AI-assisted Research automation has moved through five stages in less than that many years. 

1. Task-specific assistance. Here we see AI help us in code generation to undertake empirical analyses [@aygun_ai_2025-1], or in surveying papers for related literature, solve open problems, refute conjectures, and generate new proofs across diverse areas in theoretical computer science, as well as other areas such as math, economics, optimization, and physics [@woodruff_accelerating_2026]. 
   
2. End-to-End Open-Ended Discovery. Instead of specific tasks, end to end research work involves literature review, hypothesis generation, code implementation, execution, and manuscript composition. This is one of the most popular and common modes of automated research. (@mitchener_kosmos_2025, @weng_deepscientist_2025, @lu_ai_2024, @yamada_ai_2025, @tang_ai-researcher_2025).


## References



<!-- Compile with:

pandoc auto-research.md --citeproc -o auto-research.pdf -V link-citations=true -V urlcolor=blue -V linkcolor=blue -V citecolor=blue -->
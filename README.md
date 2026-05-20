# The End of Academic Research: My Existential Crisis

Sanjiv R Das
---
May 17, 2026

I have been exploring academic research using AI over the last three months. There is a progression of ideas and artifacts generated as I worked through this and it culminated in my preparing an entire book in a few hours. This triggered some thorny emotions on this that spilled over, and I felt compelled to write up my journey. 

Truth be told, I was learning as I proceeded with generative AI, building code and other methods to make my work easier and easier. It was exhilarating and fun, and I felt productive. Today, at the end of my journey, I feel empty inside and scared at what I have done. I thought my professional role as an academic researcher was safe in this age of AI, but I am no longer of that opinion. I can only hope we enter a new age where ideas get primacy and grunt work is deprecated. 

I am not newbie as far as LLMs are concerned. I have been teaching my course on NLP for a few years and have been changing a third of it almost every time I taught it, more so in the last year as the weekly drumbeat of new AI discoveries kept rolling out mercilessly. I am well-versed in the internals of deep learning systems, transformers, etc., from working on related science in industry as well as writing open-source software. However, I had never consolidated my ideas and considered how it may impact academia until I decided to give a talk at my business school on all the different ways in which we might use AI. I'd be grateful if you scrolled through the slides for this talk, titled [**Thinking with Machines**](artifacts/AI_Literacy_slides.pdf) just to get a sense of how huge the ecosystem now is. A lot of the meat of my experience is in the hyperlinks in this essay and I do urge you to click through on them, even if for a brief moment, as it will expand your context, I believe, in an effective way. 

In another lead up to this, I had written down an idea for a small paper on the back of an envelope for two of my students who went off and wrote the code for the paper. I also wrote up some parts of the paper and when the students returned with the code, I modified it to get results I needed to answer the questions we had (using AI to make modifications). The paper was meant to be short (5-6 pages and a few figures) because it was satisfying our curiosity about a single simple question. In the talk I used this paper as an example of how an LLM could be used to write some of the results once the tables and figures are ready, do literature review from a supplied BibTeX file, write conclusions, etc. After my talk, which went on for a few hours, one of my colleagues mentioned that UCLA's finance department was holding a [Human x AI Finance conference](https://humanxaifinance.org/) where papers had to be written with AI and all submissions would be evaluated by AIs. The deadline was that night (such a coincidence), so I used various AI steps to take what I had to finish the paper. I read the paper, made several edits, checked carefully for any hallucinations, and rewrote some parts. I also wrote up a complete description of how AI was used as an [**Appendix**](artifacts/chronos2-EL-AI-Appendix.pdf), which may be a good template to follow now that journals ask for some detail about AI. I urge you to read this appendix as it shows how you can use AI as if you have a co-author or research assistant working in tandem with you. Some people in the AI world call this approach as "multi-monitor" work. 

It brings up ideas of [pair programming](https://en.wikipedia.org/wiki/Pair_programming), which has been a successful paradigm in software engineering. Of course, now we have super RAs instead. Is this AGI (artificial general intelligence) or ASI (artificial super intelligence)? I leave that for you to decide. 

The paper was [rejected](artifacts/HumanAIconf_rejection.png) at the conference, they received over 166 submissions and I believe just 4 papers were selected. One can infer from this that I am not the only one who knows how to use AI as a super RA. 

I felt the paper did make a useful contribution about the latest AI Foundation models for forecasting, and that it might be interesting to readers to expose how AI might be used once you have a question in mind. I [submitted](artifacts/FRL_submission.png) it to *Finance Research Letters* (FRL) (which publishes very short articles with tight word limits). It was desk rejected within the hour, here is the [rejection letter](artifacts/FRL_rejection.png). My first reaction was that the rejection was AI generated, which is ironic because the paper was also somewhat AI generated, albeit I'd say more than 50% human. After reading the rejection again and again, I am convinced that it was actually the editor who wrote it. I had a similar experience with another journal where we received what looked like an AI rejection and after conferencing with the editor, the paper was unrejected (if there is such a word) and received two excellent human reviews thereafter. That [paper](https://www.sciencedirect.com/science/article/pii/S2405918826000115?via%3Dihub) is now published and was not AI-prepared, though it is *about* AI.

The rejection at FRL came with an option to transfer it to another journal (and here I am convinced that AI makes these recommendations). So I selected *Economics Letters*, which I had published in before, and it had a tighter word limit. The cover letter makes clear that AI is used and I also uploaded the Appendix explaining how the [submission](artifacts/EL67834.pdf) was prepared. Luckily, this was not desk rejected and is now under review and has been sent to [two reviewers](artifacts/EL_submission.png). I suspect the paper will be rejected as the contribution may be limited, but it may be interesting to the readership as it is about AI and is worked out with AI. But I am curious to see what the editor and referees think of this kind of submission. And I am deeply interested in the feedback because it will shed light on what policies we may need to develop at universities and journals to manage this new style of work. 

I will update this here when I hear back from the journal. 

My solace in this work so far has been that the ideation of the paper was all human and much of the structure and writing was also initially human. It was a lot of the grunt work that was handed off to the AI. 

A brief while later it struck me that I should try to engage the AI in the *ideation* process. I use Jupyter notebooks a lot for research and teaching and work with the [Jupyter](https://jupyter.org/) open-source team. I specifically spend a lot of time with the maintainers of the [Jupyter AI](https://github.com/jupyterlab/jupyter-ai) project. I decided to build an agentic add-on to Jupyter AI, which I called *QuickAgents* and open sourced the code for this, see the [GitHub repository](https://github.com/jupyterlab/jupyter-ai). This allows you to build agents with no coding required. 

One of the agents I built is called *Researcher*. All you need to do is take your datasets and papers and drop them into a folder on your laptop. Point Researcher to it and it will analyze the contents of the folder, generate research questions, ask you to select one or all of them. It will then do the data analysis to answer the research questions, generate tables and figures, write up the entire paper in LaTeX, and also prepare the code and results in a Jupyter notebook to guarantee reproducibility. Meanwhile, you go get coffee and come back to see the research project done, or at least have a complete set of artifacts that you can improve on. So far, I have been using [kaggle datasets](https://www.kaggle.com/datasets?fileType=csv) (of varying sizes) and run times have been between 10-30 minutes. It's good to get fully written insights into datasets, but it's not great research. 

Want to see an example? Here is the [procedure](https://github.com/srdas/jupyter-ai-quickagent#example-2). It produced an entire research project with no human intervention. Please read the workflow of this example in the procedure above. If nothing else, do take a look at the generated [**paper**](https://github.com/srdas/jupyter-ai-quickagent/blob/main/examples/mentalhealth/output/paper.pdf). More such examples are [here](https://github.com/srdas/jupyter-ai-quickagent/tree/main/examples). You can look into each folder and see the `.chat` files that show the sequence of steps taken by the agent, as well as all the other outputs. 

There are several things under-the-hood that make this so effective and I will mention only a few of them here. First, LLMs have become superhuman, I used Claude Sonnet-4.6 and Opus-4.7 here. Second, I prepared a skill file describing what a good research question is. This provides the LLM my quality bar and also a structure in which to think through the research project. See the [skills](https://github.com/srdas/skill-collection/tree/main/researcher/skills) I prepared. There are two files, one for what is good research and the other is for orchestration of my agent. Third, the software engineering I developed uses [LangChain DeepAgents](https://docs.langchain.com/oss/python/deepagents/overview) to manage the entire activity of the agent. If you want to dive deep, see the [Python code files](https://github.com/srdas/jupyter-ai-quickagent/tree/main/jupyter_ai_quickagent) I wrote. As I build more and more agents and develop targeted skill files, I keep open-sourcing them here in my [skill-collection](https://github.com/srdas/skill-collection).

*In short, ideas are no longer the provenance of humans alone. Machines running "soft" AI can do more than just white collar grunt work.* 

I have been working on a book for my sabbatical and AI text completion keeps popping up in my editor and I keep swatting it away, though sometimes it does suggest good ideas. But mostly, it is rather annoying. For me, relegating grunt work to AI allows me to spend more time on ideation, and that's how my book work has been, as I use AI for hours chasing down interesting historical events as it is certainly a good re(search) engine. And it can be a huge distraction, but research distractions are quite enjoyable. 

When you push things to their limits you can find yourself in an existential crisis. This is what happened to me over the past two days. But I don't think I am alone in this. *I believe that everyone who brings AI into their academic life will eventually end up here.* The malaise is spreading, and your infection is inevitable. 

So, here is what happened. Two weeks ago I engaged in some research and discussions around quantum computing with a couple of my friends and colleagues who are both quantum physicists. One of them also has a PhD in finance. I had also sat in on the quantum computing class in Q1 2026 with another engineering colleague. It slowly has become clear to me that the time has come where practical quantum computing, which seemed like too far away, is now becoming sort of feasible in the short term, and inevitable in the long run. So I asked my QuickAgent to use my collection of papers (stored in Zotero) to write up a survey of where finance would intersect with quantum computing. See: [Quantum Computing for Finance: A Survey](https://github.com/srdas/quantum-finance/blob/main/survey/QuantumFinanceSurvey.pdf) with the byline "A comprehensive review of algorithms, applications, and prospects" as a starting point for me to undertake serious exploration and research in this area. I also wanted to use this survey to level up and be able to talk intelligently to my physicist friends. 

One thing led to another and on Friday night (two days ago) I used my knowledge from the quantum computing course to list out all the mathematical concepts I had learned in order to understand [Shor's algorithm](https://en.wikipedia.org/wiki/Shor%27s_algorithm). I then asked Claude to write up a book chapter with each of the mathematical concepts briefly described with a short example and to sequence the content in the best order possible. Within a couple of minutes, it produced an absolutely amazing chapter. Encouraged by this, I then asked it to use my BibTeX file referencing all the papers on quantum computing to write up an introductory chapter to the textbook. This was also completed in swift fashion. I could now start reading this to begin my journey. 

What I realized here is that I had solved a problem that one faces when embarking on a new research area. It's always very hard to know where to start and how to accumulate knowledge in the most impactful and economical manner. [Andrew Ng](https://www.linkedin.com/in/andrewyng/) has [said](https://www.kaggle.com/discussions/getting-started/147443) that one must read 10-20 of the most important papers first and then read another 50 or so to have a good grip on any subfield. This always seemed a steep hurdle. I think preparing short book-form material for study with a little bit of knowledge can really accelerate this process.

Anyway, this morning, I decided to go the whole hog and list all the chapters I wanted in the book in my top-level LaTeX file for my [Quantum project](https://github.com/srdas/quantum-finance/). The list is shown here as a snippet from my `qbook.tex` file: 

```
\input{intro_quantum_finance.tex}
\input{math.tex}
\input{classical_vs_quantum.tex}
\input{quantum_computing.tex}
\input{hilbert_space.tex}
\input{braket.tex}
\input{qubit.tex}
\input{superposition.tex}
\input{entanglement.tex}
\input{interference.tex}
\input{schrodinger_wave.tex}
\input{quantum_hardware.tex}
\input{decoherence.tex}
\input{error_correction.tex}
\input{nisq.tex}
\input{qiskit.tex}
\input{rsa.tex}
\input{elliptic_curves.tex}
\input{shor_algorithm.tex}
\input{where_now.tex}
```

I had of course, the first two chapters in hand. I was now ready to ask Claude to generate the rest of the book using the file names above as cues. I explained what I was doing to my wife and called her over to see what would happen. I had no idea whether this would work or not. But here is the prompt I issued: 

*@qbook/qbook.tex Each of the commented lines 120-136 is a placeholder for a chapter to be written on the concept in the file name. Create a separate Latex file with that name for each chapter and in each Latex file, please write up the chapter. If you use references that are not in @qbook/Quantum.bib please add them as a separate bib file called Quantum2.bib (do not add them to the existing Quantum.bib file). Go chapter by chapter and uncomment each line for the \input{} of each chapter as you go. When writing, feel free to reference the other chapters. Try to make sure that the writing across chapters is consistent in notation and style. If you think the new chapters need to be resequenced, feel free to do so. Give catchy titles for each chapter and section within each chapter.*

https://github.com/user-attachments/assets/020012f5-fa6b-414c-8f5f-b362748bd2c2

We hit `Enter` and then watched in amazement. In less than a half hour, the entire book was ready. (You can see a short snippet of the AI at work above.) The book titled [**Quantum Phynance**](artifacts/qbook-0.0.1.pdf) looks really good though I am sure there are hallucinations---please, please click on it and take a look, preferably download it and look at all 239 pages. I have to now dig into it and check everything, but that process is going to be a learning one! Is this a new way to learn? What does one do with it?  

I asked Claude to document what it had done and you can see this [here](https://github.com/srdas/quantum-finance/blob/main/notes/instructions.md). If you scroll to the bottom of the PDF quantum book you will see that the book has a complete index as well. I remember spending hours making indexes by tagging words in LaTex, so no more of that! 

What I thought would be an enjoyable journey into the intersection of quantum computing and finance, *culminating* in a book, has now become a very different journey, *beginning* with a book---one that I daresay is not something as original as I might have hoped, and leaving me without a project I had been looking forward to. But I suppose it leaves me more time now to delve into quantum finance  without the usual academic pain of shepherding a paper/book to publication. 

After all this, I am left confused about what research means in this new age. To clear up my confusion, I turned to AI. (Everything written up to this point has no AI input at all.) Here is what I got after working with the AI to consider taste, critical thinking, ownership, the definition of research, caring and values, etc., 

> *Research, at its core, has always been a fundamentally human endeavor — not because humans are uniquely capable of generating knowledge, but because research is ultimately about asking questions that matter. The question of what matters is a deeply human one. AI can now generate hypotheses, analyze data, write papers, and even review literature with remarkable competence. But the question of which problems deserve attention, which discoveries would change lives, which ideas are worth pursuing — these remain tethered to human values, human experience, and human judgment. The new age of research is not the end of the human researcher; it is the end of the researcher as a craftsperson of process. You are now an architect of questions. The grunt work is gone. What remains is the hardest part: deciding what to care about.*

Hmmm ... it sure used everything above as context, which is fine. 

It feels like it gave me an answer that is informed enough to be reassuring, but not true enough to fully resolve my anxiety. Because here is the thing — when I asked my QuickAgent to generate research questions, it did not fail. It produced excellent questions. When I listed the chapters for a quantum finance book, Claude did not just fill them in mechanically; it made judgment calls about sequencing, about notation consistency, about which ideas deserved more depth, as instructed, but better than a human student RA would have. These are not the actions of a working stiff. These are, at minimum, the actions of a super research assistant with taste. 

One of my colleagues told me that he feels less excited about reading my emails if he suspects that some of it is AI-generated. Overuse of AI can slowly destroy identity. As our AIs talk to each other we may lose all human connection. Resistance is needed at an existential level. 

Am I still the researcher? Or am I now more like the client who gives a rough brief to an architect who then builds the whole house? Research is, more or less, a conversation — with data, with prior work, with colleagues, with students, and ultimately with the world and its values. AI has become an extraordinarily capable interlocutor in that conversation. It can push back, fill gaps, synthesize across disciplines, and suggest angles I would not have thought of on my own. 

But it cannot care. It has no stake in the outcome. It will help you write a paper about anything with equal enthusiasm. That asymmetry — between my caring and its competence — is, I think, where the human researcher still lives. But, is caring enough?

I am a finance professor. I have spent thirty years caring about markets, about risk, about the people whose savings and livelihoods hang on these things. That caring drove me to ask questions, to persist through dead ends, to revise and rethink. AI did not give me that caring. But AI has now removed most of the friction between caring and contributing. And when friction disappears, you discover very quickly which part of the journey you actually loved — the research itself, the midnight hours full of frustration, or the final output. I think I loved the struggle more than I knew.

This reminds me of the *[IKEA effect](https://en.wikipedia.org/wiki/IKEA_effect)* — people place disproportionately higher value on things they helped create, even if the result is objectively inferior. I have my favorite papers because I lived with them through thick and thin. I even love the futile ones that did not make it to completion or publication. The quantum finance book that Claude wrote in thirty minutes while my wife and I watched is not futile. It is polished and thorough and, I suspect, largely correct. But it is not mine in the way a book I had spent two years on would have been mine. That is a loss. A strange, privileged kind of loss, like complaining that the hardship was too little. We know this, the quick papers like the one I submitted to the AI x Finance conference and journals above, often bring less joy. 

What do we do with this? I think we have to be honest about what we are losing and what we are gaining. We are gaining speed, scale, and coverage. We are losing the slow accumulation of understanding that comes from fighting a problem for years. I think this is a dangerous loss. As a community of scholars, we need to think about what we are training the next generation to do and how to value research when the machinery of scholarship is so capable. We do not want to maximize output while minimizing understanding. 

I am still a researcher. But my experience in the last few months has completely changed my view of the world. I am scared for how much we will deprecate thinking, but I am not yet cynical. There is hope yet. 

I will keep writing. I will keep asking questions. I will keep caring about markets and risk and the people in them. I will use AI as a colleague who is always available, infinitely patient, and occasionally brilliant. But I will also try to remember the value of the [slow road](https://www.slow-science.com/) — and maybe, oftentimes, take it.

What I am already doing is switching off the AI unless using it for grunt work, and I will ramp up my time on critical thinking, judgment, and taste, the three pillars of what I enjoy so much about being an academic. 

So this is my existential crisis. I will find a way to deal with it. But it is also ours as a community, and we all need to work this out. 

#### Follow-on notes

May 19, 2026: Google-IO, releases [Gemini for Science](https://blog.google/innovation-and-ai/technology/research/gemini-for-science-io-2026/); see also the [article in Engadget](https://www.engadget.com/2177120/google-debuts-ai-powered-tools-to-optimize-scientific-research-workflows/). Labs: https://labs.google/science/ 

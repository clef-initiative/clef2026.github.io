---
title: "Keynotes"
draft: false
summary: "The keynote speakers for CLEF 2026."
weight: 50
toc: true
menu:
  main:
    identifier: "conference-keynotes"
    parent: "conference"
    weight: 50
---

## Michael Granitzer

**Title:** Beyond Open Models: Building Open Search Infrastructure for AI Agents

**Date:**  Monday, September 21

**Abstract:** Open-source language models are becoming increasingly capable and accessible. Yet an open model does not by itself create an open information-access system. When models and agents depend on proprietary search services, researchers cannot inspect or modify the underlying corpus, indexing process, retrieval system, or usage data. This talk therefore advances four hypotheses about the infrastructure required for transparent research on future search systems.

First, openness must extend below the model layer. OpenWebSearch.EU is a European research initiative developing distributed infrastructure for crawling, processing, and indexing the web. One of its central outcomes is the Open Web Index: an openly accessible web index that supports search services as well as bulk access to data for independent experimentation. On top of this index, OURRS provides a web search engine through which researchers, applications, and agents can retrieve information using an open and inspectable infrastructure.

Second, corpus scale and complexity must be treated as scientific variables rather than merely engineering constraints. As collections grow, retrieval systems encounter more plausible distractors, duplication, multilingual content, and conflicting evidence. These changes affect effectiveness, efficiency, and robustness. Their impact becomes even more significant when retrieval is embedded in AI agents: agents search repeatedly, reformulate queries, compare sources, and make later decisions based on earlier retrieval results. Small retrieval effects can therefore accumulate across an entire information-seeking trajectory.

This leads to the third hypothesis: usage data for agentic search should be created by design. During the rise of commercial web search, much large-scale user and interaction data remained inaccessible to researchers. With agentic systems, the community has an opportunity to instrument retrieval from the beginning, operate controlled populations of artificial agents, and collect traces of searching, reasoning, verification, and communication. Such traces do not replace human studies, but they provide a scalable complement for controlled experimentation.

Finally, agentic information access should be studied as a communication ecosystem rather than as an isolated model answering an isolated query. We are therefore developing a social agentic layer above the retrieval infrastructure that supports persistent interaction among humans and agents, including delegation, collaboration, verification, and agent-to-agent communication.

Together, these hypotheses point toward a new kind of evaluation environment: one that combines open web data, scalable retrieval systems, human and artificial participants, and observable information-seeking trajectories. Future information-access research may therefore need to evaluate not only models and ranked lists, but complete systems in which humans, agents, retrieval services, and shared knowledge interact at realistic scale.

{{< figure src="img/clef26-speakers-granitzer.png" size="400x500" float="right" classes="w-64 pl-8" width="sm"  caption="Michael Granitzer" >}}

**About:** Michael Granitzer is a renowned researcher in data science, machine learning, information retrieval, and natural language processing. As a Professor of Data Science at the University of Passau, his research focuses on intelligent systems for data analysis and utilization, with significant contributions to personalized information retrieval, visual analytics, and user behavior analysis. With over 250 scientific publications, including books, book chapters, and journal articles, Michael Granitzer is widely recognized for his contributions to the field. He also leads major research projects, such as the Horizon Europe project “OpenWebSearch.eu.” His previous roles, including Scientific Director at the Know-Center in Graz and Professor of Media Informatics, demonstrate his expertise in interdisciplinary collaboration and leading large-scale research projects.

## Lucie Flek

**Title:** TBD.

**Date:** Tuesday, September 22

**Abstract:** TBD.

{{< figure src="img/clef26-speakers-flek.jpg" size="400x500" float="right" classes="w-64 pl-8" width="sm"  caption="Lucie Flek" >}}

**About:** Lucie Flek is a professor for Data Science & Language Technologies at The University of Bonn. Her research focuses on machine learning for Natural Language Processing, with core expertise in user modeling and stylistic variation. She investigates how individuals and sociodemographic groups differ in their language use, and how this variation can be leveraged to predict in-group behavior. This work has led to a broader engagement with bias in NLP, stereotype exaggeration, ethics, model performance on underrepresented groups, and domain adaptation. Her PhD addressed lexical semantics — specifically, the role of word ambiguity and context in document classification, and whether explicit disambiguation and semantic ontologies remain beneficial in the era of deep learning, particularly under limited training data. She has continued pursuing the low-resource paradigm in industry, leading projects in multilingual and multitask learning and various bootstrapping approaches for scarce labeled data. A strong advocate for cross-disciplinary collaboration, she has published jointly with educational researchers, psychologists, sociologists, physicists, and visual analysts.

## Suzan Verberne

**Title:** Conversational search: A promise fulfilled (or is it?)

**Date:**  Wednesday, September 23

**Abstract:** In the Information Retrieval (IR) community, we have long seen the promise of conversational search. When I did my PhD, Question Answering was considered the future of IR: interacting with a search engine in natural language was the holy grail. Well, here we are: the search engine of the future is a chatbot, and the IR community is not 100% excited. In my keynote at CLEF, I will discuss the role of IR in the era of generative AI. Is retrieval more than just a component in an AI system's toolbox? What is the relevance of retrieval in AI research and industrial applications? And which questions should our academic community prioritize? (Spoiler: evaluation is one of them.)

{{< figure src="img/clef26-speakers-verbene.jpg" size="400x500" float="right" classes="w-64 pl-8" width="sm"  caption="Suzan Verberne" >}}

**About:** Suzan Verberne is a Professor of Natural Language Processing at the Leiden Institute of Advanced Computer Science (LIACS), Leiden University. She obtained her PhD in 2010 on the topic of Question Answering at Radboud University in Nijmegen, and since then she has been working at the intersection of Natural Language Processing (NLP) and Information Retrieval (IR). She has supervised projects across a wide range of application domains and collaborations, from social media to law, and from archaeology to health. Her recent work centres on interactive information access for specific domains and low-resource contexts. She has a strong interest in the interplay between search engines and large language models, and a focus on evaluation beyond accuracy. Suzan is highly active in the NLP and IR communities and holds chairing positions at major international conferences. 

---
title: "eRisk"
draft: false
params:
  subtitle: "Early risk prediction on the internet"
  url: https://erisk.irlab.org/
menu:
  main:
    identifier: "lab-erisk"
    parent: "labs"
    weight: 40
---

eRisk explores the evaluation methodology, effectiveness metrics and practical applications (particularly those related to health and safety) of early risk detection on the Internet. Early detection technologies can be employed in different areas, particularly those related to health and safety. Our main goal is to pioneer a new interdisciplinary research area that would be potentially applicable to a wide variety of situations and to many different personal profiles.

<!--more-->

## Tasks

The eRisk Lab features three different tasks:

{{< accordion  open_all="true" >}}
  {{< accordion-item title="Conversational Depression Detection" >}}
  Detecting depression through conversational agents. Participants will interact with LLM personas fine-tuned with diverse user histories and released on Hugging Face. The challenge is to determine whether each persona exhibits signs of depression and, within a limited conversational window, identify active depressive symptoms and the overall depression level. 
  {{< /accordion-item >}}
  {{< accordion-item title="Contextualised Early Detection of Depression" >}}
  This task continues last year’s shift from isolated posts to full conversational contexts, aiming to capture real interaction dynamics across multiple speakers. Participants must process dialogues sequentially, accumulating evidence, where a message may only become informative when interpreted alongside preceding or subsequent publications.
  {{< /accordion-item >}}
  {{< accordion-item title="Sentence Ranking for ADHD Symptoms" >}}
  This new task targets sentence-level retrieval for the 18 symptoms defined in the Adult ADHD Self-Report Scale (ASRS–v1.1). Participants must rank candidate sentences by their relevance to each symptom. A sentence is considered relevant when it conveys information about the user’s state with respect to the target ADHD symptom (irrespective of polarity or stance), encouraging models to capture clinically meaningful evidence rather than surface keywords.
  {{< /accordion-item >}}
{{< /accordion >}}


## Organizers

- Anxo Pérez (University of A Coruña, Spain)
- Javier Parapar (University of A Coruña, Spain)
- Xi Wang (University of Sheffield, United Kingdom)
- Fabio Crestani (Università della Svizzera Italiana, Switzerland)  


---
layout: Conceptual
title: Securing the Future of AI and ML at Microsoft
description: This research papers shares some of Microsoft’s security lessons-learned from designing products and operating online services built on AI.
ms.date: 12/04/2018
ms.service: security
ms.author: bcowper
author: BruceCowper
ms.topic: conceptual
---

# Securing the Future of Artificial Intelligence and Machine Learning at Microsoft
By Andrew Marshall, Raul Rojas, Jay Stokes and Donald Brinkman

Special Thanks to Mark Cartwright and Graham Calladine

## Executive Summary
Artificial Intelligence (AI) and Machine Learning (ML) are already making a big impact on how people work, socialize, and live their lives. As consumption of products and services built around AI/ML increases, specialized actions must be undertaken to safeguard not only your customers and their data, but also to protect your AI and algorithms from abuse, trolling and extraction. This document shares some of Microsoft’s security lessons-learned from designing products and operating online services built on AI. While it is difficult to predict how this area will unfold, we have concluded that there are actionable issues to address now. Moreover, we found that there are strategic problems that the tech industry must get ahead of to insure the long-term safety of customers and security of their data.

This document is not about AI-based attacks or even AI being leveraged by human adversaries. Instead, we focus on issues that Microsoft and industry partners will need to address to protect AI-based products and services from highly sophisticated, creative and malicious attacks, whether carried out by individual trolls or entire wolfpacks.

This document focuses entirely on security engineering issues unique to the AI/ML space, but due to the expansive nature of the InfoSec domain it is understood that issues and findings discussed here will overlap to a degree with the domains of privacy and ethics. As this document highlights challenges of strategic importance to the tech industry, the target audience for this document is security engineering leadership industry-wide.

Our early findings suggest that:

  - AI/ML-specific pivots to existing security practices are required to mitigate the types of security issues discussed in this document.

  - Machine Learning models are largely unable to discern between malicious input and benign anomalous data. A significant source of training data is derived from un-curated, unmoderated, public datasets which are open to 3<sup>rd</sup>-party contributions.   Attackers don’t need to compromise datasets when they are free to contribute to them. Over time, low-confidence malicious data becomes high-confidence trusted data, provided that the data structure/formatting remains correct.

  - Given the great number of layers of hidden classifiers/neurons which can be leveraged in a deep learning model, too much trust is placed on the output of AI/ML decision-making processes and algorithms without a critical understanding of how these decisions were
    reached. This obfuscation creates an inability to “show your work” and makes it difficult to provably defend AI/ML findings when called into question.

  - AI/ML is increasingly used in support of high-value decision-making processes in medicine and other industries where the wrong decision may result in serious injury or death. A lack of forensics reporting capabilities in AI/ML prevent these high-value conclusions from
    being defensible in both the court of law and court of public opinion.

The goals of this document are to (1) highlight security engineering issues which are unique to the AI/ML space, (2) surface some initial thoughts and observations on emerging threats and (3) share early thoughts on potential remediation. Some of the challenges in this document are problems that the industry needs to get ahead of in the next two years, others are issues that we’re already being forced to address today. Without deeper investigation into the areas covered in this document, we risk future AI becoming a black box to its  through our inability to trust or understand (and modify if necessary) AI decision-making processes at a mathematical level [7]. From a security perspective, this effectively means loss of control and a departure from Microsoft’s guiding principles on Artificial Intelligence [4, 8].

## New Security Engineering Challenges
Traditional software attack vectors are still critical to address, but they do not provide sufficient coverage in the AI/ML threat landscape. The tech industry must avoid fighting next-gen issues with last-gen solutions by building new frameworks and adopting new approaches which address gaps in the design and operation of AI/ML-based services:

1. As discussed below, secure development and operations foundations must incorporate the concepts of Resilience and Discretion when protecting AI and the data under its control. AI-specific pivots are required in the areas of Authentication, Separation of Duty, Input Validation and Denial of Service mitigation. Without investments in these areas, AI/ML services will continue to fight an uphill battle against adversaries of all skill levels.

2. AI must be able to recognize bias in others, without being biased in its own interactions with humans. Accomplishing this requires a collective and evolving understanding of biases, stereotypes, vernacular, and other cultural constructs. Such an understanding will help protect AI from social engineering and dataset tampering attacks. A properly implemented system will actually become stronger from such attacks and be able to share its expanded understanding with other AIs.

3. Machine Learning algorithms must be capable of discerning maliciously-introduced data from benign “Black Swan” events [1] by rejecting training data with negative impact on results. Otherwise, learning models will always be susceptible to gaming by attackers and trolls.

4. AI must have built-in forensic capabilities. This enables enterprises to provide customers with transparency and accountability of their AI, ensuring its actions are not only verifiably correct but also legally defensible. These capabilities also function as an early form of “AI intrusion detection”, allowing engineers to determine the exact point in time that a decision was made by a classifier, what data influenced it, and whether or not that data was trustworthy. Data visualization capabilities in this area are rapidly advancing and show promise to help engineers identify and resolve root causes for these complex issues [11].

5. AI must recognize and safeguard sensitive information, even if humans don’t recognize it as such. Rich user experiences in AI require vast amounts of raw data to train on, so “over-sharing” by customers must be planned for.

Each of these areas, including threats and potential mitigations, is discussed in detail below.

## AI requires new pivots to traditional secure design/secure operations models: the introduction of Resilience and Discretion
AI designers will always need to ensure the confidentiality, integrity and availability of sensitive data, that the AI system is free of known vulnerabilities, and provide controls for the protection, detection and response to malicious behavior against the system or the user’s data.

The traditional ways of defending against malicious attacks do not provide the same coverage in this new paradigm, where voice/video/image-based attacks can circumvent current filters and
defenses. New threat modeling aspects must be explored in order to prevent new abuses from exploiting our AI. This goes far beyond identifying traditional attack surface via fuzzing or input manipulation (those attacks have their own AI-specific pivots too). It requires
incorporating scenarios unique to the AI/ML space. Key among these are AI user experiences such as voice, video and gestures. The threats associated with these experiences have not been traditionally modeled. For example, video content is now being tailored to induce physical effects. Additionally, research has demonstrated that audio-based attack
commands can be crafted [10].

The unpredictability, creativity, and maliciousness of criminals, determined adversaries, and trolls requires us to instill our AIs with the values of **Resilience** and **Discretion**:

**Resilience:** The system should be able to identify abnormal behaviors and prevent manipulation or coercion outside of normal boundaries of acceptable behavior in relation to the AI system and the specific task. These are new types of attacks specific to the AI/ML space. Systems should be designed to resist inputs that would otherwise conflict with local laws, ethics and values held by the community and its creators. This means providing AI with the capability to determine when an interaction is going “off script.” This could be achieved with the following methods:

1. Pinpoint individual users who deviate from norms set by the various large clusters of similar users e.g. users who seem to type to fast, respond too fast, don’t sleep, or trigger parts of the system other users do not.

2. Identify patterns of behavior that are known to be indicators of malicious intent probing attacks and the start of the [Network Intrusion Kill Chain](https://en.wikipedia.org/wiki/Kill_chain).

3. Recognize any time when multiple users act in a coordinated fashion; e.g., multiple users all issuing the same unexplainable yet deliberately crafted query, sudden spikes in the number of users or sudden spikes in activation of specific parts of an AI system.

Attacks of this type should be considered on par with Denial of Service attacks since the AI may require bugfixes and retraining in order not to fall for the same tricks again. Of critical importance is the ability to identify malicious intent in the presence of countermeasures such as those used to defeat sentiment analysis APIs [5].

**Discretion**: AI should be a responsible and trustworthy custodian of *any* information it has access to. As humans, we will undoubtedly assign a certain level of trust in our AI relationships. At some point, these agents will talk to other agents or other humans on our behalf. We must be able to trust that an AI system has enough discretion to only share in a restricted form what it needs to share about us so other agents can complete tasks on its behalf. Furthermore, multiple agents interacting with personal data on our behalf should not each need global access to it. Any data access scenarios involving multiple AIs or bot agents should limit the lifetime of access to the minimum extent required. Users should also be able to deny data and reject the authentication of agents from specific corporations or locales just as web browsers allow site blocklisting today. Solving this problem requires new thinking on inter-agent authentication and data access privileges like the cloud-based user authentication investments made in the early years of cloud computing.

## AI must be able to recognize bias in others without being biased on its own
While AI should be fair and inclusive without discriminating against any particular group of individuals or valid outcomes, it needs to have an innate understanding of bias to achieve this. Without being trained to recognize bias, trolling, or sarcasm, AI will be duped by those seeking cheap laughs at best, or cause harm to customers at worst.

Achieving this level of awareness calls for “good people teaching AI bad things” as it effectively requires a comprehensive and evolving understanding of cultural biases. AI should be able to recognize a user it has had negative interactions with in the past and exercise
appropriate caution, similar to how parents teach their children to be wary of strangers. The best way to approach this is by carefully exposing the AI to trolls in a controlled/moderated/limited fashion. This way AI can learn the difference between a benign user “kicking the tires” and actual maliciousness/trolling. Trolls provide a valuable
stream of training data for AI, making it more resilient against future attacks.

AI should also be able to recognize bias in datasets it trains on. This could be cultural or regional, containing the vernacular in use by a particular group of people, or topics/viewpoints of specific interest to one group. As with maliciously-introduced training data, AI must be resilient to the effects of this data on its own inferences and deductions. At its core, this is a sophisticated input validation issue with similarities to bounds checking. Instead of dealing with buffer lengths and offsets, the buffer and bounds checks are red-flagged words from a broad range of sources. The conversation history and context in
which words are used are also key. Just as defense-in-depth practices are used to layer protections on top of a traditional Web Service API frontend, multiple layers of protection should be leveraged in bias recognition and avoidance techniques.

## Machine Learning Algorithms must be capable of discerning maliciously-introduced data from benign “Black Swan” events
Numerous whitepapers have been published on the theoretical potential of ML model/classifier tampering and extraction/theft from services where attackers have access to both the training data set and an informed understanding of the model in use [2, 3, 6, 7]. The over-arching issue here is that all ML classifiers can be tricked by an attacker who has control over training set data. Attackers don’t even need the ability to modify existing training set data, they just need to be able to add to it and have their inputs become “trusted” over time through the ML classifier’s inability to discern malicious data from genuine anomalous data.

This training data supply chain issue introduces us to the concept of “Decision Integrity” – the ability to identify and reject maliciously introduced training data or user input before it has a negative impact on classifier behavior. The rationale here is that trustworthy training data has a higher probability of generating trustworthy outcomes/decisions. While it is still crucial to train on and be resilient to untrusted data, the malicious nature of that data should be analyzed prior to it becoming part of a high-confidence body of training data. Without such measures, AI could be coerced into overreacting to trolling and deny service to legitimate users.

This is of particular concern where unsupervised learning algorithms are training on uncurated or untrusted datasets. This means that attackers can introduce any data they want provided the format is valid and the algorithm is trained on it, effectively trusting that data point equally with the rest of the training set. With enough crafted inputs from the attacker, the training algorithm loses the ability to discern noise and anomalies from high-confidence data.

As an example of this threat, imagine a database of stop signs throughout the world, in every language. That would be extremely challenging to curate because of the number of images and languages involved. Malicious contribution to that dataset would go largely unnoticed until self-driving cars no longer recognize stop signs. Data resilience and decision integrity mitigations will have to work hand in hand here to identify and eliminate the training damage done by malicious data to prevent it from becoming a core part of the learning model.

## AI must have built-in forensics and security logging to provide transparency and accountability
AI will eventually be capable of acting in a professional capacity as an agent on our behalf, assisting us with high-impact decision-making. An example of this could be an AI that assists in the processing of financial transactions. If the AI were exploited, and transactions manipulated in some way, the consequences could range from the individual to the systemic. In high-value scenarios, AI will need appropriate forensic and security logging to provide integrity, transparency, accountability, and in some instances, evidence where civil or criminal liability may arise.

Essential AI services will need auditing/event-tracing facilities at the algorithm level whereby developers can examine the recorded state of specific classifiers which may have led to an inaccurate decision. This capability is needed industry-wide in order to prove the correctness and transparency of AI-generated decisions whenever called into question.

Event tracing facilities could start with the correlation of basic decision-making information such as:

1. The timeframe in which the last training event occurred

2. The timestamp of the most recent dataset entry trained upon

3. Weights and confidence levels of key classifiers used to arrive at high-impact decisions

4. The classifiers or components involved in the decision

5. The final high-value decision reached by the algorithm

Such tracing is overkill for the majority of algorithm-assisted decision making. However, having the ability to identify the data points and algorithm metadata leading to specific results will be of great benefit in high-value decision making. Such capabilities will not only demonstrate trustworthiness and integrity through the algorithm’s ability to “show its work”, but this data could also be used for fine-tuning as well.

Another forensic capability needed in AI/ML is tamper detection. Just as we need our AIs to recognize bias and not be susceptible to it, we should have forensic capabilities available to aid our engineers in detecting and responding to such attacks. Such forensic capabilities
will be of tremendous value when paired with data visualization techniques [11] allowing the auditing, debugging and tuning of algorithms for more effective results.

## AI must safeguard sensitive information, even if humans don’t
Rich experiences require rich data. Humans already volunteer vast amounts of data for ML to train against. This ranges from the mundane video streaming queue contents to trends in credit card purchases/transaction histories used to detect fraud. AI should have an ingrained sense of discretion when it comes to handling user data, always acting to protect it even when it is volunteered freely by an over-sharing public.

As an AI can have an authenticated group of “peers” it talks to in order to accomplish complex tasks, it must also recognize the need to restrict the data it shares with those peers.

## Early Observations on Addressing AI Security Issues
Despite the nascent state of this project, we believe the evidence compiled to date shows deeper investigation into each of the areas below will be key in moving our industry towards more trustworthy and secure AI/ML products/services. The following are our early observations and thoughts on what we’d like to see done in this space.

1. AI/ML-focused penetration testing and security review bodies could be established to ensure that our future AI shares our values and aligns to the [Asilomar AI
    Principles](https://futureoflife.org/ai-principles/).
    1. Such a group could also develop tools and frameworks that could be consumed industry-wide in support of securing their AI/ML-based services.
    2. Over time, this expertise will build up within engineering groups organically, as it did with traditional security expertise over the past 10 years.

2. Training could be developed which empowers enterprises to deliver on goals such as democratizing AI while mitigating the challenges discussed in this document.
    1. AI-specific security training ensures that engineers are aware of the risks posed __to__ their AI and the resources at their disposal. This material needs to be delivered in conjunction with current training on protecting customer data.
    2. This could be accomplished without requiring every data scientist to become a security expert – instead, the focus is placed on educating developers on Resilience and Discretion as applied to their AI use cases.
    3. Developers will need to understand the secure “building blocks” of AI services that will be reused across their enterprise. There will need to be an emphasis on fault-tolerant design with subsystems which can be easily turned off (e.g. image processors, text parsers).

3. ML Classifiers and their underlying algorithms could be hardened and capable of detecting malicious training data without it contaminating valid training data currently in use or skewing the results.
    1. Techniques such as Reject on Negative Input [6] need researcher cycles to investigate.

    2. This work involves mathematical verification, proof-of-concept in code, and testing against both malicious and benign anomalous data.

    3. Human spot-checking/moderation may be beneficial here,  particularly where statistical anomalies are present.

    4. “Overseer classifiers” could be built to have a more universal understanding of threats across multiple AIs. This vastly improves the security of the system because the attacker can no longer exfiltrate any one particular model.

    5. AIs could be linked together to identify threats in each other’s systems

4. A centralized ML auditing/forensics library could be built that establishes a standard for transparency and trustworthiness of AI.

    1. Query capabilities could also be built for auditing and reconstruction of high business impact decisions by AI.

5. The vernacular in use by adversaries across different cultural groups and social media could be continuously inventoried and analyzed by AI in order to detect and respond to trolling, sarcasm, etc.

    1. AIs need to be resilient in the face of all kinds of vernacular, whether technical, regional, or forum-specific.

    2. This body of knowledge could also be leveraged in content    filtering/labeling/blocking automation to address moderator scalability issues.

    3. This global database of terms could be hosted in development libraries or even exposed via cloud service APIs for reuse by different AIs, ensuring new AIs benefit from the  combined wisdom of older ones.

6. A “Machine Learning Fuzzing Framework” could be created which provides engineers with the ability to inject various types of attacks into test training sets for AI to evaluate.

    1. This could focus on not only text vernacular, but image, voice and gesture data as well as permutations of those data types.

## Conclusion
The [Asilomar AI Principles](https://futureoflife.org/ai-principles/) illustrate the complexity of delivering on AI in a fashion that consistently benefits humanity. Future AIs will need to interact with other AIs to deliver rich, compelling user experiences. That means it simply is not good enough for Microsoft to “get AI right” from a security perspective – the *world* has to. We need industry alignment and collaboration with greater visibility brought to the issues in this document in a fashion similar to our worldwide push for a Digital Geneva Convention [9]. By addressing the issues presented here, we can begin guiding our customers and industry partners down a path where AI is truly democratized and augments the intelligence of all humanity.

## Bibliography
  [1] *Taleb, Nassim Nicholas (2007),* The Black Swan: The Impact of the Highly Improbable, Random House, [ISBN 978-1400063512](https://en.wikipedia.org/wiki/Special:BookSources/978-1400063512)

  [2] *Florian Tramèr, Fan Zhang, Ari Juels, Michael K. Reiter, Thomas Ristenpart,* [Stealing Machine Learning Models via Prediction APIs]( <https://arxiv.org/abs/1609.02943>)

  [3] *Ian GoodFellow, Nicolas Papernot, Sandy Huang, Yan Duan, Pieter Abbeel and Jack Clark:* [Attacking machine learning with adversarial examples]( <https://blog.openai.com/adversarial-example-research/>)

  [4] *Satya Nadella:* [The Partnership of the Future](<https://www.slate.com/articles/technology/future_tense/2016/06/microsoft_ceo_satya_nadella_humans_and_a_i_can_work_together_to_solve_society.html>)

  [5] *Claburn, Thomas:* [Google's troll-destroying AI can't cope with typos](<https://www.theregister.co.uk/2017/03/02/google_trollspotting_ai_trips_over_typos/>)

  [6] *Marco Barreno, Blaine Nelson, Anthony D. Joseph, J.D. Tygar:* [The security of machine learning](<https://people.eecs.berkeley.edu/~adj/publications/paper-files/SecML-MLJ2010.pdf>)

  [7] *Wolchover, Natalie:* [This Artificial Intelligence Pioneer Has a Few Concerns](<https://www.wired.com/2015/05/artificial-intelligence-pioneer-concerns/>)

  [8] *Conn, Ariel:* [How Do We Align Artificial Intelligence with Human Values?](<https://futureoflife.org/2017/02/03/align-artificial-intelligence-with-human-values/>)

  [9] *Smith, Brad:* [The need for urgent collective action to keep people safe online: Lessons from last week’s cyberattack](https://blogs.microsoft.com/on-the-issues/2017/05/14/need-urgent-collective-action-keep-people-safe-online-lessons-last-weeks-cyberattack/)

  [10] *Nicholas Carlini, Pratyush Mishra, Tavish Vaidya, Yuankai Zhang, Micah Sherr, Clay Shields, David Wagner, Wenchao Zhou:* [Hidden Voice Commands](<https://www.usenix.org/conference/usenixsecurity16/technical-sessions/presentation/carlini>)

  [11] *Fernanda Viégas, Martin Wattenberg, Daniel Smilkov, James Wexler, Jimbo Wilson, Nikhil Thorat, Charles Nicholson, Google Research:* [Big Picture](<https://research.google.com/bigpicture/>)

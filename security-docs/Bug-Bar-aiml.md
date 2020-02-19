---
# This basic template provides core metadata fields for Markdown articles on docs.microsoft.com.

# Mandatory fields.
title: AI/ML Pivots to the Security Development Lifecycle Bug Bar
description: Machine Learning Bug Triage Guidance
author: Andrew Marshall
ms.author: Andrew Marshall
ms.date: 11/11/2019
ms.topic: article
ms.prod: security
---

# AI/ML Pivots to the Security Development Lifecycle Bug Bar

By Andrew Marshall, Jugal Parikh, Emre Kiciman and Ram Shankar Siva
Kumar

November 2019

This document is a deliverable of the Microsoft [AETHER Engineering Practices for
AI Working
Group](https://news.microsoft.com/2018/03/29/satya-nadella-email-to-employees-embracing-our-future-intelligent-cloud-and-intelligent-edge/)
and functions as a supplement to the existing SDL bug
bar used to triage traditional security vulnerabilities.
It is intended to be used as a reference for the triage of AI/ML-related
security issues.
For more detailed threat analysis and mitigation information, refer to
[Threat Modeling AI/ML Systems and
Dependencies](https://docs.microsoft.com/en-us/security/threat-modeling-aiml).

This guidance is organized around and extensively references the Adversarial Machine Learning Threat Taxonomy created by Ram Shankar Siva Kumar, David O’Brien, Kendra Albert, Salome Viljoen, and Jeffrey Snover entitled [Failure Modes in Machine Learning](https://docs.microsoft.com/en-us/security/failure-modes-in-machine-learning). Note that while the research this content is based on addresses both intentional/malicious and accidental behaviors in ML failure modes, this bug bar supplement focuses entirely on intentional/malicious behaviors that would result in a security incident and/or deployment of a fix.

<table>
<thead>
<tr class="header">
<th align="left">Threat</th>
<th align="left">Severity</th>
<th align="left">Description/Business Risks/Examples</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Data Poisoning</td>
<td align="left">Important to Critical</td>
<td align="left"><p>Corrupting the training data - The end goal of the attacker is to contaminate the machine model generated <em>in the training phase</em>, so that predictions on new data will be modified in the testing phase.</p>
<p>In targeted poisoning attacks, the attacker wants to misclassify specific examples to cause specific actions to be taken or omitted.</p>
<p>Submitting AV software as malware to force its misclassification as malicious and eliminate the use of targeted AV software on client systems. </p>
<p>A company scrapes a well-known and trusted website for futures data to train their models. The data provider’s website is subsequently compromised via SQL Injection attack. The attacker can poison the dataset at will and the model being trained has no notion that the data is tainted.</p></td>
</tr>
<tr class="even">
<td align="left">Model Stealing</td>
<td align="left">Important to Critical</td>
<td align="left"><p>Recreation of the underlying model by legitimately querying it. The functionality of the new model is same as that of the underlying model. Once the model is recreated, it can be inverted to recover feature information or make inferences on training data. </p>
<p>Equation solving – For a model that returns class probabilities via API output, an attacker can craft queries to determine unknown variables in a model.</p>
<p>Path Finding – an attack that exploits API particularities to extract the ‘decisions’ taken by a tree when classifying an input.</p>
<p>Transferability attack - An adversary can train a local model—possibly by issuing prediction queries to the targeted model - and use it to craft adversarial examples that transfer to the target model. If your model is extracted and discovered vulnerable to a type of adversarial input, new attacks against your production-deployed model can be developed entirely offline by the attacker who extracted a copy of your model.</p>
<p>In settings where an ML model serves to detect adversarial behavior, such as identification of spam, malware classification, and network anomaly detection, model extraction can facilitate evasion attacks</p></td>
</tr>
<tr class="odd">
<td align="left">Model Inversion</td>
<td align="left">Important to Critical</td>
<td align="left"><p>The private features used in machine learning models can be recovered. This includes reconstructing private training data that the attacker does not have access to. This is accomplished by finding the input which maximizes the confidence level returned, subject to the classification matching the target.</p>
<p>Example: Reconstruction of facial recognition data from guessed or known names and API access to query the model.</p></td>
</tr>
<tr class="even">
<td align="left">Adversarial Example in Physical Domain</td>
<td align="left">Critical</td>
<td align="left">These examples can manifest in the physical domain, like a self-driving car being tricked into running a stop sign because of a certain color of light (the adversarial input) being shone on the stop sign, forcing the image recognition system to no longer see the stop sign as a stop sign.  </td>
</tr>
<tr class="odd">
<td align="left">Attack ML Supply Chain</td>
<td align="left">Critical</td>
<td align="left"><p>Owing to large resources (data + computation) required to train algorithms, the current practice is to reuse models trained by large corporations and modify them slightly for task at hand (e.g: ResNet is a popular image recognition model from Microsoft).</p>
<p>These models are curated in a Model Zoo (Caffe hosts popular image recognition models).</p>
<p>In this attack, the adversary attacks the models hosted in Caffe, thereby poisoning the well for anyone else.</p></td>
</tr>
<tr class="even">
<td align="left">Backdoored Algorithm from Malicious ML Provider</td>
<td align="left">Critical</td>
<td align="left"><p>Compromising the underlying algorithm</p>
<p>A malicious ML-as-a-Service provider presents a backdoored algorithm, wherein the private training data is recovered. This provides the attacker with the ability to reconstruct sensitive data such as faces and texts, given only the model.</p></td>
</tr>
<tr class="odd">
<td align="left">Neural Net Reprogramming</td>
<td align="left">Important to Critical</td>
<td align="left"><p>By means of a specially crafted query from an attacker, ML systems can be reprogrammed to a task that deviates from the creator’s original intent</p>
<p>Weak access controls on a facial recognition API enabling 3<sup>rd</sup> parties to incorporate into apps designed to harm users, such as a deep fakes generator.</p>
<p>This is an abuse/account takedown scenario</p></td>
</tr>
<tr class="even">
<td align="left">Adversarial Perturbation</td>
<td align="left">Important to Critical</td>
<td align="left"><p>In perturbation-style attacks, the attacker stealthily modifies the query to get a desired response from a <em>production-deployed model</em>. This is a breach of model input integrity which leads to fuzzing-style attacks where the end result isn’t necessarily an access violation or EOP, but instead compromises the model’s classification performance.</p>
<p>This can be manifested by trolls using certain target words in a way that the AI will ban them, effectively denying service to legitimate users with a name matching a “banned” word.</p>
<p>Forcing benign emails to be classified as spam or causing a malicious example to go undetected. These are also known as model evasion or mimicry attacks.</p>
<p>Attacker can craft inputs to reduce the confidence level of correct classification, especially in high-consequence scenarios. This can also take the form of a large number of false positives meant to overwhelm administrators or monitoring systems with fraudulent alerts indistinguishable from legitimate alerts.</p></td>
</tr>
<tr class="odd">
<td align="left">Membership Inference</td>
<td align="left">Moderate to Critical</td>
<td align="left"><p>Infer individual membership in a group used to train a model</p>
<p>Ex: prediction of surgical procedures based on age/gender/hospital</p></td>
</tr>
</tbody>
</table>



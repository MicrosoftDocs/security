---
# This basic template provides core metadata fields for Markdown articles on docs.microsoft.com.

# Mandatory fields.
title: Failure Modes in Machine Learning
description: Machine Learning Threat Taxonomy
author: AMarshal
ms.author: AMarshal
ms.date: 11/11/2019
ms.topic: article
ms.prod: security
---

# Failure Modes in Machine Learning

<table style="text-align:left" border="0">
  <tr>
    <th>Microsoft Corporation</th>
    <th>Berkman Klein Center for Internet and Society at Harvard University</th>
    
  </tr>
  <tr>
    <td><p><a href="mailto:ram.shankar@microsoft.com">Ram Shankar Siva Kumar</a></p></td>
    <td><p><a href="mailto:dobrien@cyber.harvard.edu">David O’Brien</a></p></td>
    
  </tr>
  <tr>
    <td><p><a href="mailto:jsnover@microsoft.com">Jeffrey Snover</a></p></td>
    <td><p><a href="mailto:kalbert@law.harvard.edu">Kendra Albert</a></p></td>
    
  </tr>
  <tr>
    <td></td>
    <td><p><a href="mailto:sviljoen@cyber.harvard.edu">Salome Viljoen</a></p></td>
  </tr>
</table>

November 2019

## Introduction & Background

In the last two years, more than 200 papers have been written on how
Machine Learning (ML) can fail because of adversarial attacks on the
algorithms and data; this number balloons if we were to incorporate
non-adversarial failure modes. The spate of papers has made it difficult
for ML practitioners, let alone engineers, lawyers and policymakers, to
keep up with the attacks against and defenses of ML systems. However, as
these systems become more pervasive, the need to understand how they
fail, whether by the hand of an adversary or due to the inherent design
of a system, will only become more pressing. The purpose of this
document is to jointly tabulate both the of these failure modes in a
single place.

-   *Intentional failures* wherein the failure is caused by an active
    adversary attempting to subvert the system to attain her goals –
    either to misclassify the result, infer private training data, or to
    steal the underlying algorithm.

-   *Unintentional failures* wherein the failure is because an ML system
    produces a formally correct but completely unsafe outcome.

We would like to point out that there are other taxonomies and
frameworks that individually highlight intentional failure
modes[1]<sup>,</sup>[2] and unintentional failure
modes[3]<sup>,</sup>[4]. Our classification brings the two separate
failure modes together in one place and addresses the following needs:

1.  The need to equip software developers, security incident responders, lawyers, and policy makers with a common vernacular to talk about this problem. After developing the initial version of the taxonomy last year, we worked with security and ML teams across Microsoft, 23 external partners, standards organization, and governments to understand how stakeholders would use our framework. Based on this usability study and stakeholder feedback, we iterated on the framework.

    *Results:* When presented with an ML failure mode, we frequently observed that software developers and lawyers mentally mapped the ML failure modes to traditional software attacks like data exfiltration. So, throughout the paper, we attempt to highlight how machine learning failure modes are meaningfully different from traditional software failures from a technology and policy perspective.

2.  The need for a common platform for engineers to build on top of and to integrate into their existing software development and security practices. Broadly, we wanted the taxonomy to be more than an educational tool – we want it to effectuate tangible engineering outcomes.

    *Results:* Using this taxonomy as a lens, Microsoft modified its
    [Security Development Lifecycle](https://www.microsoft.com/securityengineering/sdl/) process for its entire organization.
    Specifically, data scientists and security engineers at Microsoft now
    share the common language of this taxonomy, allowing them to more effectively threat model their ML systems before
    deploying to production; Security Incident Responders also have a
    bug bar to triage these net-new threats specific to ML, the standard process for vulnerabilities triage and response used by the Microsoft Security Response Center and all Microsoft product teams.  
    <p>

3.  The need for a common vocabulary to describe these attacks amongst policymakers and lawyers. We believe that this  for describing different ML failure modes and analysis of how their harms might be regulated is a meaningful first step towards informed policy.

    *Results:* This taxonomy is written for a wide interdisciplinary audience – so, policymakers who are looking at the issues from a general ML/AI perspective, as well as specific domains such as misinformation/healthcare should find the failure mode catalogue useful. We also highlight any applicable legal interventions to address the failure modes.

See also Microsoft's [Threat Modeling AI/ML Systems and Dependencies](https://docs.microsoft.com/security/threat-modeling-aiml) and [SDL Bug Bar Pivots for Machine Learning Vulnerabilities](https://docs.microsoft.com/security/bugbar-aiml-threats).

## How to use this document

At the outset, we acknowledge that this is a living document which will evolve over time with the threat landscape.
We also do not prescribe technological
mitigations to these failure modes here, as defenses are scenario-specific
and tie in with the threat model and system architecture under consideration.  Options presented for threat mitigation are based on current research with the expectation that those defenses will evolve over time as well.

For engineers, we recommend browsing through the overview of possible
failure modes and jumping into the [threat modeling document](https://docs.microsoft.com/security/threat-modeling-aiml). This way,
engineers can identify threats, attacks, vulnerabilities and use the
framework to plan for countermeasures where available. We then refer you
to the bug bar that maps these new vulnerabilities in the taxonomy
alongside traditional software vulnerabilities, and provides a rating
for each ML vulnerability (such as critical, important). This bug bar
is easily integrated into existing incident response processes/playbooks.

For lawyers and policy makers, this document organizes ML failure modes
and presents a framework to analyze key issues relevant for
anyone exploring policy options, such as the work done
here[5]<sup>,</sup>[6]. Specifically, we have categorized failures and
consequences in a way that policy makers can begin to draw distinctions
between causes, which will inform the public policy initiatives to
promote ML safety and security. We hope that policy makers will use
these categories begin to flesh out how existing legal regimes may (not)
adequately capture emerging issues, what historical legal regimes or
policy solutions might have dealt with similar harms, and where we
should be especially sensitive to civil liberties issues.

## Document Structure

In both the *Intentional Failure Modes* and *Unintentional Failure
Modes* sections, we provide a brief definition of the attack, and
an illustrative example from literature.

In the *Intentional Failure Modes* section, we provide the additional
fields:

1. What does the attack attempt to compromise in the ML system – Confidentiality, Integrity or Availability? We define Confidentiality as assuring that the components of the ML system (data, algorithm, model) are accessible only by authorized parties; Integrity is defined as assuring that the ML system can be modified only by authorized parties; Availability is defined as an assurance that the ML system is accessible to authorized parties. Together, Confidentiality, Integrity and Availability is called the CIA triad. For each intentional failure mode, we attempt to identify which of the CIA triad is compromised.

2. How much knowledge is required to mount this attack – blackbox or whitebox? In Blackbox style attacks., the attacker does NOT have direct access to the training data, no knowledge of the ML algorithm used and no access to the source code of the model. The attacker only queries the model and observes the response. In a whitebox style attack the attacker has knowledge of either ML algorithm or access to the model source code.  

3. Commentary on if the attacker is violating traditional technological notion of access/authorization.

## Intentionally-Motivated Failures Summary

<p>
<table  width="100%"  border="1">
  <tr>
    <th><center>Scenario Number</center></th>
    <th><center>Attack</center></th>
    <th><center>Overview</center></th>
    <th><center>Violates traditional technological notion of access/authorization?</center></th>
  </tr>
  <tr>
    <td><center>1</center></td>
    <td><center>Perturbation attack </center></td>
    <td><center>Attacker modifies the query to get appropriate response</center></td>
    <td><center>No</center></td>
  </tr>
  <tr>
    <td><center>2</center></td>
    <td><center>Poisoning attack </center></td>
    <td><center>Attacker contaminates the training phase of ML systems to get intended result</center></td>
    <td><center>No</center></td>
  </tr>
  <tr>
    <td><center>3</center></td>
    <td><center>Model Inversion</center></td>
    <td><center>Attacker recovers the secret features used in the model by through careful queries</center></td>
    <td><center>No</center></td>
  </tr>
  <tr>
    <td><center>4</center></td>
    <td><center>Membership Inference</center></td>
    <td><center>Attacker can infer if a given data record was part of the model’s training dataset or not</center></td>
    <td><center>No</center></td>
  </tr>
  <tr>
    <td><center>5</center></td>
    <td><center>Model Stealing</center></td>
    <td><center>Attacker is able to recover the model through carefully-crafted queries</center></td>
    <td><center>No</center></td>
  </tr>
  <tr>
    <td><center>6</center></td>
    <td><center>Reprogramming ML system</center></td>
    <td><center>Repurpose the ML system to perform an activity it was not programmed for</center></td>
    <td><center>No</center></td>
  </tr>
  <tr>
    <td><center>7</center></td>
    <td><center>Adversarial Example in Physical Domain </center></td>
    <td><center>Attacker brings adversarial examples into physical domain to subvertML system e.g: 3d printing special eyewear to fool facial recognition system</center></td>
    <td><center>No</center></td>
  </tr>
  <tr>
    <td><center>8</center></td>
    <td><center>Malicious ML provider recovering training data </center></td>
    <td><center>Malicious ML provider can query the model used by customer and recover customer’s training data </center></td>
    <td><center>Yes</center></td>
  </tr>
  <tr>
    <td><center>9</center></td>
    <td><center>Attacking the ML supply chain</center></td>
    <td><center>Attacker compromises the ML models as it is being downloaded for use</center></td>
    <td><center>Yes</center></td>
  </tr>
  <tr>
    <td><center>10</center></td>
    <td><center>Backdoor ML </center></td>
    <td><center>Malicious ML provider backdoors algorithm to activate with a specific trigger</center></td>
    <td><center>Yes</center></td>
  </tr>
  <tr>
    <td><center>11</center></td>
    <td><center>Exploit Software Dependencies</center></td>
    <td><center>Attacker uses traditional software exploits like buffer overflow to confuse/control ML systems</center></td>
    <td><center>Yes</center></td>
  </tr>
</table>

## Unintended Failures Summary
<p>
<table  width="100%"   border="1">
  <tr>
    <th><center>Scenario #</th>
    <th><center>Failure</th>
    <th><center>Overview</th>
  </tr>
  <tr>
    <td><center>12</center></td>
    <td><center>Reward Hacking</center></td>
    <td><center>Reinforcement Learning (RL) systems act in unintended ways because of mismatch between stated reward and true reward</center></td>
  </tr>
  <tr>
    <td><center>13</center></td>
    <td><center>Side Effects</center></td>
    <td><center>RL system disrupts the environment as it tries to attain its goal</center></td>
  </tr>
  <tr>
    <td><center>14</center></td>
    <td><center>Distributional shifts</center></td>
    <td><center>The system is tested in one kind of environment, but is unable to adapt to changes in other kinds of environment</center></td>
  </tr>
  <tr>
    <td><center>15</center></td>
    <td><center>Natural Adversarial Examples</center></td>
    <td><center>Without attacker perturbations, the ML system fails owing to hard negative mining</center></td>
  </tr>
  <tr>
    <td><center>16</center></td>
    <td><center>Common Corruption</center></td>
    <td><center>The system is not able to handle common corruptions and perturbations such as tilting, zooming, or noisy images.</center></td>
  </tr>
  <tr>
    <td><center>17</center></td>
    <td><center>Incomplete Testing</center></td>
    <td><center>The ML system is not tested in the realistic conditions that it is meant to operate in.</center></td>
  </tr>
</table>
<p>

## Details on Intentionally-Motivated Failures

<p>
<table  width="100%"  border="1"  style="text-align:center" margin="0 auto" padding="0">
  <tr>
    <th>Scenario #</th>
    <th>Attack Class</th>
    <th>Description</th>
    <th>Type of Compromise</th>
    <th>Scenario</th>
    <!-- <th>Is the attacker [technologically] misusing the system?   </th> -->
  </tr>
  <tr>
    <td>1 </td>
    <td>Perturbation attacks </td>
    <td>In perturbation style attacks, the attacker stealthily modifies the query to get a desired response </td>
    <td>Integrity</td>
    <td>Image: Noise is added to an X-ray image, which makes the predictions go from normal scan to abnormal  [1][Blackbox]<p>  
    Text translation: Specific characters are manipulated to result in incorrect translation. The attack can suppress specific word or can even remove the word completely[2][Blackbox and Whitebox]<p>
    Speech: Researchers showed how given a speech waveform, another waveform can be exactly replicated but transcribes into a totally different text[3][Whitebox but may be extended to blackbox]</td>
    <!-- <td>In a blackbox setting no special privileges are required by the attacker to perform the attack. The attacker generates the perturbations offline and queries the system legitimately.<p>There seems to be no technological access violations<p>Just like a legitimate user sends in a legitimate image, the attacker sends in a corrupted image for classification to purposely confuse the system.     </td> -->
  </tr>
  <tr>
    <td>2</td>
    <td>Poisoning attacks  </td>
    <td>The goal of the attacker is to contaminate the machine model generated in the training phase, so that predictions on new data will be modified in the testing phase <p>Targeted: In targeted poisoning attacks, the attacker wants to misclassify specific examples <p>Indiscriminate: The aim here is to cause DoS like effect, which makes the system. </td>
    <td>Integrity</td>
    <td>In a medical dataset where the goal is to predict the dosage of anticoagulant drug Warfarin using demographic information, etc. Researchers introduced malicious samples at 8% poisoning rate, which changed dosage by 75.06% for half of patients[4][Blackbox] <p>In the Tay chatbot, future conversations were tainted because a fraction of the past conversations were used to train the system via feedback[5] [Blackbox] </td>
    <!-- <td>No special privileges required by the attacker. In a closed system like social media platforms, the attacker needs to be a user of the platform.<p> No technological access violation<p>The authorized attacker sends chaff traffic to the endpoint, just like an authorized user would send legitimate traffic to the end point.        </td> -->
  </tr>
  <tr>
    <td>3</td>
    <td>Model Inversion  </td>
    <td>The private features used in machine learning models can be recovered</td>
    <td>Confidentiality; </td>
    <td>Researchers were able to recover private training data used to train the algorithm[6] The authors were able to reconstruct faces, by just the name and access to the model to the point where Mechanical turks could use the photo to identify an individual from aline-up with 95% accuracy.  The authors were also able to extract specific information.  [Whitebox and Blackbox][12] </td>
    <!-- <td>Technologically, it feels like the attacker is not misusing the system  -       No special privileges is required by the attacker to perform the attack.  -       There seems to be no technological access violations – Just like a legitimate user sends in a legitimate image, the attacker sends these specially craftedqueries to recover the private features.     </td> -->
  </tr>
  <tr>
    <td>4</td>
    <td>Membership Inference attack</td>
    <td>The attacker can determine whether a given data record was part of the model’s training dataset or not</td>
    <td>Confidentiality </td>
    <td>Researchers were able to ay to predict a patient’s main procedure(e.g: Surgery the patient went through) based on the attributes (e.g: age,gender, hospital)[7][Blackbox]</td>
    <!-- <td>Technologically, it feels like the attacker is not misusing the system  -       No special privileges is required by the attacker to perform the attack.  -       There seems to be no technological access violations – Just like a legitimate user sends in a legitimate image, the attacker sends these specially crafted queries to infer membership.    </td> -->
  </tr>
  <tr>
    <td>5</td>
    <td>Model stealing </td>
    <td>The attackers recreate the underlying model by legitimately querying the model. The functionality of thenew model is same as that of the underlying model. </td>
    <td>Confidentiality</td>
    <td>Researchers successfully emulated the underlying algorithm from Amazon, BigML. For instance, in the BigML case, researchers were able to recover the model used to predict if someone should have a good/bad credit risk (German Credit Card dataset) using 1,150 queries and within 10 minutes[8]</td>
    <!-- <td>Technologically, it feels like the attacker is not misusing the system  -       No special privileges is required by the attacker to perform the attack.  -       There seems to be no technological access violations – Just like a legitimate user sends in a legitimate image, the attacker sends these specially crafted queries to confuse the system   </td> -->
  </tr>
  <tr>
    <td>6</td>
    <td>Reprogramming deep neural nets</td>
    <td>By means of a specially crafted query from an adversary, Machine learning systems can be reprogrammed to a task that deviates from the creator’s original intent</td>
    <td>Integrity, Availability</td>
    <td>Demonstrated how ImageNet, a system used to classify one of several categories of images was repurposed to count squares. Authors end the paper with a hypothetical scenario: An attacker sends Captcha images to the computer vision classifier in a cloud hosted photos service to solve the image captchas to create spam accounts[9]  </td>
    <!-- <td>Technologically, it feels like the attacker is not misusing the system  -       No special privileges is required by the attacker to perform the attack.  -       There seems to be no technological access violations – Just like a legitimate user sends in a legitimate image, the attacker sends these specially crafted queries to reprogram the system  </td> -->
  </tr>
  <tr>
    <td>7</td>
    <td>Adversarial Example in the Physical domain </td>
    <td>An adversarial example is an input/query from a malicious entity sent with the sole aim of misleading the machine learning system These examples can manifest in the physical domain </td>
    <td>Integrity</td>
    <td>Researchers 3D prints a rifle with custom texture that fools image recognition system into thinking it is a turtle[10] <p>
    Researchers construct sunglasses with a design that can now fool image recognition systems, and no longer recognize the faces correctly[11]</td>
    <!-- <td> </td> -->
  </tr>
  <tr>
    <td>8</td>
    <td>Malicious ML providers who can recover training data</td>
    <td> Malicious ML provider can query the model used by customer and recover customer’s training data</td>
    <td>Confidentiality </td>
    <td>Researchers show how a malicious provider presents a backdoored algorithm, wherein the private training data is recovered. They were able to reconstruct faces and texts, given the model alone.  [12] </td>
    <!-- <td>Technologically, it feels like the provider is misusing the system. Providers don’t snoop around on customer’s data, and this is indirect violation of customer promises. </td> -->
  </tr>
  <tr>
    <td>9</td>
    <td>Attacking the ML Supply Chain[13]</td>
    <td>Owing to large resources (data + computation) required to train algorithms, the current practice is to reuse models trained by large corporations, and modify them slightly for task at hand (e.g: ResNet is a popular image recognition model from Microsoft). These models are curated ina Model Zoo (Caffe hosts popular image recognition models). In this attack,the adversary attacks the models hosted in Caffe, thereby poisoning the well for anyone else. </td>
    <td>Integrity</td>
    <td>Researchers show how it is possible for an attacker to check in malicious code into one of the popular model. An unsuspecting ML developer downloads this model and uses it as part of the image recognition system in their code [14]. The authors show how in Caffe, there exists a model whose SHA1 hash doesNOT match the authors’ digest, indicating tampering. There are 22 models without any SHA1 hash for integrity checks at all. </td>
    <!-- <td>Technologically, the attacker is misusing the system  -      Injecting malicious code into source repository feels like a technological violation.    Questions:  1.      Are Model repositories (typically open source)  failing their duty of care if they don’t check for adversarial manipulation of the models they host?  2.       Can the adversary who tampered with the models be punished under CFAA?  3.       Is the unsuspecting developer now liable for any damages incurred by the customer?  </td> -->
  </tr>
  <tr>
    <td>10</td>
    <td>Backdoor Machine Learning</td>
    <td>Like in the “Attacking the ML Supply Chain”, In this attack scenario,the training process is either fully or partially outsourced to a malicious party who wants to provide the user with a trained model that contains a backdoor. The backdoored model would perform well on most inputs (including inputs that the end user may hold out as a validation set) but cause targeted misclassifications or degrade the accuracy of the model for inputs that satisfy some secret, attacker-chosen property, which we will refer to as the backdoor trigger</td>
    <td>Confidentiality, Integrity</td>
    <td>Researchers created a backdoored U.S. street sign classifier that identifies stop signs as speed limits only when a special sticker is added to the stop sign (backdoor trigger) 20 They are now extending this work to text processing systems, wherein specific words are replaced with the trigger being the speaker’s accent[15]</td>
    <!-- <td>Technologically, it feels like the attacker is misusing the system. This is because backdooring the system feels like violating access controls put forth by the original system designer.  </td> -->
  </tr>
  <tr>
    <td>11</td>
    <td>Exploit software dependencies of ML system</td>
    <td>In this attack, the attacker does NOT manipulate the algorithms. Instead, exploits traditional software vulnerabilities such as buffer overflows. </td>
    <td>Confidentiality, Integrity, Availability, </td>
    <td>An adversary sends in corrupt input to an image recognition system that causes it to misclassify by exploiting a software bug in one of the dependencies.</td>
    <!-- <td>Technologically, it feels like the attacker is misusing the system. This is because exploiting software dependencies equates to violating access controls put forth by the original system designer.  </td> -->
  </tr>
</table>
<p>

## Details on Unintended Failures
<p>

<table   width="100%"  border="1"  style="text-align:center" margin="0 auto" padding="0">
  <tr>
    <th>Scenario #</th>
    <th>Attack Class</th>
    <th>Description</th>
    <th>Type of Compromise</th>
    <th>Scenario</th>
  </tr>
  <tr>
    <td>12</td>
    <td>Reward Hacking</td>
    <td>Reinforcement learning systems act in unintended ways because of discrepancies between the specified reward and the true intended reward.</td>
    <td>Safety of the system </td>
    <td>A huge corpus of gaming examples in AI has been compiled here[1]</td>
  </tr>
  <tr>
    <td>13</td>
    <td>Side Effects</td>
    <td>RL system disrupts the environment as it tries to attain their goal </td>
    <td>Safety of the system </td>
    <td>Scenario, verbatim from the authors in [2]:“Suppose a designer wants an RL agent (for example our cleaning robot) to achieve some goal, like moving a box from one side of a room to the other.Sometimes the most effective way to achieve the goal involves doing something unrelated and destructive to the rest of the environment, like knocking over a vase of water that is in its path. If the agent is given reward only for moving the box, it will probably knock over the vase.”</td>
  </tr>
  <tr>
    <td>14</td>
    <td>Distributional shifts</td>
    <td>The system is tested in one kind of environment, but is unable to adapt to changes in other kinds of environment </td>
    <td>Safety of the system</td>
    <td>Researchers trained two state of the art RL agents, Rainbow DQN and A2C in a simulation to avoid lava. During training, the RL agent was able to avoid lava successfully and reach its goal. During testing, they slightly moved the position of the lava, but the RL agent was not able to avoid [3]</td>
  </tr>
  <tr>
    <td>15</td>
    <td>Natural Adversarial Examples </td>
    <td>The system incorrectly recognizes an input that was found using hard negative mining </td>
    <td>Safety of the system</td>
    <td>Here the authors show how by a simple process of hard negative mining[4], it is possible to confuse the ML system by relaying the example. </td>
  </tr>
  <tr>
    <td>16</td>
    <td>Common Corruption</td>
    <td>The system is not able to handle common corruptions and perturbations such as tilting, zooming, or noisy images. </td>
    <td>Safety of the system</td>
    <td>The authors[5] show how common corruptions such as changes to brightness, contrast, fog or noise added to images, have a significant drop in metrics in image recognition </td>
  </tr>
  <tr>
    <td>17</td>
    <td>Incomplete Testing in Realistic conditions</td>
    <td>The ML system is not tested in realistic conditions that it is meant to operate in </td>
    <td>Safety of the system</td>
    <td>The authors in [25] highlight that that while defenders commonly account for robustness of the ML algorithm, they lose sight of realistic conditions. For instance, they argue that a missing stop sign knocked off in the wind (which is more realistic) than an attacker attempting to perturb the system's inputs.</td>
  </tr>
</table>

## Acknowledgements 

We would like to thank Andrew Marshall, Magnus Nystrom, John Walton, John Lambert, Sharon Xia, Andi Comissoneru, Emre Kiciman, Jugal Parikh, Sharon Gillet, members of Microsoft’s AI and Ethics in Engineering and Research (AETHER) committee’s Security workstream, Amar Ashar, Samuel Klein, Jonathan Zittrain,  members of AI Safety Security Working Group at Berkman Klein for providing helpful feedback. We would also like to thank reviewers from 23 external partners, standards organization, and government organizations for shaping the taxonomy.  

## Bibliography

[1] Li, Guofu, et al. "Security Matters: A Survey on Adversarial Machine
Learning." *arXiv preprint arXiv:1810.07339* (2018).

[2] Chakraborty, Anirban, et al. "Adversarial attacks and defences: A
survey." *arXiv preprint arXiv:1810.00069* (2018).

[3] Ortega, Pedro, and Vishal Maini. "Building safe artificial
intelligence: specification, robustness, and assurance." *DeepMind
Safety Research Blog* (2018).

[4] Amodei, Dario, et al. "Concrete problems in AI safety." *arXiv
preprint arXiv:1606.06565* (2016).

[5] Shankar Siva Kumar, Ram, et al. "Law and Adversarial Machine
Learning." *arXiv preprint arXiv:1810.10731* (2018).

[6] Calo, Ryan, et al. "Is Tricking a Robot Hacking?." University of
Washington School of Law Research Paper 2018-05 (2018).

[7] Paschali, Magdalini, et al. "Generalizability vs. Robustness:
Adversarial Examples for Medical Imaging." arXiv preprint
arXiv:1804.00504 (2018).

[8] Ebrahimi, Javid, Daniel Lowd, and Dejing Dou. "On Adversarial
Examples for Character-Level Neural Machine Translation." arXiv preprint
arXiv:1806.09030 (2018)

[9] Carlini, Nicholas, and David Wagner. "Audio adversarial examples:
Targeted attacks on speech-to-text." arXiv preprint arXiv:1801.01944
(2018).

[10] Jagielski, Matthew, et al. "Manipulating machine learning:
Poisoning attacks and countermeasures for regression learning." *arXiv
preprint arXiv:1804.00308* (2018)

[11] [https://blogs.microsoft.com/blog/2016/03/25/learning-tays-introduction/]

[12] Fredrikson M, Jha S, Ristenpart T. 2015. Model inversion attacks
that exploit confidence information and basic countermeasures

[13] Shokri R, Stronati M, Song C, Shmatikov V. 2017. Membership
inference attacks against machine learning models. In *Proc. of the 2017
IEEE Symp. on Security and Privacy (SP)*, *San Jose, CA, 22–24 May
2017*, pp. 3–18. New York, NY: IEEE.

[14] Tramèr, Florian, et al. "Stealing Machine Learning Models via
Prediction APIs." *USENIX Security Symposium*. 2016.

[15] Elsayed, Gamaleldin F., Ian Goodfellow, and Jascha Sohl-Dickstein.
"Adversarial Reprogramming of Neural Networks." *arXiv preprint
arXiv:1806.11146* (2018).

[16] Athalye, Anish, and Ilya Sutskever. "Synthesizing robust
adversarial examples." *arXiv preprint arXiv:1707.07397*(2017)

[17] Sharif, Mahmood, et al. "Adversarial Generative Nets: Neural
Network Attacks on State-of-the-Art Face Recognition." *arXiv preprint
arXiv:1801.00349* (2017).

[19] Xiao, Qixue, et al. "Security Risks in Deep Learning
Implementations." *arXiv preprint arXiv:1711.11008* (2017).

[20] Gu, Tianyu, Brendan Dolan-Gavitt, and Siddharth Garg. "Badnets:
Identifying vulnerabilities in the machine learning model supply
chain." *arXiv preprint arXiv:1708.06733* (2017)

[21] [https://www.wired.com/story/machine-learning-backdoors/]

[22] [https://docs.google.com/spreadsheets/d/e/2PACX-1vRPiprOaC3HsCf5Tuum8bRfzYUiKLRqJmbOoC-32JorNdfyTiRRsR7Ea5eWtvsWzuxo8bjOxCG84dAg/pubhtml]

[23] Amodei, Dario, et al. "Concrete problems in AI safety." *arXiv
preprint arXiv:1606.06565* (2016).

[24] Leike, Jan, et al. "AI safety gridworlds." *arXiv preprint
arXiv:1711.09883* (2017).

[25] Gilmer, Justin, et al. "Motivating the rules of the game for
adversarial example research." *arXiv preprint arXiv:1807.06732* (2018).

[26] Hendrycks, Dan, and Thomas Dietterich. "Benchmarking neural network
robustness to common corruptions and perturbations." *arXiv preprint
arXiv:1903.12261* (2019).

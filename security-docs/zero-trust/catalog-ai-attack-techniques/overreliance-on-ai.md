---
title: 10. Overreliance on AI (Misuse & Human Factor)
description: Covers the risks of trusting AI output without verification, including fabricated citations and misinformation, and the human oversight needed to mitigate them.
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 10. Overreliance on AI (Misuse & Human Factor)

*Perhaps the best cautionary tale for overreliance is the now-famous legal case of the “fake precedent”.* In mid-2023, lawyers in New York submitted a legal brief that was drafted by ChatGPT – and **the AI had completely fabricated court case citations and quotes**. The lawyers hadn’t checked the AI’s work, and the cited cases didn’t exist. A federal judge sanctioned the attorneys for submitting false information, noting they “abandoned their responsibilities” by trusting an AI without verification.

Another example: a consulting firm submitted a report to their customer that was later found to contain AI generated errors—including fabricated academic citations and misquoted Federal Court judgments. After researchers uncovered references to nonexistent studies and fake quotes, the consulting firm acknowledged using AI in drafting, agreed to repay the final installment, and released a revised version stripping out the bogus sources while maintaining its core findings.

These incidents show that overreliance on AI, especially without checks, can lead to serious professional, legal, and ethical lapses. Attackers could exploit this by deliberately feeding misinformation into AI systems (knowing employees won’t verify it), or by generating convincing spear-phishing messages.

The overarching lesson: **AI is a powerful assistant, but human judgment and verification must remain in loop to avoid costly mistakes**.

## What happens in this scenario
This is a more subtle risk where the “attack” is essentially self-inflicted: users or organizations **place blind trust in AI outputs or use AI inappropriately**, leading to errors or vulnerabilities. While not a cyber-attack in the traditional sense, attackers can *indirectly exploit this* by feeding misinformation to AI systems or taking advantage of an organization’s overconfidence in AI-generated results. In an enterprise setting, overreliance might look like:

1.  **Failing to verify AI-generated content** – e.g., an employee uses an AI to draft an email or a piece of code and sends/deploys it without review, not realizing the AI introduced serious errors or security flaws.

2.  **Using AI for tasks beyond its capability or domain** – e.g., relying on an AI to provide legal or medical advice internally and acting on it verbatim. If the AI hallucinates (makes up information), the company could make decisions based on false information.

3.  **Ignoring better judgement due to AI authority** – employees might defer to what the AI outputs even when it contradicts their training, under the assumption that *“the AI must know better.”* In essence, the scenario is a human/organizational vulnerability: treating AI as infallible or using it without proper checks, which can lead to compliance violations, financial loss, or other damage when the AI is wrong or manipulated.

## Why this technique is effective
AI systems, especially those like LLMs, often produce output that *sounds confident and authoritative*. Psychologically, people tend to trust fluent, detailed answers – a phenomenon magnified when the answers come from an “advanced” AI system.

Attackers can exploit this trust by *using AI to lend credibility to false or malicious content*. For example, a phishing email crafted by an AI can be more persuasive (fewer typos, more contextually relevant) than one by a typical scammer, leading employees to fall for it.

Internally, if an AI summarizer provides subtly biased reports (say, always downplaying certain risks), executives might make poor decisions, believing the AI’s output is unbiased truth. Overreliance is also a prime concern for compliance: there have been cases of professionals (lawyers, doctors) using ChatGPT outputs directly in official work, which later turned out to be erroneous – leading to legal and reputational consequences.

The technique (if one frames it as an attack) succeeds not through a system hack, but through *social engineering at scale*: getting people to trust AI without verification.

## Recommended controls
- **Establish clear policies and training**: Educate staff that AI is a tool to assist, not a source of ground truth. For example, if an AI provides a numeric analysis, policy might require that a human double-checks critical numbers or that a parallel traditional analysis is performed.

- **Verification workflows**: Integrate verification steps especially for high-impact AI outputs. If an AI writes code, have a code review step (just as you would for human-written code). If it produces a business report, have a human analyst validate key facts and figures. Essentially, *never let a significant action or decision hinge on a single unverified AI output*.

- **Pilot and test before deploying AI decisions**: Before giving any AI decision-making power, test it thoroughly and compare its decisions to human decisions over a period of time. This helps identify systematic errors or biases. For example, if using an AI to approve financial transactions, run it in shadow mode first to see how its decisions stack up to a human approver’s decisions.

- **Transparency in AI outputs**: Whenever possible, have the AI provide *sources or rationale* for its outputs. This helps users judge credibility. In enterprise knowledge management, this could mean using **retrieval-augmented generation** (the AI cites which internal document or database entry supports its answer). Knowing the source of an AI’s answer (e.g., a specific policy document) can help users trust but verify the information.

- **Limit critical use-cases**: For now, avoid using LLMs in fully autonomous mode for mission-critical decisions that they are not proven to handle. Use simpler, more predictable AI models or rule-based systems for decisions that require high reliability, and reserve LLMs for suggestions or insights rather than final calls.

## Technologies to consider
- **Human-in-the-loop systems**: Implement approval workflows in tools like **Power Automate** or other business process management software so that AI recommendations pass through human decision-makers for critical processes (e.g., compliance checks, financial approvals).

- **Verification tools**: Use specialized validation AI or software to cross-verify AI outputs. For instance, if an LLM provides a numeric summary, a simpler script or model could re-calculate key figures from source data to ensure consistency. If an AI makes a classification (like a risk score), have a rule-based system that flags if the recommendation falls outside certain bounds before actioning it.

- **Monitoring and feedback loops**: Deploy feedback mechanisms (such as Microsoft’s **Microsoft Foundry Control Plane** or custom feedback forms) for users to flag AI outputs that seem incorrect or risky. This feedback should be reviewed and used to retrain or adjust the AI.

- **Robust documentation and model cards**: Ensure that each AI system comes with documentation of its intended use, limitations, and accuracy. Technologies like **Azure Machine Learning’s model interpretability and error analysis tools** can help identify where the model is likely to be confident vs. uncertain. Surfacing an AI’s confidence level or uncertainty to the user (e.g., “The AI is 60% sure about this answer”) can prevent blind trust.

## OWASP Top 10 mapping
[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)

This scenario maps to **LLM09: Misinformation**, where the model generates confident but incorrect or misleading outputs, and users place undue trust in those responses – leading to flawed decisions, operational errors, or unsafe actions driven by hallucinated or unreliable content.

## MITRE ATLAS mapping
This scenario maps broadly to MITRE ATLAS behaviors around human influence, adversarial misinformation, and misuse of model outputs. MITRE ATLAS does not currently define a dedicated “overreliance on AI” technique, so these are closest-fit mappings to integrity erosion, indirect prompt injection, and external harm when user trust in AI output becomes the exploited path.

**[MITRE ATLAS Techniques](https://atlas.mitre.org/techniques) (Attack):**
The attack primarily reflects human overreliance and influence: users treat AI output as authoritative, allowing incorrect, manipulated, or hallucinated content to drive decisions or actions.
* AML.T0031 Erode AI Model Integrity
* AML.T0048 External Harms
* AML.T0051.001 LLM Prompt Injection: Indirect (when the content the human reads is itself poisoned)

**[MITRE ATLAS Mitigations](https://atlas.mitre.org/mitigations) (Defense):**
Prioritize user education, decision gates, provenance, uncertainty signaling, interface safeguards, and monitoring for blind-obedience patterns.
* AML.M0018 User Training
* AML.M0020 Generative AI Guardrails
* AML.M0021 Generative AI Guidelines
* AML.M0024 AI Telemetry Logging

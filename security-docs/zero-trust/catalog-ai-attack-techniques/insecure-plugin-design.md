---
title: 8. Insecure Plugin Design (Tools/Plugins)
description: Describes how poorly designed AI plugins with excessive permissions can be exploited to perform unauthorized actions without user confirmation.
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 8. Insecure plugin design (tools and plugins)

In 2023, researchers discovered **vulnerabilities in some early ChatGPT plugins** that bad actors could exploit without user intervention. In one case, a malicious website leveraged ChatGPT’s **“Chat With Code” plugin (which connects to GitHub)** along with a web-browsing plugin. By simply having a user’s AI assistant visit the site, hidden prompts caused the AI to invoke the GitHub plugin and **leak private repository data and even change repository permissions**. The plugins allowed these actions without verifying with the user, essentially acting with excessive permissions. This vulnerability demonstrated how a poorly designed plugin (with OAuth but insufficient confirmation steps) could be misused to perform privileged operations.

This incident, along with others investigated by security firms, led to stronger guidelines for plugin developers. For example, OpenAI now requires certain plugins to enforce user confirmation for high-risk actions. Nonetheless, the episode is a stark reminder that extending AI with powerful plugins is like installing third-party apps – without proper vetting and constraints, they can become the **significant attack surface of your AI ecosystem**.

## What happens in this scenario
In this scenario, an AI *plugin or extension* serves as the weak link that bad actors exploit. **Insecure plugin design** means a plugin (or integrated tool) used by the AI has vulnerable code or overly broad permissions, which bad actors can exploit to perform unintended actions. For example:

1.  Consider a CRM assistant AI with a scheduling plugin that can create calendar events through API calls. If that plugin doesn't properly authenticate requests or limit scope, a bad actor could craft a prompt that causes the AI to create unauthorized meetings or send invites company-wide.

1.  In more severe cases, a poorly designed plugin could enable remote code execution (RCE): For example, an AI with a "server admin" plugin might execute any OS command it's told, without confirming with the user, letting a bad actor's prompt actually run shutdown on a server.

> Essentially, the AI's plugin becomes an open door. The scenario often ties back to prompt injection: the bad actor finds a way to get the AI to call the vulnerable plugin with malicious parameters. If the plugin isn't built with security in mind (for example, no input sanitization, no permission checks), the bad actor's wishes are carried out by the system.

## Why this technique is effective
Many third parties develop plugins or developers quickly roll out plugins to extend AI functionality. These plugins might not undergo rigorous security testing. Bad actors prey on plugins that:

- **Lack strict permission scopes**: For example, a file-management plugin that can access an entire file system instead of a specific folder can be misused to read or write sensitive files.

- **Trust the AI’s input blindly**: If a plugin executes whatever command or URL the AI passes it, then a prompt injection on the AI can directly become a system command or API call. This is akin to the classic “confused deputy” problem, where the AI (deputy) can be tricked into misusing its authority on behalf of the attacker.

- **Have known vulnerabilities**: like any software, plugins can have bugs (buffer overflows, injection flaws) that an attacker might exploit via crafted plugin inputs. This technique is effective because the **AI extends trust to the plugin** (it assumes the plugin will do what it’s supposed to), and often the system extends trust to the plugin’s actions (the plugin might be allowed to pull data or perform tasks with significant impact). If both the AI and the host system aren’t validating what the plugin is asked to do, a malicious prompt can cause a high-privilege action with minimal oversight. The multiplication of plugins increases the attack surface – each plugin could introduce new vulnerabilities, and compromising any one can compromise the whole AI workflow.

## Recommended controls
- **Plugin vetting and sandboxing**: Thoroughly review any plugin’s code and security before enabling it, especially if it can access sensitive data or systems. Run plugins in **sandboxed environments** with minimal privileges. For example, if a plugin needs to manipulate calendar events, give it an account with only calendar access, not broader system rights.

- **Principle of least privilege**: Limit what plugins can do. If an AI plugin should only read HR data, enforce that it cannot write or delete data. Use API gateways or intermediate services that verify the plugin’s actions; for instance, a plugin request to “delete database” should be blocked or require separate approval.

- **Mandatory user confirmation**: Design plugins (or the AI’s use of them) such that certain sensitive actions require explicit human confirmation. OpenAI has issued guidelines that any plugin performing high-impact actions must seek user approval – implement similar checks in your enterprise AI. For example, an AI-generated email draft might be automatic, but sending it should need a click from a human.

- **Continuous security testing**: Include plugins in regular pen-testing and code audits. Employ static and dynamic analysis security tools on plugin code. Additionally, simulate prompt attacks that target plugins – e.g., can a fake command be injected that causes the plugin to misbehave? This helps catch issues early.

- **Monitor plugin activity**: Keep logs of all plugin invocations and their actions. An unusual spike (like a plugin reading an abnormal number of files or making external calls it normally wouldn’t) should trigger alerts or auto-disable that plugin until reviewed.

## Technologies to consider
- **OAuth and identity for plugins**: Use standardized auth for plugins (e.g., OAuth with scopes). Microsoft’s **Entra ID** can help ensure plugins operate under service principals with limited rights. Enforce short-lived tokens so that compromised plugins can’t be misused for long.

- **Containerization and API wrappers**: Deploy each plugin in a container with network and filesystem restrictions. For example, run plugins in an **Azure Function** or **Kubernetes** with AppArmor/SELinux profiles that prevent illegitimate actions (no outbound network calls unless necessary, no file system writes, etc.).

- **Security testing tools**: Use fuzzing and scanning tools on plugin code (e.g., **OWASP ZAP** for web plugins, static code analyzers for any scripting). Microsoft’s **Security Code Analysis** or third-party tools can be integrated into the CI/CD pipeline of plugin development.

- **Plugin management**: Maintain an approved list of allowed plugins. Disable or remove plugins that are not needed. Utilize enterprise plugin management settings (for example, if using Microsoft 365 Copilot or similar, turn off connectors that you don’t plan to use to reduce risk).

## OWASP Top 10 mapping
[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)

This scenario maps to **LLM03: Supply Chain**, where poorly vetted or insecure plugins introduce attack surfaces through untrusted dependencies, unsafe tool APIs, or compromised extension ecosystems. It also aligns with **LLM06: Excessive Agency**, since overly‑permissive or insufficiently governed plugins allow the model to perform unintended or harmful actions through delegated capabilities.

## MITRE ATLAS mapping
This scenario maps broadly to MITRE ATLAS behaviors around component misuse, supply-chain compromise, API abuse, and tool-mediated data exposure.

**[MITRE ATLAS Techniques](https://atlas.mitre.org/techniques) (Attack):**
The attack primarily reflects insecure component or tool abuse: a plugin becomes the privileged path through which malicious prompts or unsafe inputs cause unauthorized actions or data exposure.
* AML.T0110 AI Agent Tool Poisoning
* AML.T0010.005 AI Supply Chain Compromise: AI Agent Tool
* AML.T0053 AI Agent Tool Invocation
* AML.T0055 Unsecured Credentials

**[MITRE ATLAS Mitigations](https://atlas.mitre.org/mitigations) (Defense):**
Prioritize plugin vetting, signed manifests, scope limits, sandboxing, lifecycle governance, schema enforcement, and plugin activity monitoring.
* AML.M0013 Code Signing
* AML.M0014 Verify AI Artifacts
* AML.M0019 Control Access to AI Models & Data in Production
* AML.M0020 Generative AI Guardrails
* AML.M0024 AI Telemetry Logging

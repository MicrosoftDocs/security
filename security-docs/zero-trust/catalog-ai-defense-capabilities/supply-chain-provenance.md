---
title: 2. Supply-chain and Provenance
description: Learn how to protect AI models, datasets, plugins, and agents from supply-chain compromise using provenance records, integrity verification, and trusted registries.
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 2. Supply-chain and Provenance

## What this group defends against

This group addresses trust placed in upstream components — pre-trained models, datasets, open-source libraries, plugins, agent tools, and MCP directories. It counters rug-pull tool swaps, open-source Supply-chain compromise, poisoned models on public hubs, tampered training data, and malicious or renamed tools introduced after initial approval.

## Core capabilities

Supply-chain security establishes confidence that every model, dataset, library, plugin, tool, and agent component is the version the organization approved and has not been substituted or modified. That confidence requires provenance from original source through deployment, cryptographic verification at trust boundaries, controlled registries and promotion workflows, and the ability to trace and reverse changes. Third-party assets should be evaluated in isolation before adoption and monitored after release because a previously trusted dependency can change over time.

- **Record provenance:** generate SBOM and AI-BOM records, document training and transformation lineage, and retain ownership, source, license, and approval metadata.

- **Verify integrity:** sign artifacts, validate checksums and signatures before loading, pin approved versions, and use trusted registries with controlled promotion.

- **Test and recover:** scan dependencies and model files, restrict unsafe deserialization and library loading, sandbox third-party evaluations, and preserve clean rollback checkpoints.

## Which technologies do we use?

Supply-chain and provenance controls require technology across the full path from source to production. The tools below provide trusted registries, package and dependency security, data cataloging and lineage, reproducible MLOps, and cryptographic verification so teams can approve components, detect unauthorized change, and return to a known-good state.

- **Azure Machine Learning registries and model registry** — managed repositories for versioned models, environments, components, and data assets. Use them to promote approved assets across development, test, and production; retain lineage to training jobs and source artifacts; isolate environments; and roll back to known-good versions.

- **Azure Artifacts** — a package-management service in Azure DevOps for hosting and controlling feeds such as NuGet, npm, Maven, Python, and Universal Packages. Use private feeds, upstream-source controls, permissions, retention, and immutable version references to reduce substitution and unapproved dependency risks.

- **GitHub Dependabot and code-scanning services** — dependency-security capabilities that identify known vulnerable or outdated packages and propose controlled updates. Pair alerts and pull requests with secret scanning, code scanning, branch protection, required reviews, and signed releases so dependency changes are visible and approved before deployment.

- **Microsoft Purview and Collibra** — enterprise data-governance platforms used to catalog data, record business and technical lineage, assign ownership, classify sensitive content, and document approved sources. These capabilities help prove which datasets trained or grounded a model and identify unauthorized source changes.

- **Azure Machine Learning MLOps** — lifecycle automation for reproducible training, evaluation, registration, approval, deployment, and monitoring. Use versioned pipelines and environments, lineage, gated promotion, notifications, drift monitoring, and CI/CD integration to make model changes repeatable and auditable.

- **Artifact signing, checksums, and AI-BOM** — control practices rather than one product. Cryptographically sign code and model packages, verify hashes before loading, pin exact versions, record every component and source, and reject artifacts whose signature, provenance, or approved registry does not match policy.

## Framework mapping

**[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)**: Maps to LLM03 Supply Chain and LLM04 Data and Model Poisoning by controlling the integrity of models, datasets, libraries, plugins, and agent tools before they are trusted. Version pinning, trusted registries, artifact signing, training-data change management, and provenance records reduce poisoned components, malicious updates, and rug-pull tool swaps.

**[MITRE ATLAS](https://atlas.mitre.org/mitigations)**: Maps to AML.M0013 Code Signing, AML.M0014 Verify AI Artifacts, AML.M0016 Vulnerability Scanning, AML.M0023 AI Bill of Materials, and AML.M0025 Maintain AI Dataset Provenance. These current mitigations support component inventories, signature and provenance verification, dependency and model-file scanning, dataset lineage, and rollback to known-good artifacts.

**[NIST AI RMF 1.0 and NIST AI 600-1](https://www.nist.gov/itl/ai-risk-management-framework)**: Supports **MAP** and **MANAGE** by identifying third-party dependencies, documenting training-data and model-artifact sources, evaluating supplier risk, and maintaining change control and assurance evidence across the AI value chain.


# RAG Service

**AI-Augmented SOC - Retrieval-Augmented Generation**

> Ground LLM responses in verified security knowledge to reduce hallucinations by 30-40%.

---

## Overview

The RAG (Retrieval-Augmented Generation) Service provides semantic search over security knowledge bases, enabling LLMs to cite verified sources instead of hallucinating information.

**Knowledge Sources:**
- **MITRE ATT&CK:** 3000+ attack techniques and tactics
- **CVE Database:** Critical vulnerabilities (CVSS >= 9.0)
- **Incident History:** Resolved TheHive cases
- **Security Runbooks:** Response playbooks and procedures

**Performance Targets:**
- **Faithfulness (RAGAS):** >0.90 (RAG accuracy)
- **Retrieval Precision:** >0.85 (relevant results)
- **Hallucination Reduction:** 30-40% vs non-RAG baseline
- **Latency:** <500ms per query

---

## Architecture

```
+--------------+      +--------------+      +--------------+
| Alert Triage |----->| RAG Service  |----->|  ChromaDB    |
|   Service    |Query | (Embeddings) |Search| (Vector DB)  |
+--------------+      +--------------+      +-------+------+
                                                    |
                                             +------+-------+
                                             | Knowledge    |
                                             | - MITRE      |
                                             | - CVE
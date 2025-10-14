# Procurement-Agentic-AI
This repository explores how agentic AI systems can transform procurement by combining natural language understanding, structured data extraction, and vector search. The goal is to automate repetitive tasks, monitor SLA Rules and any other regulation such as compliance or Procurement Policies.

> **„Die Zukunft des Einkaufs: Agentische KI, die Anfragen beantwortet, SLAs überwacht und automatisch eskaliert.“**

---

## 🚀 Überblick

Dieses Projekt modernisiert Ihre Beschaffungsprozesse mit einem **modularen KI-Stack**.  
Ein eingebetteter Chat beantwortet Anfragen blitzschnell, überwacht SLA-Regeln in Echtzeit und eskaliert Verstöße automatisiert an die richtigen Rollen.
- [🚀 Überblick](#-überblick)
- [🎯 Ziele](#-ziele)
- [🛠️ Tech Stack](#️-tech-stack)
- [🏗️ Architektur](#-architektur)
- [🔄 End-to-End Workflow](#-end-to-end-workflow)
- [💻 Installation & Lokales Deployment](#-installation--lokales-deployment)
- [⚙️ Konfiguration](#️-konfiguration)
- [🔒 Sicherheit & Governance](#-sicherheit--governance)
- [🚀 Performance & Observability](#-performance--observability)
- [🛣️ Roadmap](#️-roadmap)
- [💼 Einsatzszenarien](#-einsatzszenarien)
- [⚡ Quickstart](#-quickstart)
- [📊 Executive Insights](#-executive-insights)
- [📑 Lizenz & Beitrag](#-lizenz--beitrag)
- [🧭 Nächste Schritte](#-nächste-schritte)

---

## 🎯 Ziele

- ⚡ **Automatisierte Antworten** auf Standardanfragen  
- ⏱️ **Echtzeit-SLA-Monitoring** mit automatischen Erinnerungen  
- 🚨 **Eskalations-Logik** an Manager oder definierte Teams  
- 🔍 **Semantische Suche & Kontext-Engineering** via Vector DB & Light-Graph-RAG  
- 🔐 **Sicherheit & Compliance** durch Guardrails und API-Security  
- 📈 **Messbare Performance-Optimierung** mit Deepeval  
- 🔄 **Zukunftsfähigkeit** via MCP-Integration in der nächsten Pilotphase

---

[Hier wird ein GIF oder vllt doch ein Video eingesetzt - zur Veranschaulichungszweck (Veröffentlichung bis heute spät abend)]

---

## 🛠️ Tech Stack

- **Orchestrierung:** n8n  
- **Containerisierung:** Docker (n8n, Ollama lokal, PostgreSQL, Qdrant, ngrok)  
- **LLMs:**  
  - Lokal: Ollama  
  - Extern: OpenRouter  
- **OCR & Bildanalyse:** Mistral API  
- **Datenhaltung:**  
  - Relational: PostgreSQL  
  - Semantisch: Qdrant (Vector-Store)  
- **Sicherheit:** Guardrails, API-Security  
- **Performance-Monitoring:** Deepeval  
- **Tunnel & Webhooks:** ngrok  

---

## 🏗️ Architektur

1. **Intake Layer**  
   - Embedded Chat, E-Mail, Dokument/Upload, API  
2. **Perzeption**  
   - Mistral OCR & Bildanalyse → Rohtext  
3. **Extraktion & Schema-Füllung**  
   - JSON-Agent füllt `items`, `DeliveryTo_Team`, `Due_Date` etc.  
4. **Kontext-Engineering**  
   - Embeddings aus Kernfeldern → Qdrant Payload  
   - Light-Graph RAG verbindet Teams, SLAs & History  
5. **Reasoning & Antwort**  
   - Ollama lokal oder OpenRouter extern  
   - Guardrails-Checks vor Ausgabe  
6. **SLA-Monitoring & Eskalation**  
   - Regelprüfung (Budget, Abholzeiten…)  
   - Erinnerungen an Mitarbeitende  
   - Eskalation an Manager/Rollen  
7. **Audit & Log**  
   - Postgres für Transaktionen & Logs  
8. **Performance-Tuning**  
   - Deepeval identifiziert Nodes > 1 s → Optimierung  

---

## 🔄 End-to-End Workflow

```mermaid
flowchart LR
  A[User Anfrage] --> B[OCR/Parsing]
  B --> C[Schema-Agent → JSON]
  C --> D[Embedding & Qdrant Insert]
  D --> E[Light-Graph RAG]
  E --> F[LLM-Router (Ollama/OpenRouter)]
  F --> G[Guardrails Check]
  G --> H[Antwort an User]
  C --> I[SLA Checker]
  I -->|OK| H
  I -->|Alarm| J[Reminder/Notify Staff]
  I -->|Verstoß| K[Eskalation Manager]
  H & J & K --> L[Audit-Log (Postgres)]
  L --> M[Deepeval Analyse]

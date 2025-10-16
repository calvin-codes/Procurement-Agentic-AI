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
- [⚙️ Konfiguration](#️-konfiguration)
- [🔒 Sicherheit & Governance](#-sicherheit--governance)
- [🚀 Performance & Observability](#-performance--observability)
- [🛣️ Roadmap](#️-roadmap)
- [💼 Einsatzszenarien](#-einsatzszenarien)
- [📊 Executive Insights](#-executive-insights)
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

[![Demo: Anlegen einer Bestellung sowie abfragen der Details](https://vimeo.com/1127977900?fl=ip&fe=ec)]
(thumbnail.jpeg)


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


  
## ⚙️ Konfiguration

- **Embedding-Strategie:** Kombiniere Produkt, Marke, Menge, Team und Datum zu kompakten, semantisch aussagekräftigen Texten.
- **RAG-Kontext:** Light-Graph-Knoten für Teams, Produkte, SLAs und Lieferanten; gezielte Verknüpfungen für präzises Retrieval.
- **Kontext-Expansion:** Nur bei Unklarheit oder fehlenden Daten, kostenbewusst und kontrolliert.
- **Guardrail-Policies:** Output-Filter, API-Limits und Rollen-Gates vor kritischen Aktionen.

---

## 🔒 Sicherheit & Governance

- **Guardrails:** Richtlinien für Inhalte, Aktionen und sichere Tool-Ausführung.
- **API-Security:** Tokens, Rate-Limits und IP-Filter, auch für Tunnel (z. B. ngrok).
- **Auditability:** Vollständige Protokolle für alle AI-Entscheidungen und Eskalationsereignisse.
- **Compliance:** Budget- und Datenschutz-Checks eingebettet in die Workflows.

---

## 🚀 Performance & Observability

- **Deepeval:** Identifiziert langsame Nodes (Threshold > 1 s) und priorisiert Optimierungen.
- **KPI-Dashboard:** Antwortzeit, SLA-Reminder-Quote, Eskalationsrate, First-Contact-Resolution.

---

## 🛣️ Roadmap

| Phase   | Fokus                                                     |
|---------|-----------------------------------------------------------|
| Pilot   | Lokales Hosting, Chat, SLA-Monitoring, Eskalation         |
| Phase 2 | Deepeval-Tuning, Retrieval-Optimierung                    |
| Phase 3 | MCP-Integration (Agenten-Interoperabilität)               |
| Phase 4 | Cloud-Rollout, ERP-Anbindung, erweiterte Compliance       |

---

## 💼 Einsatzszenarien

- **Anfragen:** Lieferstatus, Budgetfreigabe, Ersatzartikel.
- **Dokumenteingang:** OCR aus Rechnung oder Bestellschein mit automatischer Zuordnung.
- **Proaktive SLAs:** Erinnerungen vor Fristablauf; Eskalation bei Verstößen.
- **Manager-View:** Übersicht, Risiken und klare Handlungsempfehlungen.

---

## 📊 Executive Insights

- **Effizienzgewinn:** Weniger manuelle Tickets.
- **Konsistenz:** Kontinuierliche SLA-Überwachung in Echtzeit.
- **Sicherheit:** Lokales Hosting und Guardrails minimieren Risiken.
- **Skalierbar:** Modularer Aufbau für zukünftige Expansion.

---

## 🧭 Nächste Schritte

- **Gif/Video Präsentation:** Einfügen eines demos des Pilot-Launch in Readme Github
- **Diagramm-Support:** Tool-Stack mit Logos sowie eine prägnante Workflow-Übersicht.
- **Pilot-Launch:** Feedback sammeln und Metriken beobachten.
- **MCP-Integration:** Interagentische Erweiterung im nächsten Pilot-Stadium.
- **Cloud-Skalierung:** ERP/Procurement-System Anbindung und Governance ausbauen.

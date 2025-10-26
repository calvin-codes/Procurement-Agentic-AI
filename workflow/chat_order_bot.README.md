# n8n Workflows: Bestellverarbeitung & Q&A

Dieses Repo enthält einen **Main Workflow** und **2 Subworkflows**.  
Alle müssen zuerst in **n8n** importiert werden.

## Überblick
- **Workflow**:  
Der Hauptworkflow nimmt Bestellungen per Chat-Trigger im Fließtext entgegen, strukturiert sie und schreibt die Daten in PostgreSQL, Qdrant und Google Sheets, wobei er auch Fragen über status beantworten kann.
  - Startet mit einem Chat-Trigger  
  - Nimmt Bestellungen als Fließtext entgegen  
  - Wandelt sie in strukturierte Daten um  
  - Schreibt Ergebnisse in:
    - **PostgreSQL**
    - **Qdrant (Vector Store)**
    - **Google Sheets**  
  - Kann zusätzlich Fragen beantworten  

## Voraussetzungen
- **PostgreSQL**-Datenbank  
- **Qdrant**-Instanz  
- **Google Sheets**-Zugang  
- **Mistral Credentials** (falls nicht durch eigene ersetzt)  

## Nutzung
1. Alle Workflows in n8n importieren  
2. Verbindungen zu PostgreSQL, Qdrant und Google Sheets einrichten  
3. Mistral-Credentials hinterlegen  
4. Main Workflow starten und testen  

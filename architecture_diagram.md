# System Architecture Diagram

The following diagram illustrates the high-level architecture of the system:

```mermaid
graph TD

%% Define components
A[Ad Server Emails] -->|1. Data Extraction| B[Google Cloud Functions]
B -->|2. Load Data| C[Google BigQuery]

D[Internal Pixel Data] -->|3. Scheduled Import| C

C -->|4. Data Comparison Queries| E[Discrepancy Detection]

E -->|5. Store Reports| F[BigQuery Partitioned Tables]
F -->|6. Visualization| G[Google Data Studio Dashboard]

G -->|7. User Review & Notations| H["Notation Interface - Google Sheets or Web App"]
H -->|8. Save Notations| F

F -->|9. Train ML Model| I[BigQuery ML]
I -->|10. Predict Notations| E

%% Define interactions
subgraph Data_Ingestion
    A --> B
    D --> C
end

subgraph Data_Processing_And_Storage
    C --> E
    E --> F
    F --> I
end

subgraph User_Interaction
    G --> H
    H --> F
end

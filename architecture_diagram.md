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
subgraph Data Ingestion
    A
    B
    D
end

subgraph Data Processing & Storage
    C
    E
    F
    I
end

subgraph User Interaction
    G
    H
end



### Description of Components and Data Flow

1. **Ad Server Emails** (`A`): The system begins by receiving emails containing Ad server data.

2. **Google Cloud Functions** (`B`): Cloud Functions are triggered to extract data from these emails and preprocess it as necessary.

3. **Internal Pixel Data** (`D`): This data is imported into BigQuery on a scheduled basis, ensuring that the system has up-to-date internal tracking information.

4. **Google BigQuery** (`C`): Serves as the central data warehouse where both Ad server and internal pixel data are stored.

5. **Data Comparison Queries** (`E`): BigQuery executes SQL queries to compare the Ad server data with internal pixel data, detecting any discrepancies.

6. **Discrepancy Reports Storage** (`F`): The results of the data comparison are stored in partitioned tables within BigQuery for efficient access and historical tracking.

7. **Google Data Studio Dashboard** (`G`): Visualizes the discrepancy reports, providing users with interactive dashboards for analysis.

8. **Notation Interface** (`H`): Users can review the reports and add notations using either a Google Sheets interface or a custom web application. These notations are then saved back into the BigQuery tables.

9. **BigQuery ML** (`I`): Utilizes historical data, including past discrepancies and user notations, to train machine learning models that can predict future notations, thereby enhancing the system's automation capabilities.

10. **Feedback Loop**: The predictions made by the ML models are fed back into the discrepancy detection process, and user interactions with these predictions are used to further train and refine the models.

---

**Notes:**

- **Subgraphs**: The diagram groups components into three subgraphs to illustrate the different layers of the system:
  - **Data Ingestion**: Handles the collection and preprocessing of raw data.
  - **Data Processing & Storage**: Manages data comparison, storage of results, and machine learning operations.
  - **User Interaction**: Encompasses the visualization tools and interfaces through which users interact with the system.

- **Numbered Steps**: Each arrow in the diagram is labeled with a step number corresponding to the description above, providing a clear flow of data and processes.

---

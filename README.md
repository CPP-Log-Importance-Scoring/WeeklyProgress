## **CPP Meeting 1 - 03/03/26**

### Discussion:

- The mentor shared the complete project workflow via email and explained the overall system objective.
- The end-to-end pipeline, including ingestion, processing, scoring, correlation, storage, and visualization stages, was introduced.
- The team was instructed to thoroughly review the problem statement to understand the expected project scope.
- Key technologies and core concepts required for implementation were highlighted for self-study.
- Reference materials and learning resources were provided to build foundational knowledge.
- Team members were expected to prepare for deeper technical discussions in the next meeting.

### Contribution:

- Everyone went through the documents and the links provided by the mentor.

---

## **CPP Meeting 2: 10/03/26**

### Discussion:

- Discussed schema design for CPP Log Importance Scoring and Cross Signal Correlation project
- Identified key factors to include in the schema (event type, frequency, severity, etc.)
- Understood how these factors influence the scoring logic
- Explored structure for storing logs and embeddings

### Contribution:

- Everyone participated in schema design discussion and came up with a unified schema
- Submitted the sample dataset

---

## **CPP Meeting 3: 17/03/26**

### Discussion:

- Multi-layered architecture: Designed pipeline from log ingestion to visualization.
- Scoring logic: Created importance_score using event weight, frequency, and correlation.
- Event weighting: Used rule-based method with log level as modifier.
- Incident correlation: Grouped related logs into clusters based on time and component.

### Contribution:

- Based on mentors feedback schema was refactored and some elements were removed
- Members researched on how to calculate weights for each log

---

## **CPP Meeting 4: 25/03/26**

### Discussion:

- Presented system design and scoring logic to mentor
- Received feedback on architecture and approach
- Discussed improvements in scoring logic
- Advised to refine dataset and enhance data quality
- Suggested creating and maintaining a GitHub repository for collaboration

### Contribution:

- Everyone did their research and then discussed among the team and created a unified system design document

## **CPP Meeting 5: 31/03/26**

### Discussion:

- Worked on the system design document
- Researched AI/ML models for log importance scoring
- Identified Isolation Forest as a potential approach
- Explored its working and applicability to the system

### Contribution:

- Ujwal: Worked on the system design, researched various AI/ML models suitable for log importance scoring, and identified Isolation Forest as a potential approach. Further explored its working and suitability for integration into the system
- Sumukha: Worked on system design, researched on topics such as similarity search and methods to optimise existing design
- Vishon: Reviewed the earlier sample dataset to understand its structure and format. Generated a new syslog-format dataset which contains ~10,000 logs covering network, security, system logs etc
- Shreeraksha M: Implemented feature computation by mapping log levels and event types to numerical scores, and built event weight calculation using configurable weights. Also explored how template IDs are generated and how they help group similar logs for further analysis.
- Sharva: Implemented the core parsing pipeline which includes the LogRecord schema with all stage wise fields, the syslog line parser with per service event extraction rules, and the template extraction module that normalises log messages and assigns template IDs to group similar logs.

---

## **CPP Meeting 6: 07/04/26**

### Discussion:

- The meeting was cancelled due to internal examinations.

### Contribution:

- No contributions for this week due to internal examinations.

---

## **CPP Meeting 7: 15/04/26**

### Discussion:

- Presented system design document and ML approach
- Presented rule-based scoring system
- Suggested increasing template diversity or moving towards dynamic template assignment

### Contribution:

- Shreeraksha M: Completed implementation of event weight calculation using configurable weights and developed the importance scoring module by combining event weight, frequency, and correlation signals.

- Vishon Dsouza: Enhanced dataset (logs2.txt) with multiple log types and created logs3.txt with burst patterns and anomaly scenarios. Took team feedback to sort logs in ascending timestamp order.

- Sharva: Validated the scoring pipeline by examining calculated scores across parsed log records, verifying that severity scores, event type scores, and event weights are correctly assigned across different log types.

- Ujwal Hegde: Implemented the Isolation Forest–based anomaly detection pipeline and engineered features such as frequency, deviation, and rarity for model input. Analyzed model behavior in depth, including feature influence, path-based isolation, and anomaly scoring.

- Sumukha: Enhanced system design and added new layers to address challenges highlighted by the mentor and team. Also introduced graph-based computation for correlation and improved clarity on dynamic template creation and management.

---

## **CPP Meeting 8: 21/04/26**

### Discussion:

- Focused primarily on improving the rule-based scoring system based on feedback from the previous presentation
- Presented dynamic template extraction approach to enhance log grouping and improve scoring and correlation
- Mentor instructed the team to prepare a presentation (PPT) for the next checkpoint covering problem understanding, approach, and system design
- Suggested exploring AI/ML models to cross check and validate the results of the rule-based system as part of further improvement

### Contribution:

- Sharva: Validated the dataset by examining log consistency and correctness across different scenarios, and tuned event weights to improve the accuracy and balance of the scoring mechanism across various log types and patterns

- Sumukha: Could not contribute this week due to organizing a hackathon

- Ujwal Hegde: Improved the ML pipeline by refining the Isolation Forest model, enhancing feature engineering with frequency, deviation, rarity, and change, and making the system more robust through adaptive thresholding and generalized log handling

- Shreeraksha M: Improved log importance scoring and cross-signal correlation by enhancing template-based grouping using dynamic template extraction and refining scoring weights to better reflect real-world incident severity

- Vishon: Improved dataset based on prior feedback, simulating multi-host infrastructure with realistic noise and diverse events. Includes explicit attack chains and failure cascades for log correlation and anomaly detection

---

## **CPP Meeting 9: 28/04/26**

### Discussion:

- Presented the first checkpoint PPT draft to the mentor and incorporated the feedback received to revise and improve the presentation.
- Briefed the mentor on the work distribution across the team for the ML implementation phase.
- Discussed the limitations and challenges encountered during the rule-based implementation, and elaborated on how the proposed ML-based approach addresses those shortcomings and offers a more robust solution.


### Contribution:

- Sumukha: Initialized the ML repository structure and configured persistent volumes for the database container. Conducted research into established methods for implementing the sequence analysis and correlation engine layers of the pipeline.

- Ujwal: Strengthened the ML pipeline by refining feature engineering and optimizing the Isolation Forest–based anomaly detection, and contributed to the design of the importance scoring layer by combining ML outputs with correlation and novelty signals.

- Sharva: Compared the pipeline's log scoring output with LLM output to evaluate alignment and identify gaps in critical event detection.

- Vishon: Configured a Docker Compose logging stack with PostgreSQL, Elasticsearch, Grafana, and Kibana. Updated service setup, secured credentials using .env, and added .gitignore. Successfully tested all containers locally and verified integration.

- Shreeraksha M: Validated and tuned the rule-based scoring system by experimenting with multiple datasets and refining weight configurations for improved log scoring. Initiated the ML anomaly detection pipeline by implementing a z-score based baseline and structuring the anomaly detection module in preparation for Isolation Forest integration and hybrid scoring.

## **CPP Meeting 10: 05/05/26**

### Discussion:

- Presented the project PPT covering the problem statement, overall approach, architecture design, current progress, and planned ML-based workflow.
- Discussed the implementation and validation status of the rule-based scoring system and demonstrated the current pipeline flow.
- The mentor reviewed the presentation and asked questions regarding the scoring methodology, limitations of the rule-based approach, and the transition toward ML-based anomaly detection.
- Further discussion focused on the planned use of Isolation Forest, correlation mechanisms across logs, and integration of multiple signals for improved importance scoring and root cause analysis.

### Contribution:

- Sumukha: Implemented the correlation/graph_builder.py module in the correlation layer. Built a weighted undirected co-occurrence graph from parsed log events, linked flagged anomaly events to dedicated anomaly nodes, and added configurable parameters for the time window and node cap. Also added 23 unit tests and a manual inspection script.

- Ujwal: Initialized the scoring module structure and configuration by defining scoring weights, label thresholds, and DBSCAN parameters. Set up module stubs, input/output contracts, and updated the README with scoring pipeline documentation.

- Sharva: Developed the simulated sessionized log pipeline and implemented feature extraction for session-level metrics such as frequency and burstiness scores. Validated schema consistency and structured the pipeline to support further ML integration and anomaly detection enhancements.

- Vishon: Defined the PostgreSQL schema structure for logs and related pipeline data, verified table creation and consistency locally using Docker, configured the db_writer module to align with the database schema, created Elasticsearch index mappings for log fields, and implemented centralized .env-based environment variable handling with validation support.

- Shreeraksha M: Initiated the ML anomaly detection module by implementing the Isolation Forest–based anomaly detector skeleton with configurable contamination and hybrid scoring parameters. Worked on the initial trainer module structure for retraining and model serialization, documented key ML design decisions, and added preliminary tests for anomaly output and schema validation.


## **CPP Meeting 11: 12/05/26**

### Discussion:

- The meeting was cancelled due to Sem End Examinations.

### Contribution:

* Sharva Dhanvi V: Continued development of the Phase 2 feature engineering pipeline by integrating all feature modules into feature_pipeline.py. Implemented statistical, temporal, severity, and counter proximity features on sessionized log data, added schema validation and parquet export support, improved malformed-row handling with centralized logging, and expanded edge-case testing for timestamp ordering, sparse sessions, and missing values.

* Shreeraksha M: Continued implementation of the ML anomaly detection layer using Isolation Forest with configurable contamination and hybrid scoring support. Worked on sliding-window retraining, model persistence, cold-start fallback handling, anomaly output generation, and evaluator/test coverage for anomaly scoring workflows.

* Sumukha Rao H: Continued development of the correlation and shared infrastructure layers by scaling the graph builder for real datasets, implementing centrality computation and sequence detection, generating graph scoring outputs and graph exports, and simultaneously maintaining parsing validation, shared schema definitions, logger utilities, helper functions, and end-to-end pipeline orchestration support.

* Ujwal Hegde: Continued integration of the importance scoring pipeline by combining anomaly outputs, graph scores, and engineered features into a unified scoring workflow. Worked on configurable label mapping, DBSCAN-based incident clustering, root cause ranking, confidence scoring, and finalized output schema handling for scored logs and root cause datasets.

* Vishon Dsouza: Continued implementation of storage and visualization modules by developing PostgreSQL and Elasticsearch writers, refining schema and indexing support, scaffolding evaluation and benchmarking utilities, and configuring Grafana and Kibana dashboards for anomaly visualization, incident monitoring, and log exploration workflows.

---
## **CPP Meeting 12: 19/05/26**

### Discussion:

- The meeting was cancelled due to Sem End Examinations.

### Contribution:

- No contributions for this week due to Sem End Examinations.

---
## **CPP Meeting 13: 26/05/26**

### Discussion:

- The meeting was cancelled due to Sem End Examinations.

### Contribution:

- No contributions for this week due to Sem End Examinations.

---
##  **CPP Meeting 14: 02/06/26**

### Discussion:

* The ML pipeline and Incident Intelligence Dashboard were presented and reviewed.
* Mentor advised the team to properly document individual contributions for future presentations and project tracking.
* Discussed generating logs in multiple formats and scenarios to improve model training, evaluation, and robustness.

### Contribution:

* **Shreeraksha M:** Implemented the LLM summary generation module using Gemini with a batch-processing architecture and caching support. Added summary generation and regeneration workflows as per dashboard requirements. Developed the initial Streamlit dashboard structure and completed the basic UI design for the major dashboard pages. Implemented page layouts, navigation flow, and dashboard components required for incident visualization. Integrated summary display functionality into the dashboard interface.

* **Sumukha:** Worked on integrating all individual modules into a functioning end-to-end pipeline. Identified the gradual drift edge case and implemented sliding-window retraining to improve adaptation to evolving patterns. Created `fingerprint.py` to extract unique templates from incidents and compute Jaccard Similarity and Overlap Coefficient metrics. Generated synthetic datasets using Claude to inject anomaly and gradual drift scenarios. Tested the pipeline and analyzed expected versus actual behavior.

* **Ujwal Hegde:** Worked on the ML training and drift detection phase of the network anomaly detection pipeline. Studied the complete training architecture involving Isolation Forest, statistical drift detection, rolling feature storage, and automatic retraining. Generated realistic network log datasets, validated the training workflow through the pipeline, and analyzed model behavior, retraining mechanisms, and anomaly detection outputs. Currently working on a multi-day gradual drift simulation to evaluate system adaptability while maintaining accurate anomaly and root-cause detection.

* **Sharva:** Worked on synthetic data generation and validation for the anomaly detection pipeline. Created realistic network log scenarios covering normal behavior, routing instability, gradual drift, authentication attacks, and cross-system cascades. Defined anomaly and root-cause labels, validated dataset quality, and prepared ground-truth data for downstream ML training and evaluation.

---
## **CPP Meeting 15: 09/06/26**

### Discussion:

- Reviewed the integrated end-to-end pipeline and finalized the handoff plan for the dashboard and anomaly detection components.
- Discussed the need to synchronize the Groq LLM summary generation flow with the incident dashboard and confirm update frequency for summary regeneration.
- Evaluated the drift detection strategy and decided to add targeted alerts for gradual drift scenarios based on feature distribution shifts.
- Confirmed synthetic dataset coverage for model validation, ensuring normal, drift, attack, and correlated failure cases were represented.


### Contribution:

* **Ujwal Hegde:** Focused on improving the stability and maintainability of the core pipeline. Identified and resolved execution edge cases by implementing a critical fix to prevent the pipeline from silently continuing when a step produces an empty output. Additionally, refactored the core configuration logic to centralize output paths, successfully eliminating path duplication and reducing potential routing errors. Finally, streamlined the repository by auditing and removing redundant code lines, ensuring a cleaner and more reliable foundation for downstream validation and testing.

* **Sumukha:** Focused on the statistical correctness and evaluation rigor of the scoring pipeline. Built a new oracle evaluation harness that scores pipeline output against scenario_labels ground truth, wiring it in as a dedicated pipeline step with full test coverage. Drove a phase-1 score calibration effort retuning thresholds, switching graph centrality to PMI, and replacing optimistic metrics with honest ones. Resolved several phase-2 statistical defects, most notably eliminating Welford self-contamination in the streaming feature computation and auditing mean-fill behavior in the statistical features. Corrected incident severity aggregation to rank by true severity rather than alphabetical order. On the dashboard side, implemented the data access layer (database and Elasticsearch), added auto-detection of parsing mode on log upload, and contributed vendor-neutral and test dataset generators to support downstream validation.

* **Shreeraksha M:** Implemented the dashboard log upload workflow, enabling users to upload single or multiple log files and trigger the analysis pipeline directly from the dashboard. Extended the pipeline to support directory-based syslog processing, integrated background pipeline execution with progress tracking, and added result summarization with error handling for uploaded log analysis.

* **Sharva:** Conducted testing of the Upload & Analyze workflow with emphasis on anomaly detection metrics. Looked into inconsistencies in anomaly count reporting, validated anomaly data against database records, implemented necessary fixes, and verified dashboard behavior.

* **Vishon Dsouza:** Working on testing the custom dashboard with different datasets to identify potential issues and validate dashboard functionality across various scenarios.

---

## **CPP Meeting 16: 16/06/26**

### Discussion:

- The meeting was cancelled due to some technical difficulties.

### Contribution:

- No contributions for this week due to some technical difficulties.

---
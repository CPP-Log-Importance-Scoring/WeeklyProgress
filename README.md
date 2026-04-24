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

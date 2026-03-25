->Multi-layered architecture: Designed a structured system pipeline from log ingestion (Fluent Bit, Kafka) through normalization and template extraction to the final visualization layer.
->Scoring logic: Developed an importance_score formula combining event weight, log frequency (log-scaled), and correlation score to rank logs effectively.
->Event weighting: Implemented a rule-based approach to assign base weights based on event type, with log level acting as a dynamic modifier for severity.
->Incident correlation: Built a system to group related logs into incident clusters using template extraction and correlation based on time proximity and component similarity.

#Documentation
[View Project Documentation]
(System_Design.pdf)

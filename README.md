# YouTube-Comments-Sentiment-Analysis-GCP-

Real-Time YouTube Comments Sentiment Analysis (GCP)
This is a production-grade data engineering + DevOps pipeline on Google Cloud Platform. It collects live YouTube comments via the YouTube Data API, streams them through Pub/Sub, processes and scores sentiment (Positive/Negative/Neutral) using an Apache Beam pipeline on Dataflow, stores results in BigQuery, orchestrates workflows with Cloud Composer (managed Airflow), and visualizes in Power BI — with the entire infrastructure automated via Terraform + Ansible + Jenkins CI/CD.

<img width="853" height="426" alt="image" src="https://github.com/user-attachments/assets/5060ba03-5052-4065-bbca-b906c477567a" />


Pipeline flow:

Python app → fetches live YouTube comments → publishes to GCP Pub/Sub
Dataflow (Apache Beam) → consumes from Pub/Sub → applies NLP sentiment classification → writes to BigQuery
Cloud Composer → runs Airflow DAGs for health checks, batch jobs, metadata validation
Terraform → provisions all GCP resources (Pub/Sub, Dataflow, BigQuery, IAM, Composer, Storage)
Ansible → handles VM config, dependency installs, service account setup
Jenkins → CI/CD on every GitHub commit, triggers Terraform + Ansible automatically
Power BI → connects to BigQuery Gold layer for live sentiment dashboards

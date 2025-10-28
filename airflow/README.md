# Airflow DAGs

This directory contains Airflow DAGs for the Hotel Data Intelligence Platform.

## Structure

- **etl_pipelines/**: ETL pipelines for data ingestion and transformation
- **data_quality/**: Data quality checks and validation
- **ml_pipelines/**: Machine learning pipelines for predictive analytics

## Getting Started

1. Start Airflow with Docker:
   ```bash
   cd infrastructure
   docker-compose up -d
   ```

2. Access Airflow UI at http://localhost:8080
   - Username: airflow
   - Password: airflow

3. Monitor DAGs in the Airflow UI

## Custom Operators

Custom operators are located in `plugins/custom_operators/` for reusable components.

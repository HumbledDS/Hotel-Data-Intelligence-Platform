# dbt Models

This directory contains all dbt models for the Hotel Data Intelligence Platform.

## Structure

- **staging/**: Raw data transformations and data quality checks
- **mart/**: Business-ready dimensional models
- **metrics/**: Business metrics and KPIs

## Getting Started

1. Install dbt: `pip install dbt-snowflake`
2. Configure profiles in `profiles.yml`
3. Run models: `dbt run`
4. Test models: `dbt test`

## Model Layers

### Staging Layer
Raw data from source systems, cleaned and standardized.

### Mart Layer
Business-ready fact and dimension tables for analysis.

### Metrics Layer
Pre-calculated business metrics and KPIs (e.g., RevPAR, Occupancy Rate).

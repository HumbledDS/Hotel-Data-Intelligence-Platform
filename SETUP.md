# Hotel Data Intelligence Platform - Setup Guide

## Quick Start

### Prerequisites

- Python 3.10+
- Docker and Docker Compose
- Git

### 1. Environment Setup

```bash
# Clone the repository
git clone <repository-url>
cd Hotel-Data-Intelligence-Platform

# Install Python dependencies
pip install -r requirements.txt
```

### 2. Configure dbt

Edit `dbt/profiles.yml` with your Snowflake credentials:

```yaml
hotel_data_platform:
  target: dev
  outputs:
    dev:
      type: snowflake
      account: <your-account>
      user: <your-user>
      password: <your-password>
      # ... other settings
```

### 3. Start Airflow

```bash
cd infrastructure
docker-compose up -d
```

Access Airflow UI at http://localhost:8080
- Username: `airflow`
- Password: `airflow`

### 4. Run dbt Models

```bash
cd dbt
dbt deps  # Install dbt packages
dbt run  # Run all models
dbt test # Run tests
```

## Project Structure

```
├── airflow/          # Airflow DAGs and workflows
├── dbt/             # dbt models and transformations
├── micro-apps/      # Monitoring and dashboard apps
├── infrastructure/  # Docker, Kubernetes, Terraform configs
├── tests/           # Test files
└── docs/            # Documentation
```

## Next Steps

1. Create your first DAG in `airflow/dags/etl_pipelines/`
2. Add dbt models in `dbt/models/staging/`
3. Set up CI/CD by pushing to the main branch
4. Configure monitoring dashboards

## Support

For more information, see the main [README.md](README.md)

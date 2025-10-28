# Hotel-Data-Intelligence-Platform

Voici une proposition de projet personnel ambitieux qui couvre l'ensemble des technologies mentionnées et démontre des compétences clés pour un poste de Lead Data Platform dans l'hospitalité :

## 🏨 **Hotel Data Intelligence Platform**

### 📊 **Architecture Globale**
```
Airflow (Orchestration) → Snowflake (Storage) → dbt (Transformation) → Métriques Business
```

### 🎯 **Sous-projets modulaires**

#### 1. **Pipeline de Réservations en Temps Réel**
```python
# Architecture Airflow
reservation_pipeline/
├── dags/
│   ├── real_time_booking_etl.py
│   ├── data_quality_checks.py
│   └── anomaly_detection.py
├── dbt/models/
│   ├── staging/stg_reservations.sql
│   ├── mart/fact_daily_occupancy.sql
│   └── metrics/hotel_kpis.sql
```

**Fonctionnalités :**
- Ingestion de données de réservations (APIs fictives)
- Calcul du taux d'occupation en temps réel
- Détection d'anomalies (annulations massives, surréservations)
- Alertes automatiques via Slack/Email

#### 2. **Customer 360 & Segmentation**
```sql
-- Modèle dbt avancé
WITH customer_journey AS (
  SELECT 
    customer_id,
    COUNT(DISTINCT booking_id) as total_bookings,
    AVG(booking_value) as avg_booking_value,
    -- Pattern recognition pour la fidélité
    LAG(check_in_date) OVER (PARTITION BY customer_id ORDER BY check_in_date) as previous_stay
  FROM {{ ref('fct_bookings') }}
)
```

**Analyses :**
- Scoring de valeur client (RFM)
- Segmentation comportementale
- Prédiction de la probabilité de retour

#### 3. **Price Optimization Engine**
```python
# DAG Airflow pour l'optimisation tarifaire
def calculate_dynamic_pricing(**context):
    # Analyse de la demande saisonnière
    # Concurrence locale (données simulées)
    # Optimisation du revenu par chambre (RevPAR)
    return optimized_prices
```

#### 4. **Data Quality Framework**
```yaml
# dbt tests avancés
models:
  - name: fct_reservations
    tests:
      - dbt_utils.equal_rowcount:
          compare_model: ref('stg_reservations')
      - unique_key: ['booking_id']
      - not_null: ['customer_id', 'hotel_id']
      - accepted_range:
          field: 'booking_value'
          min: 0
          max: 10000
      - custom_anomaly_detection:
          sql: "AVG(booking_value) OVER (PARTITION BY hotel_id)"
```

### 🚀 **Features Techniques Avancées**

#### **Micro-app de Monitoring**
```python
# Streamlit/FastAPI pour la surveillance
@app.get("/api/data-quality-metrics")
def get_quality_metrics():
    return {
        "freshness_score": calculate_freshness(),
        "completeness_score": calculate_completeness(),
        "anomaly_alerts": get_recent_anomalies()
    }
```

#### **CI/CD pour la Data Platform**
```yaml
# .github/workflows/data-pipeline-ci.yml
name: Data Pipeline CI
on:
  push:
    branches: [main]
jobs:
  test-dbt:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Test dbt models
        run: |
          dbt test
          dbt run --models tag:ci
```

#### **Monitoring & Alerting**
```python
# Custom Airflow operators
class DataFreshnessOperator(BaseOperator):
    def execute(self, context):
        # Vérification de la fraîcheur des données
        # Alerting si données > 2h old
        pass
```

### 🏗️ **Structure du Repository GitHub**
```
hotel-data-platform/
├── airflow/
│   ├── dags/
│   │   ├── etl_pipelines/
│   │   ├── data_quality/
│   │   └── ml_pipelines/
│   └── plugins/custom_operators/
├── dbt/
│   ├── models/
│   │   ├── staging/
│   │   ├── mart/
│   │   └── metrics/
│   ├── tests/custom_tests/
│   └── macros/
├── micro-apps/
│   ├── data_monitoring/
│   ├── anomaly_dashboard/
│   └── kpi_reporting/
├── infrastructure/
│   ├── docker-compose.yml
│   ├── kubernetes/
│   └── terraform/
├── tests/
├── docs/
└── .github/workflows/
```

### 🔧 **Points Techniques Démonstratifs**

1. **Orchestration Complexe** : DAGs interdépendants, gestion des dépendances
2. **Quality Engineering** : Tests unitaires, dbt tests, monitoring custom
3. **Performance** : Optimisation Snowflake, clustering des tables
4. **DevOps** : CI/CD, containerisation, déploiement Kubernetes
5. **Innovation** : Micro-apps, intégration IA (recommandations)

### 📈 **Métriques de Performance Implémentées**

```sql
-- Dans dbt metrics
metric:
  - name: monthly_recurring_revenue
    model: ref('fct_subscriptions')
    label: Monthly Recurring Revenue
    calculation_method: average
    expression: revenue_amount
    timestamp: created_date
    dimensions:
      - plan_type
      - hotel_chain
```

### 🎨 **Différenciateurs pour le Poste**

- **Architecture modulaire** et scalable
- **Documentation technique** complète
- **Tests automatisés** poussés
- **Monitoring business et technique**
- **Focus hospitality** avec métriques sectorielles
- **Veille technologique** intégrée (ex: utilisation de nouvelles features Snowflake) -> progression vers chatbots, usage de LLM type api OPENAI

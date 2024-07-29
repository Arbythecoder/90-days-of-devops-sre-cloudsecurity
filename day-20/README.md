## Day 20: Configuring Prometheus Alerting

This day focuses on setting up Prometheus alerting to monitor critical system metrics and send notifications when thresholds are exceeded.

### Setup

1. **Folder Structure:**
day-20
├── prometheus
│ └── prometheus.yml
├── alerts
│ └── alerts.yml
└── alertmanager
└── alertmanager.yml

2. **Configuration Files:**
* `prometheus.yml` (in `prometheus/`)
* `alerts.yml` (in `alerts/`)
* `alertmanager.yml` (in `alertmanager/`)

**Example `prometheus.yml`:**

```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

alerting:
  alertmanagers:
    - static_configs:
        - targets:
          - 'localhost:9093'

rule_files:
  - '/etc/prometheus/alerts/alerts.yml'

alerting:
  alertmanagers:
    - static_configs:
        - targets:
          - 'localhost:9093'

rule_files:
  - '/etc/prometheus/alerts/alerts.yml'
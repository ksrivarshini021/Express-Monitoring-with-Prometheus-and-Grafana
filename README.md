# Express Monitoring with Prometheus and Grafana

This bases of this project is to familarize usage of the Node.js API using Prometheus for extracting metrics and visualize them through Grafana dashboards.

The monitoring stack used in this project includes:
- Express.js
- prom-client
- Prometheus
- Grafana
- Docker


## Methodology 

#### 1. Creating API server

The first step was to create a simple API server using Express. The server exposes endpoints that simulate API requests and responses.

To enable monitoring, the `prom-client` library was integrated into the application. This library provides utilities to collect and expose application metrics in a format compatible with Prometheus.

Metrics collected include:
- Total HTTP requests
- CPU usage
- Memory usage
- Event loop statistics

The metrics are exposed through a `/metrics` endpoint which Prometheus periodically scrapes.

#### 2. Containing the applciation 

The application was containerized using Docker for easy deployment. Containerization ensures that the application and its dependencies run consistently across different environments.

#### 3. Prometheus Configuration

Prometheus was used as the monitoring server responsible for scraping metrics from the application.
Prometheus uses a pull-based model, it periodically sends HTTP requests to the metrics endpoint.

Prometheus retrieves metrics from `http://express-app:8000/metrics`

#### 4. Dashboard Visualization

To visualize the collected metrics, Grafana was deployed. Grafana connects to Prometheus as a data source and allows users to build dashboards for monitoring system performance. The steps are as follows:

- Deploy Grafana using Docker
- Add Prometheus as a data source
- Import a dashboard from Grafana.com
- Configure queries to match the available metrics

Grafana provides real-time visualization of system metrics such as:
Request rates
CPU utilization
Memory consumption
API usage patterns

### Deployment

All services were deployed using Docker Compose to simplify system startup.

To deploy throught doker: `docker compose up --build`. This command launches the API server, Prometheus monitoring server, and Grafana dashboard service.

Once deployed, the monitoring pipeline provides real-time visibility into application performance.
The `/metrics` endpoint exposes metrics such as:
```
http_requests_total{method="GET",route="/",status="200"} 5
process_cpu_user_seconds_total 0.12
process_resident_memory_bytes 48234496
```

Prometheus continuously scrapes these metrics and stores them as time-series data. Grafana dashboards allow users to visualize these metrics, enabling monitoring of API traffic and server resource usage.

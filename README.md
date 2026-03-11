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

To enable monitoring, the 'prom-client' library was integrated into the application. This library provides utilities to collect and expose application metrics in a format compatible with Prometheus.

Metrics collected include:
- Total HTTP requests
- CPU usage
- Memory usage
- Event loop statistics

The metrics are exposed through a '/metrics' endpoint which Prometheus periodically scrapes.

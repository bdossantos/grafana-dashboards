# Grafana dashboards

A collection of Grafana dashboards backed by [Prometheus](https://prometheus.io/) data sources.

## Dashboards

| Dashboard | Description |
| --- | --- |
| [HAProxy](prometheus/haproxy-2-full.json) | HAProxy metrics via the Prometheus exporter (HAProxy 2.x) |
| [Mimir / Alertmanager](prometheus/mimir-alertmanager.json) | Grafana Mimir Alertmanager overview |
| [Mimir / Alertmanager Resources](prometheus/mimir-alertmanager-resources.json) | Grafana Mimir Alertmanager resource usage |
| [Mimir / Compactor](prometheus/mimir-compactor.json) | Grafana Mimir Compactor overview |
| [Mimir / Compactor Resources](prometheus/mimir-compactor-resources.json) | Grafana Mimir Compactor resource usage |
| [Mimir / Config](prometheus/mimir-config.json) | Grafana Mimir configuration |
| [Mimir / Object Store](prometheus/mimir-object-store.json) | Grafana Mimir object store metrics |
| [Mimir / Overrides](prometheus/mimir-overrides.json) | Grafana Mimir per-tenant overrides |
| [Mimir / Overview](prometheus/mimir-overview.json) | Grafana Mimir high-level overview |
| [Mimir / Overview Networking](prometheus/mimir-overview-networking.json) | Grafana Mimir overview networking |
| [Mimir / Overview Resources](prometheus/mimir-overview-resources.json) | Grafana Mimir overview resource usage |
| [Mimir / Queries](prometheus/mimir-queries.json) | Grafana Mimir query path metrics |
| [Mimir / Reads](prometheus/mimir-reads.json) | Grafana Mimir reads path overview |
| [Mimir / Reads Networking](prometheus/mimir-reads-networking.json) | Grafana Mimir reads path networking |
| [Mimir / Reads Resources](prometheus/mimir-reads-resources.json) | Grafana Mimir reads path resource usage |
| [Mimir / Remote Ruler Reads](prometheus/mimir-remote-ruler-reads.json) | Grafana Mimir remote ruler reads |
| [Mimir / Remote Ruler Reads Networking](prometheus/mimir-remote-ruler-reads-networking.json) | Grafana Mimir remote ruler reads networking |
| [Mimir / Remote Ruler Reads Resources](prometheus/mimir-remote-ruler-reads-resources.json) | Grafana Mimir remote ruler reads resource usage |
| [Mimir / Rollout Progress](prometheus/mimir-rollout-progress.json) | Grafana Mimir rollout progress |
| [Mimir / Ruler](prometheus/mimir-ruler.json) | Grafana Mimir Ruler metrics |
| [Mimir / Scaling](prometheus/mimir-scaling.json) | Grafana Mimir scaling recommendations |
| [Mimir / Slow Queries](prometheus/mimir-slow-queries.json) | Grafana Mimir slow query analysis |
| [Mimir / Tenants](prometheus/mimir-tenants.json) | Grafana Mimir per-tenant metrics |
| [Mimir / Top Tenants](prometheus/mimir-top-tenants.json) | Grafana Mimir top tenants by usage |
| [Mimir / Writes](prometheus/mimir-writes.json) | Grafana Mimir writes path overview |
| [Mimir / Writes Networking](prometheus/mimir-writes-networking.json) | Grafana Mimir writes path networking |
| [Mimir / Writes Resources](prometheus/mimir-writes-resources.json) | Grafana Mimir writes path resource usage |
| [MySQL](prometheus/mysql-overview.json) | MySQL server metrics via the Prometheus mysqld exporter |
| [Node Exporter Full](prometheus/node-exporter-full.json) | Comprehensive host metrics via the Prometheus node exporter |
| [Redis](prometheus/redis.json) | Redis metrics via the Prometheus Redis Exporter 1.x |
| [Thumbor](prometheus/thumbor.json) | Thumbor image service metrics via Prometheus |

## Usage

1. In Grafana, go to **Dashboards → Import**.
2. Click **Upload JSON file** and select the desired `.json` file from the `prometheus/` directory, or paste the raw JSON content.
3. Select the Prometheus data source and click **Import**.

## Resources

* https://github.com/percona/grafana-dashboards
* https://github.com/rfrail3/grafana-dashboards
* https://github.com/oliver006/redis_exporter/blob/master/contrib/grafana_prometheus_redis_dashboard.json

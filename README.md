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
| [Memcached](prometheus/memcached.json) | Memcached metrics via the Prometheus memcached exporter |
| [MySQL](prometheus/mysql-overview.json) | MySQL server metrics via the Prometheus mysqld exporter |
| [Node Exporter Full](prometheus/node-exporter-full.json) | Comprehensive host metrics via the Prometheus node exporter |
| [Redis](prometheus/redis.json) | Redis metrics via the Prometheus Redis Exporter 1.x |
| [Storage Health](prometheus/storage-health.json) | Fleet NVMe / SSD / HDD health via the node exporter textfile collector |
| [Thumbor](prometheus/thumbor.json) | Thumbor image service metrics via Prometheus |

## Usage

1. In Grafana, go to **Dashboards → Import**.
2. Click **Upload JSON file** and select the desired `.json` file from the `prometheus/` directory, or paste the raw JSON content.
3. Select the Prometheus data source and click **Import**.

### Storage Health

The Storage Health dashboard uses metrics from [`nvme_metrics.sh`](https://github.com/bdossantos/prometheus-alert-rules/blob/master/textfile-collector/nvme_metrics.sh) and [`smartmon.sh`](https://github.com/bdossantos/prometheus-alert-rules/blob/master/textfile-collector/smartmon.sh).
Schedule the appropriate scripts on each server, write their output atomically to `.prom` files in node exporter's configured `--collector.textfile.directory`, and scrape node exporter with Prometheus. The NVMe script requires root, `nvme-cli` and `jq`; the SMART script requires `smartctl` and permission to access the drives. Either collector can be used alone; panels for the other collector will have no data.

Select **Prometheus**, then use the multi-select **Job** and **Instance** filters for a fleet or individual hosts. **NVMe device** filters the NVMe collector's `device` label (such as `nvme0n1`); **SMART disk** independently filters the SMART collector's `disk` label (such as `/dev/sda`). The dashboard includes fleet counts, per-drive health and identity, temperature, NVMe endurance/spare/media errors, SMART sector errors and SSD lifetime indicators, power-on time, and collector diagnostics.

- NVMe and SMART device counts can overlap: do not sum them. SMART's `type` is a transport (such as `sat` or `scsi`), not an SSD/HDD classification.
- Missing metrics are not treated as healthy or zero. Sleeping/inactive SMART devices may have no health or attribute samples; consult the inactive-device count and collector diagnostics.
- SMART attributes and their encoding vary by vendor, model and transport. SSD lifetime indicators are normalized vendor scores, not universally comparable percentages. Temperature thresholds are illustrative and should be adapted to drive specifications.
- `nvme_critical_warning_total` is a current warning bitmask despite its name, so it is not queried with `rate` or `increase`. NVMe endurance and spare metrics are ratios (`1` = 100%).
- SMART collection age is based on `smartmon_smartctl_run`; compare it with your script schedule. The NVMe script has no run timestamp. Textfile scrape errors cover all textfiles on the selected targets and cannot detect a missing or stale NVMe file; monitor expected file modification times (`node_textfile_mtime_seconds`) and missing targets separately.

## Development

After updating dashboard JSON files, run [Prettier](https://prettier.io/) to keep formatting consistent:

```sh
prettier --write "prometheus/**/*.json"
```

## Resources

* https://github.com/percona/grafana-dashboards
* https://github.com/rfrail3/grafana-dashboards
* https://github.com/oliver006/redis_exporter/blob/master/contrib/grafana_prometheus_redis_dashboard.json

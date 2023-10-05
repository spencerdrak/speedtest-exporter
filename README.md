# Speedtest Exporter

Simple **Speedtest exporter** for **Prometheus** written in **Python** using the
official CLI from **Ookla**

You can get all the documentation [here](https://docs.miguelndecarvalho.pt/projects/speedtest-exporter/)

# Installing

You can easily install this chart via helm: 

```
helm repo add spencerdrak https://spencerdrak.github.io/public-helm-charts/
helm install -n speedtest-exporter speedtest-exporter spencerdrak/speedtest-exporter --version 0.9.0
```

Unfortunately, the helm chart isn't yet configured for a service monitor. PRs Welcome!

If your prometheus isn't configured for any sort of scraping, here's the relevant config:

```
- job_name: speedtest-exporter
  honor_timestamps: true
  scrape_interval: 1h
  scrape_timeout: 1m
  metrics_path: /metrics
  scheme: http
  follow_redirects: true
  enable_http2: true
  static_configs:
  - targets:
    - speedtest-exporter.speedtest-exporter.svc.cluster.local:9798
```

## Thanks to

- [Nils Müller](https://github.com/tyriis)

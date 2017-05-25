# gitlab-ci-runner-grafana
grafana dashboard for gitlab-ci-runner metrics


in the runners `config.toml` add a `metrics_server` key to the global section
the value can specify any `[host]:<port>` combination, like `":9999"`

configure a scraping job in your prometheus instance like so:
```
- job_name: 'gitlab-ci-runner'
    scrape_interval: 5s
    static_configs:
      - targets: ['1.2.3.1:9999', '1.2.3.2:9999']
        labels:
          alias: gitlab-ci-runner
```

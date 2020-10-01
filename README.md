# Prometheus blackbox HTTP probing monitoring starter

A docker-compose-based basic configuration of Prometheus + Alertmanager + Alertmanager Telegram bot.

Probes http/s endpoints to ensure the are up, issues alerts if gets anything except 2xx, sends these to telegram.

## How to set up

1. Clone the repo
2. Make changes to the config/prometheus.yml - replace endpoints to monitor (http and https) with your own ones (look for targets:)
3. Copy .env_ to .env
4. Set your Telegram user ID and the token of your Telegram bot in .env
5. Procure a machine with docker and docker-compose
6. mkdir /var/monitoring, mkdir /var/alertbotdata on the machine
7. Drop repo files to /var/monitoring
8. cd /var/monitoring
9. docker-compose pull && docker-compose up -d
10. Verify Prometheus GUI is available on http://host:9090 and Alertmanager on http://host:9093
11. Kill one of your sites and check that you see the alert both in Alertmanager GUI and in Telegram
12. Optionally create a bare git repo on the machine and drop in the provided post-receive hook to enable updates through git push

## Built from

- [Prometheus](https://prometheus.io/)
- [Prometheus Blackbox Exporter](https://github.com/prometheus/blackbox_exporter)
- [Alertmanager](https://github.com/prometheus/alertmanager)
- [Alertmanager Bot](https://github.com/metalmatze/alertmanager-bot)

## To improve

- Currently update through git hook is done by restarting the containers - could just force them to reload the configs

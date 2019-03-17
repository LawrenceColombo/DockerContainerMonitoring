# Docker Monitoring Solution

A simple project to easiy deploy Grafana to monitor a host system as well as monitor running docker containers.

## Project Structure

This project consists of three submodules:
- Standalone: Monitors host system and running containers as well as exposing Grafana
- Docker Host: Intended to be run on every host machine you want to monitor
- Grafana Host: Can be run on a seperate host machine that acts as a single source for Grafana

## Standalone
The standalone module is meant to run on a single machine, that will both monitor the host system and host the Prometheus and Grafana instance.

To run the standalone, use the docker compose file inside the standalone folder.

## Docker Host

The docker host module is meant to be run on a machine you want to monitor that allows its metrics to be scraped remotely.

To run the docker host module, use the docker compose file insde the docker host folder.

## Grafana Host

The grafana host is meant to run on a seperate machine as the docker host module and sets up the Grafana instance that is browsable at http://localhost

The one setting that the Grafana host needs is to change the Prometheus Job target which is found in the `grafana_host/prometheus/prometheus.yml` file.

Change both the Node-exporter and CAdvisor job targets to your docker host domain.
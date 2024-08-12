# Deployment
In this repo you can find a few Ansible playbooks for configuring monitoring on already deployed instance.

username for the instance - ubuntu (default of amazon)

The whole repo is tested on VirtualBox with OS Ubuntu Linux

These sets of playbook have the following use:
- os-update.yml - updates the packages of the OS ( this is from security perspective because sometimes there are packages
vulnerabilities that may cause a security breach.)
- deploy-monitoring.yml - this playbook install and configure a prometheus, grafana, postgres and postgres-exporter

## Why Prometheus?
Probably one of the best monitoring solutions

## Why Grafana?
The easiest way to visualize the metrics gathered from Prometheus using Prometheus datasource and dashboard from 
open-source community

## Why Postgres?
I`ve decided to deploy and configure a postgresql just for fun and try to get some real metrics from a database. I've
configured and one test database to have some dummy database to monitor

## Why Postgres-exporter?
The exporters are important part of the monitoring because they gather the metrics and expose them on a port from where 
Prometheus can pull data and this data can be easily visualized in Grafana afterward.

All these directories are Ansible roles generated with ansible-galaxy.
You can see templating using Jinja2 in the roles.

You need to configure a Prometheus datasource to install a Postgres dashboard to see the metrics.
in the datasource configuration "Prometheus server URL: http://localhost:9090" because we are deploying it locally.

NOTE:
It is not the power of ansible to use it locally, but in this case is easier for testing.
The right way is to have a hosts file with the following configuration:

[monitoring]\
<ip/dns of the monitoring instance>

and then apply configuration from a control node.
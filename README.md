Ark Proxy
=========

This repo consists of configuration files to set up an authentiating caching
proxy to ark.stackhhpc.com.

The proxy consists of two containers, deployed with docker compose.
One is a container registry
The other is a generic http caching proxy based on nginx, designed for apt and dnf package downloads

Repo files
----------

1. `docker-compose.yml` A docker compose to deploy two containers - a docker
container registry, and a general nginx http caching proxy
2. `nginx.conf` A config file for the nginx container
3. `config.yml` A config file for the container registry

Deployment
----------
Both container config files require credentials to reach Ark, which are omitted
for obvious reasons.

After cloning the repo, filling in the credentials, and running `docker compose
up -d`, the container registry will be present on port 5000, and the package proxy on port 80.


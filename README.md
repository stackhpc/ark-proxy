Ark Proxy
=========

This repo consists of configuration files to set up an authentiating caching
proxy to ark.stackhhpc.com.

The proxy consists of two containers, deployed with docker compose. One is a
[Zot](https://zotregistry.dev) container registry on port 5000 (with web UI).
The other is a generic http caching proxy based on nginx which covers three
artefact types: Authenticated apt/dnf repo content from Ark on port 80, Ansible
Galaxy collections and roles on port 8080, and PyPI packages on port 8081.

Repo files
----------

1. `docker-compose.yml` A docker compose to deploy two containers - a Zot
container registry, and a general nginx http caching proxy
2. `zot/config.json` A config file for the Zot registry
3. `nginx.conf` A (poorly named) config file for caching Ark package repo
   content in the nginx container
3. `galaxy.conf` A config file for caching Ansible Galaxy content in the nginx
   container
3. `pypi.conf` A config file for caching PyPI content in the nginx container

Deployment
----------
Both the container registry and apt/dnf package cache require credentials to
reach Ark, which are omitted for obvious reasons. Zot reads its credentials from
`zot/credentials.json`, which you must create.

After cloning the repo and filling in the credentials, run `docker compose up
-d`.


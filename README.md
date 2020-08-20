This is a fork of the Git repo of the official Docker image for [Odoo](https://registry.hub.docker.com/_/odoo/). 
See the Hub page for the full readme on how to use the Docker image and for information regarding contributing and issues.

The full readme is generated over in [docker-library/docs](https://github.com/docker-library/docs), specifically in [docker-library/docs/odoo](https://github.com/docker-library/docs/tree/master/odoo).

The changes I made in this fork:
- Offer only ODOO 13.0, with always latest version
- Add ptvsd to image and implement attach-hook for remote debugging
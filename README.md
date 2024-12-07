# OS-installation-with-docker



# Plone Docker Repository

This repository provides a comprehensive guide and resources for working with the Plone Docker image. Plone is a powerful open-source content management system (CMS) built on the Zope application server.

---

## Quick Reference

### Maintained by:
Plone Community

### Where to Get Help:
- **Docker Community Slack**
- **Server Fault**
- **Unix & Linux**
- **Stack Overflow**

### Where to File Issues:
[Plone Docker GitHub Issues](https://github.com/plone/plone.docker/issues)

### Supported Tags and Dockerfile Links:
- `5.2.14-python38`, `5.2-python38`, `5-python38`, `python38`, `5.2.14`, `5.2`, `5`, `latest`

### Supported Architectures:
- **amd64** (see more details in the [repo-info](https://github.com/docker-library/repo-info))

---

## Features
- Support for Plone 5.x and 4.x versions
- Enable add-ons via environment variables
- Debian or Alpine-based images
- Built-in RelStorage and LDAP/AD support (Plone 5.2.4+)

---

## Usage

### Start a Single Plone Instance
Run the following command to start the latest Plone 5 container (Debian-based):

```bash
docker run -p 8080:8080 plone

Access your instance at http://localhost:8080 with default credentials:

Username: admin
Password: admin
Start a Plone ZEO Cluster
For production setups requiring a ZEO cluster, follow these steps:

Start the ZEO server:
docker run --name=zeo plone zeo

Start two Plone clients:
docker run --link=zeo -e ZEO_ADDRESS=zeo:8080 -p 8081:8080 plone
docker run --link=zeo -e ZEO_ADDRESS=zeo:8080 -p 8082:8080 plone

Add-Ons
Enable Plone add-ons via the ADDONS environment variable:

bash
Copy code
docker run -p 8080:8080 -e ADDONS="eea.facetednavigation Products.PloneFormGen" plone
Specify versions:

bash
Copy code
-e ADDONS="eea.facetednavigation collective.easyform" \
-e VERSIONS="eea.facetednavigation=13.3 collective.easyform=2.1.0"

Supported Environment Variables
Basic Configuration
ADDONS – Install Plone add-ons.
SITE – Initialize a Plone instance with a specific ID.
ZEO_ADDRESS – Configure the container as a ZEO client.
VERSIONS – Use specific add-on or library versions.
Advanced Options
PLONE_SITE, SITE – Add Plone site on first run.
PLONE_ADDONS, ADDONS – Customize Plone via add-ons.
PLONE_PROFILES, PROFILES – Include GenericSetup profiles.
ZEO_SHARED_BLOB_DIR – Share blob directories between ZEO server and instance.
For a full list of variables and configurations, visit the documentation.

REST API
Plone includes a REST API for programmatic access:

bash
Copy code
docker run -p 8080:8080 -e SITE=plone plone
curl -H 'Accept: application/json' http://localhost:8080/plone
Documentation
Visit Plone Documentation for complete guides, tutorials, and reference material.

csharp
Copy code

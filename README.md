Kibana
========
[![Galaxy](https://img.shields.io/badge/galaxy-samdoran.kibana-blue.svg?style=flat)](https://galaxy.ansible.com/samdoran/kibana)
[![Build Status](https://travis-ci.org/samdoran/ansible-role-kibana.svg?branch=master)](https://travis-ci.org/samdoran/ansible-role-kibana)

Install Kibana

Requirements
------------

TCP port 5601 open in the firewall.


Role Variables
--------------

| Name              | Default Value       | Description          |
|-------------------|---------------------|----------------------|
| `es_http_port` | `9200` | Port to communicate with Elasticsearch. |
| `es_http_listen_port` | `{{ es_http_port }}` | Can be set to a different value when using a TLS proxy in front of Elasticsearch and you want to talk directly to Elasticsearch service and bypass the proxy. |
| `kibana_version` | `4.5` | Version number used in `kibana.repo.j2` template. The latest version from that repository will be installed. |
| `kibana_tls_enabled` | `False` | Whether or not to use TLS for connections from the browser to Kibana. Setting this to `True` also inserts `kibana_service_ssl_cert` and `kibana_service_ssl_key` into `kibana.yml`, so make sure those values are correctly defined as well. |
| `kibana_tls_crt_path` | `/etc/pki/tls/certs` | Location of the Kibana TLS certificate will be copied to. |
| `kibana_tls_key_path` | `/etc/pki/tls/private` | Locate of the Kibana TLS private key will be copied to. |
| `kibana_tls_filename` | `{{ ansible_fqdn }}` | Basename used for naming certificate and private key files. |
| `kibana_elasticsearch_tls_enabled` | `False` | Whether or not to use TLS for connections from the Kibana to Elasticsearch. Setting this to `True` also inserts `kibana_service_ssl_cert` and `kibana_service_ssl_key` into `kibana.yml`, so make sure those values are correctly defined as well. |
| `kibana_elasticsearch_tls_crt_path` | `/etc/pki/tls/certs` | Location of the TLS certificate used to validate the identity of the Elasticsearch node. |
| `kibana_elasticsearch_tls_key_path` | `/etc/pki/tls/private` | Locate of the TLS key used to validate the identity of the Elasticsearch node. |
| `kibana_elasticsearch_tls_filename` | `{{ ansible_fqdn }}` | Basename used for naming certificate and private key files used by the Elasticsearch node. |
| `kibana_tls_cerficates` | `[see defaults/main.yml` | List of TLS files to copy, their destinations, and optionally ower, group, and mode. |

All other settings available in `kibana.yml` can be set as variables. See `defaults/main.yml` for available settings and the destripition of what they do.

Dependencies
------------

None

Example Playbook
----------------

        hosts: all
        roles:
            - samdoran.java
            - samdoran.elasticsearch
            - samdoran.kibana

License
-------

MIT

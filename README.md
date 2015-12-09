Kibana
========

Install Kibana 3.

Requirements
------------

TCP ports 80, 443, 9200, and 9300 open in iptables.


Role Variables
--------------

| Name              | Default Value       | Description          |
|-------------------|---------------------|----------------------|
| `kibana_zip` | `http://download.elasticsearch.org/kibana/kibana/kibana-latest.zip` | Zip file containing Kibana release |
| `kibana_git_url` | `https://github.com/elasticsearch/kibana.git` | Git repo where Kibana will be checked out out from. |
| `kibana_git_version` | `kibana3` | Git branch to checkout. |
| `kibana_root` | `/var/www/kibana/src` | Root directory served by nginx containing kibana. |
| `kibana_ssl_crt`| [undefined] | SSL public certificate. |
| `kibana_ssl_key` | [undefined] | SSL private key. |
| `kibana_dataonly_es` | `False` | Make kibana elasticsearch node data only and never a master. |
| `kibana_default_route` | [undefined] | Override the default landing page. |
| `kibana_update_cert` | `False` | Whether or not to copy new SSL private and pubilc key files. |

Dependencies
------------

- Elasticsearch role
- nginx role

Example Playbook
----------------

        hosts: all
        roles:
            - { role: kibana, kibana_dataonly_es: True }

License
-------

MIT

kibana
========

Install nginx, kibana, and elasticsearch. Configure the node as a data-onle elasticsearch node using nginx as an HTTPS proxy to elasticsearch. A self-signed certificate is included. Creating a certificate and storing it in an Ansible vault is recommended.

Requirements
------------



Role Variables
--------------

**kibana_zip**              Zip file containing kibana release

**kibana_git_url**          Git repo where Kibana will be checked out from

**kibana_root**             Root directory served by nginx containing kibana

**kibana_ssl_crt**          SSL public key

**kibana_ssl_key**          SSL private key. I recommend storing this in an Ansible vault.

**kibana_dataonly_es**      Make kibana elasticsearch node data only and never a master

**kibana_ssl_kibana_ssl_basename**    Name of SSL key files. `.crt` is added to the end of the public key and `.key` is added to the end of the private key. (Default: {{ ansible_fqdn }})

**kibana_default_route**    Override the default landing page

**kibana_update_cert** Whether or not to copy new SSL private and pubilc key files. (Default: undefined)

Dependencies
------------

- Elasticsearch role.

- TCP ports 80, 443, 9200, and 9300 open in iptables.

Example Playbook
----------------

        hosts: all
        roles:
            - { role: kibana, kibana_dataonly_es: true }

License
-------

MIT

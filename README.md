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

**kibana_ssl_cert_file**    Name of SSL public key file. `.crt` is added to the end. (Default: {{ ansible_fqdn }})

**kibana_ssl_key_file**    Name of SSL private key file. `.key` is added to the end. (Default: {{ ansible_fqdn }})

**kibana_default_route**    Override the default landing page

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

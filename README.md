Kibana
========

Install Kibana 3.

Requirements
------------

TCP ports 80, 443, 9200, and 9300 open in iptables.


Role Variables
--------------

Zip file containing kibana release:
    
    kibana_zip: http://download.elasticsearch.org/kibana/kibana/kibana-latest.zip

Git repo where Kibana will be checked out from:
    
    kibana_git_url: https://git.royall.com/sdoran/kibana-alex.git

Git branch to checkout:

    kibana_git_version: master

Root directory served by nginx containing kibana
    
    kibana_root: /var/www/kibana/src

SSL cert and key. I recommend storing the key in an Ansible vault.
    
    kibana_ssl_crt: |   
    kibana_ssl_key: |

Make kibana elasticsearch node data only and never a master
    
    kibana_dataonly_es: False

Name of SSL key files. `.crt` is added to the end of the public key and `.key` is added to the end of the private key. (Default: {{ ansible_fqdn }})
    
    kibana_ssl_kibana_ssl_basename

Override the default landing page:
    
    kibana_default_route: /dashboard/file/default.json

Whether or not to copy new SSL private and pubilc key files. (Default: false)
    
    kibana_update_cert: False

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

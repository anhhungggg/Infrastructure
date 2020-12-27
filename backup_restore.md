Nginx
---
Install and configure with Ansible:
~~~
ansible-playbook lab02_web_server.yaml
~~~

AGAMA
-----
Install and configure with Ansible:
~~~
ansible-playbook lab03_web_app.yaml
~~~
Restore the data from the backup:
~~~
su - backup duplicity --no-encryption restore rsync://<github_user>@backup.skaldr.io//home/<github_user>/ /home/backup/restore/
su - backup mysql agama < /home/backup/restore/agama.sql
~~~

DNS
---
Install and configure with Ansible:
~~~
ansible-playbook lab05_dns.yaml
~~~

Prometheus
---
Install and configure with Ansible:

~~~
ansible-playbook lab06_prometheus.yaml
~~~

Grafana
---
Install and configure with Ansible:
~~~
ansible-playbook lab07_grafana.yaml
~~~
Restore the data from the backup:
~~~
su - backup duplicity --no-encryption restore rsync://<github_user>@backup.skaldr.io//home/<github_user>/ /home/backup/restore/
su - backup cp -a /home/backup/backup/grafana/* /var/lib/grafana/
~~~

Exporters
---
- (available exporter tags: bind_exporter,nginx_exporter,mysql_exporter,node_exporter)
Install and configure with Ansible:
~~~
ansible-playbook exporters.yaml --tags "<exporter_name>"
~~~

Telegraf
---
Install and configure with Ansible:
~~~
ansible-playbook lam08_logging.yaml --tags "telegraf"
~~~

Rsyslog input for telegraf
---
Install and configure with Ansible:
~~~
ansible-playbook lam08_logging.yaml --tags "rsyslog"
~~~

Influxdb
---
Install and configure with Ansible:
~~~
ansible-playbook lam08_logging.yaml (optional: --tags "influxdb" not included telegraf and rsyslog)
~~~
Restore the data from the backup:
~~~
su - backup duplicity --no-encryption restore rsync://<github_user>@backup.skaldr.io//home/<github_user>/ /home/backup/restore/
su - backup cp -a /home/backup/restore/influxdb/* /var/lib/influxdb/
~~~

For latest restore point:
---
~~~
su - backup duplicity --force --no-encryption restore rsync://<github_user>@backup.skaldr.io//home/<github_user>/ /home/backup/restore/
~~~

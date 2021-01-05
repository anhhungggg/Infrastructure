Nginx
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "nginx"
~~~

MySQL (include mysql_exporter)
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "mysql"
~~~

AGAMA
-----
Restore the data from the backup:  
As backup user:
~~~
duplicity --no-encryption restore rsync://anhhungggg@backup.skaldr.io//home/anhhungggg/ /home/backup/restore/
mysql agama < /home/backup/restore/agama.sql
~~~
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "agama_docker"
~~~

DNS
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "dns_servers"
~~~

Prometheus
---
Install and configure with Ansible:

~~~
ansible-playbook infra.yaml --tags "prometheus"
~~~

Grafana
---
Restore the data from the backup:  
As backup user:
~~~
duplicity --no-encryption restore rsync://anhhungggg@backup.skaldr.io//home/anhhungggg/ /home/backup/restore/
~~~
root user:
~~~
cp -a /home/backup/backup/grafana/* /opt/docker/grafana/
chown -R 472:472 /opt/docker/grafana
~~~
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "grafana"
~~~

Exporters (nginx_exporter, node_exporter)
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "expt"
~~~

Influxdb (include Telegraf & Rsyslog)
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "influxdb"
~~~
Restore the data from the backup:  
As backup user:
~~~
duplicity --no-encryption restore rsync://anhhungggg@backup.skaldr.io//home/anhhungggg/ /home/backup/restore/
~~~
root user:
~~~
cp -a /home/backup/restore/influxdb/* /var/lib/influxdb/
~~~

HAproxy (include HAproxy exporter)
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "haproxy"
~~~

Keepalived (include Keepalived exporter)
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "keepalived"
~~~

For latest restore point:
---
~~~
sudo su - backup duplicity --force --no-encryption restore rsync://anhhungggg@backup.skaldr.io//home/anhhungggg/ /home/backup/restore/
~~~

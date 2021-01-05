Nginx
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "nginx"
~~~

MySQL
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
duplicity --force --no-encryption restore rsync://anhhungggg@backup.skaldr.io//home/anhhungggg/ /home/backup/restore/
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

Exporters
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "expt"
~~~

Telegraf
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "telegraf"
~~~

Rsyslog input for telegraf
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "rsyslog"
~~~

Influxdb
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

HAproxy
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "haproxy"
~~~

Keepalived
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

IT Infrastructure deployment with Ansible
---

IT Infrastructure provides:

Operating:
- DNS servers (masters and slaves): provisioned with Bind9
- Web servers: provisioned with Nginx
- Web application: provisioned with Docker
- Database servers: provisioned with MySQL
- High-Availability: provisioned with HAproxy
- Load-balancing: provisioned with Keepalived

Logging:
- Exporters running as services: MySQL exporter,Bind exporter,Nginx exporter,HAproxy exporter,Node exporter,Keepalived exporter
- Exporter metrics gathered by Prometheus
- Syslog gathered by InfluxDb
- Logging visualizationed by: grafana

Backup Server:
...

Instruction:

- Ansible Installation  
<https://docs.ansible.com/ansible/latest/installation_guide/index.html>
- Running playbook for full deployment (navigate to the playbook directory beforehand)
~~~
ansible-playbook infra.yaml
~~~
Some useful links about Ansible vault password and ansible.cfg file  
<https://docs.ansible.com/ansible/latest/user_guide/vault.html>  
<https://docs.ansible.com/ansible/latest/installation_guide/intro_configuration.html>

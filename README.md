## Node Exporter Ansible Role

[![CI](https://github.com/bilalcaliskan/node_exporter-ansible-role/workflows/CI/badge.svg?event=push)](https://github.com/bilalcaliskan/node_exporter-ansible-role/actions?query=workflow%3ACI)

Installs and configures [Node exporter](https://github.com/prometheus/node_exporter) to expose node metrics to Prometheus.

## Requirements

This role requires minimum Ansible version 2.4 and maximum Ansible version 2.9. You can install suggested version with pip:
```
$ pip install "ansible==2.9.16"
```

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: true`, or invoke the role in your playbook like:

```yaml
- hosts: all
  become: true
  roles:
    - role: bilalcaliskan.node_exporter
```

### Role Variables
See the default values in [defaults/main.yml](defaults/main.yml). You can overwrite them in [vars/main.yml](vars/main.yml) if neccessary or you can set them while running playbook.

> Please note that this role will ensure that `firewalld` systemd service on your servers are started and enabled by default. If you want to stop and disable `firewalld` service, please modify below variable as false when running playbook:  
> ```yaml  
> firewalld_enabled: false

## Dependencies

None

### Example Playbook File For Installation

```yaml
- hosts: all
  become: true
  roles:
    - role: bilalcaliskan.node_exporter
      vars:
        exporter_port: 9092
        install_node_exporter: true
        version: 1.0.1
```

You can also override default variables inside [vars/main.yml](vars/main.yml)*:
```yaml
version: 1.0.1
```

### Example Playbook File For `Ununinstallation`

```yaml
- hosts: all
  become: true
  roles:
    - role: bilalcaliskan.node_exporter
      vars:
        install_node_exporter: false
```

### License

MIT / BSD

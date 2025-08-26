# Pi Monitoring Ansible setup

[![CI][badge-gh-actions]][link-gh-actions]

This project installs my raspberry pi monitoring setup, available [here](https://github.com/rafael-c-alexandre/Docker-Raspberry-PI-Monitoring) on any raspberry pi.

## Installation

The recommend installation guide is as follows:

1. Ensure the Raspberry Pi has Pi OS installed and SSH running and reachable.
2. Get the Pi IP address or hostname through `ip a` (or any other network-related tool) or in the router UI.
3. Add the IP address/hostname in an inventory file such as `inventories/hosts.ini`.
4. Clone or download this repository to your local drive.
5. Run `ansible-galaxy install -r requirements.yml` inside this directory to install required Ansible roles and collections.
6. To prepare the ansible environment,
    - Change host in `inventories/hosts.ini` file.

8. In the root folder, run 
``` bash
ansible-playbook main.yml
``` 

## Overriding Defaults

You can override any of the defaults configured in `default.config.yml` by creating a `config.yml` file and setting the overrides in that file. For example, you can customize the wireguard ip addresses, interfaces and peers to be generated with something like:

```yaml
---
monitoring_root: /home/rafael/monitoring

grafana_port: 3000
prometheus_port: 9090

monitoring_internal_subnet: 172.20.0.0/16
docker_interface: docker0

```

Any variable can be overridden in `config.yml`; see the supporting roles' and documentation for a complete list of their available variables.


## Testing the Playbooks

This project is [continuously tested on GitHub Actions](https://github.com/rafael-c-alexandre/pi-monitoring-playbook/blob/main/.github/workflows/ci.yml).


License
-------

MIT

[badge-gh-actions]: https://github.com/rafael-c-alexandre/pi-monitoring-playbook/actions/workflows/ci.yml/badge.svg
[link-gh-actions]: https://github.com/rafael-c-alexandre/pi-monitoring-playbook/actions/workflows/ci.yml

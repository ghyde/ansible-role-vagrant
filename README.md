# Vagrant

Install [Vagrant][vagrant] on Fedora.

## Role Variables

### defaults/main.yml

| name                        | description                                      | type | default |
| --------------------------- | ------------------------------------------------ | ---- | ------- |
| vagrant_boxes               | List of Vagrant boxes to download                | List | []      |
| vagrant_plugins             | List of Vagrant plugins to install               | List | []      |
| vagrant_plugin_dependencies | List of RPM packages required by Vagrant plugins | List | []      |

### vars/main.yml

| name                     | description                   | type       | default   |
| ------------------------ | ----------------------------- | ---------- | --------- |
| dnsmasq_listen_address   | Dnsmasq's listening address   | IP Address | 127.0.0.1 |
| dnsmasq_listen_interface | Dnsmasq's listening interface | Interface  | lo        |

## Dependencies

- [ghyde.libvirt][libvirt_role]
- [ghyde.virtualbox][virtualbox_role]

## Example Playbook

```yaml
- hosts: workstations
  tasks:
  - import_role:
      name: vagrant
    vars:
      vagrant_boxes:
        - name: centos/7
          provider: libvirt
      vagrant_plugins:
        - landrush
      vagrant_plugin_dependencies:
        - dnsmasq
```

## License

MIT

[libvirt]: https://libvirt.org
[libvirt_role]: https://galaxy.ansible.com/ghyde/libvirt
[vagrant]: https://www.vagrantup.com/
[virtualbox]: https://www.virtualbox.org
[virtualbox_role]: https://galaxy.ansible.com/ghyde/virtualbox

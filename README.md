Ansible Role: Docker
====================

An Ansible Role that installs [Docker](https://www.docker.com) Community Edition & Enterprise Edition with docker-compose on Linux.

We want this role as simple, configurable and interoperable as possible.

Requirements
------------

Compliant with :
- Debian 8 (Jessie)
- Debian 9 (Stretch)

Other:
- Fact gathering should be allowed in ansible-playbook (By default)
- The role require the superuser privileges. The task should be used with remote_user root or with a sudo/su grant


Role Variables
--------------

Available variables with defaults values are defined in `defaults/main.yml`.

Modifiables variables and possible values are listed below :

```
# Docker options
docker_edition: 'ce'                                    # Default is 'ce' for Community Edition, set 'ee' for Entreprise Edition
docker_package: "docker-{{ docker_edition }}"           # Default is the latest version, set docker-{{ docker_edition }}-<VERSION>" for a specific version
docker_apt_release_channel: 'stable'                    # Default is take packages from Stable channel, set 'edge' for edge channel
docker_apt_repository: "deb https://download.docker.com/linux/{{ ansible_distribution|lower }} {{ ansible_distribution_release }} {{ docker_apt_release_channel }}"

# Docker Compose options
docker_compose_install: true                            # Set to false in order to uninstall docker compose
docker_compose_version: '1.22.0'                        # Docker-compose version
docker_compose_path: '/usr/local/bin/docker-compose'    # Update it for a custom docker-compose path

# Docker firewall options
docker_disable_iptables_management: false               # Set to true in order to disable iptables rules management by docker
docker_firewall_primary_if: 'eth0'                      # Set the default primary interface (with wan connection), or override rules_var

# Docker firewall rules variable designed to become a fact
docker_firewall_rules_var:
  - { chain: 'FORWARD',  in_if: '{{ docker_firewall_primary_if }}', out_if: 'docker0', policy: 'ACCEPT' }
  - { chain: 'FORWARD',  out_if: '{{ docker_firewall_primary_if }}', in_if: 'docker0', policy: 'ACCEPT' }
```

Dependencies
------------

none


Example Playbook
----------------

How to use the role in your ansible playbook.

    - name: Playbook Task to install docker role
      hosts: docker-servers (Group of servers on which you want to install docker)
      roles:
         - { role: hexanode.docker, tags: [ 'docker' ] }


ToDo
----

- Add tests
- Add CI Integration


License
-------

GPLv3


Author Information
------------------

This role is maintained by maximiliend. Issues and Merge Request are welcome.

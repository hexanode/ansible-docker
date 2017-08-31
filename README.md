# Ansible Role: Docker

An Ansible Role that installs [Docker](https://www.docker.com) on Linux.

## Requirements

Compliant with :
- Debian 8 (Jessie)
- Debian 9 (Stretch)

Fact gathering should be allowed in ansible-playbook (By default)

## Role Variables

Available variables with defaults values are defined in `defaults/main.yml`.

Modifiables variables and possible values are listed below :

- docker_edition: 'ce' (Community Edition) or 'ee' (Entreprise Edition)
- docker_package: "docker-{{ docker_edition }}" (Latest version) or "docker-{{ docker_edition }}-<VERSION>" (Specific version)
- docker_apt_release_channel: 'stable' (Take packages from Stable channel) or 'edge' (From Edge channel)

## Author Information

This role is maintained by maximiliend

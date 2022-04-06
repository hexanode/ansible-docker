Ansible Role: Docker
====================

An Ansible Role that installs [Docker](https://www.docker.com) Community Edition & Enterprise Edition with docker-compose on Linux.

We want this role as simple, configurable and interoperable as possible.

Requirements
------------

Compliant with :
- Ubuntu 20 (Focal Fossa)
- Debian 11 (Bullseye)
- Debian 10 (Buster)
- Debian 9 (Stretch)
- Debian 8 (Jessie)

Other:
- Fact gathering should be allowed in ansible-playbook (By default)
- The role require the superuser privileges. The task should be used with remote_user root or with a sudo/su grant

Role Variables
--------------

Available variables with defaults values are defined in `defaults/main.yml`.

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

License
-------

GPLv3

Author Information
------------------

This role is maintained by maximiliend. Issues and Merge Request are welcome.

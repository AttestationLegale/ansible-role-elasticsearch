# Ansible Role: elasticsearch

[![Build Status](https://travis-ci.org/AttestationLegale/ansible-role-elasticsearch.svg?branch=master)](https://travis-ci.org/AttestationLegale/ansible-role-elasticsearch) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-elasticsearch-blue.svg)](https://galaxy.ansible.com/AttestationLegale/elasticsearch/)

The elasticsearch role allows you to create dedicated instances running under a specified user/group.

This role performs the following tasks:

  - create /home/{{ user }}/etc/php5/fpm/php.ini
  - create /home/{{ user }}/etc/php5/fpm/elasticsearch.conf
  - create /home/{{ user }}/etc/php5/fpm/env.conf
  - create /home/{{ user }}/etc/php5/fpm/pool.d/{{ user }}.conf
  - create /home/{{ user }}/usr/lib/php5/php5-fpm-checkconf
  - create /home/{{ user }}/usr/lib/php5/php5-fpm-reopenlogs
  - create /home/{{ user }}/usr/lib/php5/sessionclean
  - create /etc/cron.d/php5-{{ user }} (cronjob calling /home/{{ user }}/usr/lib/php5/sessionclean for sessions cleanup)
  - create /etc/logrotate.d/php5-fpm-{{ user }} (to rotate php5-fpm logs for this instance)
  - create /lib/systemd/system/php5-fpm-{{ user }}.service (so that your instance can be managed with systemctl)


## Requirements

### User

The user hosting the elasticsearch instance must exist on the target system.

You can use [AttestationLegale.skel](https://galaxy.ansible.com/AttestationLegale/skel/) and [AttestationLegale.users](https://galaxy.ansible.com/AttestationLegale/users/) to create all the necessary stuff before calling elasticsearch role.

## Role Variables

For a complete list of variables, see `default/main.yml`.

    elasticsearch_instances: []

## Dependencies

None

## Example Playbook

```yaml
---
  - hosts: all
    roles:
      - elasticsearch
    vars:
      - elasticsearch_instances:
        - owner: foo
          group: bar
          home: /home/foo
          version: 2.1.0
```

## License

MIT / BSD

## Author Information

This role was created in 2016 by [ALG](https://www.attestationlegale.fr)

# Ansible Role: elasticsearch

[![Build Status](https://travis-ci.org/AttestationLegale/ansible-role-elasticsearch.svg?branch=master)](https://travis-ci.org/AttestationLegale/ansible-role-elasticsearch) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-elasticsearch-blue.svg)](https://galaxy.ansible.com/AttestationLegale/elasticsearch/)

The elasticsearch role allows you to create dedicated instances running under a specified user/group.

This role performs the following tasks:

  - download and exrtact elasticsearch in /home/{{ user }}/elastcsearch-{{ version }}
  - push /home/{{ user }}/elastcsearch-{{ version }}/config/elasticsearch.yml
  - push /home/{{ user }}/.es-env
  - push /home/{{ user }}/bin/els # startup script


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
          config: []
```

## License

MIT / BSD

## Author Information

This role was created in 2016 by [ALG](https://www.attestationlegale.fr)

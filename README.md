postgresql
============

[![Build Status](https://travis-ci.org/andrelohmann/ansible-role-postgresql.svg?branch=master)](https://travis-ci.org/andrelohmann/ansible-role-postgresql)

Use this role to provision postgresql

Requirements
------------

This role requires ubuntu

Role Variables
--------------

The default set of variables can be used to provision databses, users and privileges and set the listen_addresses

    postgresql_listen: "0.0.0.0"
    postgresql_databases:
    - name: test
      encoding: UTF-8
      state: present
      schemas:
      - name: schemaone
        state: present
      - name: schematwo
        state: present
    postgresql_users:
    - name: testuser
      password: 1234test
      state: present
      privileges:
      - database: test
        privs: "All"
        state: present
      hosts:
      - cidr: 0.0.0.0/0
        database: test
        state: present



Example Playbook
----------------

    - hosts: postgresql
      become: yes
      roles:
         - { role: andrelohmann.postgresql }

License
-------

MIT

Author Information
------------------

https://github.com/andrelohmann

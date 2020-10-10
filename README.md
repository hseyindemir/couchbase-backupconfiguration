Role Name
=========

cbbackup-configurator


Role Description
=========

This role aimed to configure a backup schedule to a remote server for a Couchbase server. By default, this role keeps daily backups. Backups older than 1 day is removed automatically.
Attention :
  - The role schedules backup jobs into crontab and job runs every hour in a minute defined as period in variable section.
  - The role does not able to keep backups older than 1 day.


Role Dependencies
=========

  - Couchbase Server >= 6.5.1

Role Variables
--------------

Markdown | Less | Pretty
--- | --- | ---
Variable Name | Default Value | Description | Type
cluster_name | test | logical cluster name | string/text
username | test | couchbase username to backup | string/text
password | test | couchbase password to backup| string/text
server_address | test | couchbase server to backup | ip
mountpoint | /backup | root directory for backup | string
period | 10 | the minute that each backup will be started every hour | integer

Example Playbook
----------------
```
- hosts: backup_server
  become: true
  roles: 
    - cbbackup-configurator
  vars:
    cluster_name: cluster-name-addr
    username: cluster-username
    password: cluster-pass
    server_address: server-ip-cb
    period: 30
    mountpoint: /cb-data
```

Author Information
------------------

Hüseyin Demir.

ovv.nfs
=======

[![Build Status](https://travis-ci.org/ovv/ansible-role-nfs.svg?branch=master)](https://travis-ci.org/ovv/ansible-role-nfs)

Ansible role to install and configure NFS.

Installation
------------

To install this roles clone it into your roles directory.

```bash
$ git clone https://github.com/ovv/ansible-role-nfs.git ovv.nfs
```

If your playbook already reside inside a git repository you can clone it by using git submodules.

```bash
$ git submodule add -b master https://github.com/ovv/ansible-role-nfs.git ovv.nfs
```

Role Variables
--------------

* `nfs_port`: NFS listen port (default to `34433`). 
* `ufw_enabled`: Open ports in UFW (default to `True`).

* `nfs_exports`: Dict of NFS exports. Folder path as key:
    * `host`: host authorized to access the share.
    * `config`: Configuration of the share (default to `['rw','sync','no_subtree_check']`).


Example Playbook
----------------

```yml
- hosts: nfs
  tags:
    - nfs
  roles:
    - ovv.nfs
  vars:
    nfs_exports:
        /var/nfs/foo:
            host: 8.8.8.8
            config:
                - rw
                - sync
```

License
-------

MIT

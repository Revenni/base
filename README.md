revenni.base
=========

Ansible role providing minimum configuration for Ubuntu machines.  Unattended updates and postfix configuration for external relay host.

[![Platforms](http://img.shields.io/badge/platforms-ubuntu-lightgrey.svg?style=flat)](#)
[![Licence](https://img.shields.io/badge/Licence-MIT-blue.svg)](https://tldrlegal.com/license/mit-license)

Requirements
------------

* None

Role Variables
--------------

### Unattended update variables
* ```unattended_enabled``` (1) - enable unattended upgrades
* ```unattended_email``` (emailxyz@domain.com) - email address to send errors to
* ```unattended_email_errors_only``` (true) - only email errors
* ```unattended_reboot``` (false) - reboot automatically?  bool.
* ```unattended_reboot_time``` (21:00) - time to reboot machine
* ```unattended_remove_deps``` (true) - automatically remove unused dependencies? bool.

### Postfix variables
* ```postfix_enabled``` (0) - enable postfix?
* ```postfix_relayhost``` ([smtp.gmail.com]:587) - mailserver to connect to
* ```postfix_interfaces``` (127.0.0.1) - only used for system relaying
* ```postfix_protocols``` (ipv4) - ipv4
* ```postfix_sasl_username``` (relay@somedomain.com) - username for sasl auth
* ```postfix_sasl_password``` (vault string) - replace with output of ```echo -n "password" | ansible-vault encrypt_string --stdin-name 'postfix_sasl_password'```


Dependencies
------------

* None

Example Playbook
----------------

    - hosts: all
      become: true
      roles:
         - { role: revenni.base, tags: base }

License
-------

MIT

Author Information
------------------
* [Vince Hillier](https://revenni.com) | [@email](mailto:vince@revenni.com) | [twitter](https://twitter.com/vincedotca)

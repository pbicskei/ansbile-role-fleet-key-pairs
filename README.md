Role Name
=========

This role allows a process to generate ssh key-pairs for use with remote hosts and services.

What it will do:

* Generate a local key-pair for `user`@`service_domain` in `target_directory`
* Place a managed block for this domain in `~/.ssh/config`
* (Optional) ssh-add `<key_pair_path>` file credentials into key-store.

Requirements
------------

The role should be allowed to generate new `users`, `directories`, `key-pairs`.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yml
---
- hosts: localhost
  connection: local

  vars:
    user_group: staff
    ssh_user: "{{ ansible_env.USER }}"
    ssh_file_path: "{{ lookup('env', 'PWD') }}/.ssh"

    ssh_synced_state: present
    
    p3t_input:
      - { ssh_service: "root" ,ssh_key_domain: "example.com", ssh_key_type: "rsa", ssh_key_bits: 4096, ssh_key_path: "ansible/local", ssh_passphrase: "", state: "{{ ssh_synced_state }}" }
      - { ssh_service: "root" ,ssh_key_domain: "example.com", ssh_key_type: "rsa", ssh_key_bits: 4096, ssh_key_path: "ansible/local/user", ssh_passphrase: "", state: "{{ ssh_synced_state }}" }
      - { ssh_service: "root" ,ssh_key_domain: "example.com", ssh_key_type: "rsa", ssh_key_bits: 4096, ssh_key_path: "ansible/local/service", ssh_passphrase: "", state: "{{ ssh_synced_state }}" }
   
  roles:
    - role: pbicskei.fleet_key_pairs
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).

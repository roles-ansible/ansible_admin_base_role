 ansible admin base role
================

Ansible role to define default admin permissions on linux servers



 Dependencies
-----------------
+ [do1jlr.sshd](https://galaxy.ansible.com/do1jlr/sshd)
+ [do1jlr.auth](https://galaxy.ansible.com/do1jlr/auth)
+ [do1jlr.users](https://galaxy.ansible.com/do1jlr/users)
+ a filestore with your public ssh key collection.


 Usage
-------
In this ansible role default admin accesses are defined, which can be used for a large number of ansible managed servers.
The variable ``default_admins`` defines who is allowed to log in with which ssh key as which user by default and that he got sudo permissions.
So if you want to use this role for yourself, it might make sense to fork it and adjust the default variables.

### Customizations for hosts or groups
For each host or group of your ansible inventory, the list of admins can be extended with the following variable:
```yaml
# Add you and the ssh key you@example.org to a server
local_admins:
  - name: you
    pubkeys:
      - you@example.org
```

Unprivileged users can also be added in this way:
```yaml
# add unpriviledged users foo and bar
local_accounts:
  - foo
  - bar
```

 Good to know
---------------

+ By default, the [do1jlr.sshd](https://github.com/roles-ansible/ansible_role_sshd.git) role only allow the login of **defined users**.
+ By default, the [do1jlr.sshd](https://github.com/roles-ansible/ansible_role_sshd.git) role only allow the **login with [ed25519](https://de.wikipedia.org/wiki/Curve25519) SSH Keys**. Eliptic curve ssh key pairs can be created using ``ssh-keygen -t ed25519``.
+ The [do1jlr.auth](https://github.com/roles-ansible/ansible_role_auth.git) role is very picky about the filenames in which the public ssh keys must be stored. Better have a look at their readme.

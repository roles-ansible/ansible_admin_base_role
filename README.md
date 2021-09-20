 ansible admin base role
================

Ansible role to define default admin permissions on linux servers.

 Dependencies
-----------------
This role uses the following ansible roles, which must be available in your ansible playbook:

- [do1jlr.users](https://github.com/roles-ansible/ansible_role_users.git) *create user and manage sudoers*
- [do1jlr.auth](https://github.com/roles-ansible/ansible_role_auth.git) *deploy ssh pubkeys*
- [do1jlr.sshd](https://github.com/roles-ansible/ansible_role_sshd.git) *configure sshd*

A collection of ssh keys is also needed. These must be located in the ``ssh_public_keys`` folder, for example.
*In the following example the 'files/ssh_public_keys/' folder contains the following files with ssh public key for ``alice``, ``bob`` and two for ``eve``:*
```
alice_ed25519.pub
bob_ed25519.pub
eve@device1_ed25519.pub
eve@device2_ed25519.pub
```

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
+ The following two ansible roles fit very good to this role. Maybe you want to use them too?
  - [do1jlr.base](https://github.com/roles-ansible/ansible_role_base.git) *install some useful packages*
  - [do1jlr.dotfiles](https://github.com/roles-ansible/ansible_role_dotfiles) *deploy some fancy dotfiles*

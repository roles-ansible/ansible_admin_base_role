 ansible admin base role
================

Ansible role to define default admin permissions on linux servers



 Dependencies
-----------------
+ [do1jlr.sshd](https://galaxy.ansible.com/do1jlr/sshd)
+ [do1jlr.auth](https://galaxy.ansible.com/do1jlr/auth)
+ [do1jlr.users](https://galaxy.ansible.com/do1jlr/users)


 Usage
-------
In this ansible role standard user and admin accesses are defined, which can be used for a large number of ansible managed servers.
The variable ``default_admins`` defines who is allowed to log in with which ssh key as which user by default. And if he also gets sudo permissions.
So if you want to use this role for yourself, it might make sense to fork it and adjust the default variables.

### Customizations for hosts or groups


```yaml
# Add you and the ssh key you@example.org to a server
local_admins:
  - name: you
    pubkeys:
      - you@example.org
```

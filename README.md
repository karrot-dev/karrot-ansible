# bath.social server setup

This configures the server with the basics of:
1. user accounts and ssh keys
2. security hardening (via https://github.com/konstruktoid/ansible-role-hardening)
3. installing enough stuff for co-op cloud to work (https://docs.coopcloud.tech/)

## 1. User accounts

```
# first time, before accounts created
ansible-playbook users.yml -u root

# later, can use your own account
ansible-playbook users.yml
```

## 2. Server hardening

Note: make sure you installed the users first, as after this you'll need to login as one of those, not root.

```
ansible-galaxy install -r galaxy-requirements.yml
ansible-playbook harden.yml
```

## 3. rest of setup

```
ansible-playbook setup.yml
```

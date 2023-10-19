# karrot ansible server setup

This configures the server with the basics of:
1. user accounts and ssh keys
2. security hardening (via https://github.com/konstruktoid/ansible-role-hardening)
3. installing enough stuff for co-op cloud to work (https://docs.coopcloud.tech/)

First, create a python virtualenv (recommended, but not essential):

```
python -m venv .venv
```

(if you're using [rtx](https://github.com/jdx/rtx) it'll setup the venv for you automatically as we have a `.rtx.toml` config file)

Then, install python deps and galaxy deps:

```
pip install -r requirements.txt
ansible-galaxy install -r galaxy-requirements.yml
```

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
ansible-playbook harden.yml
```

## 3. Rest of the setup

```
ansible-playbook setup.yml
```

You're then ready to start using abra with co-op cloud, some useful resources:
- https://docs.coopcloud.tech/operators/tutorial/#server-setup
- https://docs.karrot.world/self-hosting.html
- https://git.coopcloud.tech/coop-cloud/karrot

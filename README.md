## Intro to Ansible

This is a super introductory repo on using ansible.

## Prerequisites

You must already have instances up and running to use ansible.
The connection is always done through `ssh`, and ansible uses
python both in your machine and in the target machines to do stuff.

---

### The inventory file

The inventory file contains the instances than you can call and configure through ansible. They are typically divided into different groups.

### About ssh-keys

Since ssh-keys are sort of a "newer" thing, the way we specify them in the inventory looks a bit weird, but super doable:

```
[databases]
db01 ansible_host=34.203.245.33 ansible_user=ubuntu ansible_ssh_private_key_file=./ansible-instances.pem
```

---

### Ad-hoc commands

You can try individual commands with the `ping` module:
```bash
ansible all -m ping -vv 
```

Note: the `-vv` is just extra verbose (extra information about what's happening).

---

### Using Playbooks

Playbooks are the standard for Ansible, because you want to be able to reproduce what you're configuring.

Try out the palybooks in this repo:
```
ansible-playbook basic-playbook.yml
```

But make sure to uninstall afterwards:

```bash
ansible-playbook teardown-playbook.yml
```

---

If you want to use your own instances, you absolutely need to put public ssh keys in the instances. You can create them locally, then paste them (the public ones) in the `~/.ssh/authorized_keys` file.

---

It's time for you to start this!
Do you have the pre-requisites?

- 2-3 working machines (that have port 22 exposed)
- your `ansible.cfg` file
- your `inventory.ini` file
- a working ssh private key
- a module you want to use (with an adhoc command or playbook)

🚀 Good Luck and Have fun! 🚀
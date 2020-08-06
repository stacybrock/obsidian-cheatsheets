# Ansible Cheatsheet

## Ad-hoc Commands

**Run on all hosts in inventory:**
```
$ ansible all -i inventoryfile -m ping
$ ansible all -i inventoryfile -m command -a 'uptime'
```

**Run on a specific group in inventory:**
```
$ ansible dev -i inventory/dev -m ping
```

### Get Facts For a Host

```
$ ansible dev -i inventory/dev -m setup
```

## Playbook

```
$ ansible-playbook -i inventoryfile site.yml
$ ansible-playbook -i inventoryfile site.yml --list-tasks
$ ansible-playbook -i inventoryfile site.yml --list-hosts
```

## Connecting to EC2 Instances

**Configure host in inventory:**
```
54.188.154.252 ansible_user=ec2-user ansible_ssh_private_key_file=~/.ssh/your.pem ansible_become=yes ansible_become_method=sudo
```

## Using Vault

```
$ ansible-playbook -i inventoryfile site.yml --vault-password-file vault_pass.txt
```

## Debugging Playbooks

- Keep temp ansible command files on the remote by setting the environment variable `ANSIBLE_KEEP_REMOTE_FILES=1`
- `--start-at-task` will run the playbook from the given task
- `--step` will step through the execution of each task
- `--extra-vars "some_variable=1.23.45 other_variable=foo"` to pass params directly on the commandline

### Troubleshooting SSH Issues

Edit `$HOME/.ansible.cfg` and add an `ssh_connection` section. Set `ssh_args` to empty. This will disable ControlMaster/ControlPersist, which won't resolve the SSH problem but does produce better debug output from SSH.

```
[ssh_connection]
ssh_args=''
```

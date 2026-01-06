# Focus-ansible

Ansible playbooks to install and configure Docker on a VM and run Docker Compose workloads.

## Requirements
- Ansible on your control machine
- SSH access to the VM (sudo privileges)

## Quick start
1) Edit `inventory/hosts` and set your VM IP/hostname and user.
2) Optional: edit `group_vars/docker_hosts.yml` to set `docker_users` and daemon config.
3) Run:

```bash
ansible-playbook site.yml
```

## Deploy Focus app
Use the provided deploy playbook to sync the local Focus project to the VM and run Docker Compose.

1) Set `app_src` in `group_vars/docker_hosts.yml` to the local path of the Focus project.
2) Run:

```bash
ansible-playbook deploy_focus.yml
```

## Variables
Defined in `group_vars/docker_hosts.yml` or per-host/group.

- `docker_users`: list of users to add to the `docker` group
- `docker_daemon_config`: dict for `/etc/docker/daemon.json`
- `docker_package_state`: install state for docker packages (default: `present`)

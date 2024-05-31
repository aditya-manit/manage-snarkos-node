# Manage SnarkOS Node Remotely

Ansible project to manage snarkOS as a systemd service on remote servers.

## Project Structure

```
snarkos-ansible/
├── inventories/
│   └── hosts
├── playbooks/
│   ├── setup.yml
│   ├── install.yml
│   ├── upgrade.yml
│   ├── start.yml
│   ├── stop.yml
│   └── logs.yml
├── roles/
│   └── snarkos/
│       ├── tasks/
│       │   ├── main.yml
│       │   ├── install_dependencies.yml
│       │   ├── configure_firewall.yml
│       │   ├── install_snarkos.yml
│       │   ├── upgrade_snarkos.yml
│       │   ├── manage_service.yml
│       ├── handlers/
│       │   └── main.yml
│       ├── vars/
│       │   └── main.yml
│       └── templates/
├── vars/
│   └── snarkos_vars.yml
├── ansible.cfg
└── README.md
```

## Usage

### Setup Environment

Run the setup playbook to install dependencies and configure the environment.

```sh
ansible-playbook playbooks/setup.yml
```

### Install snarkOS

Run the install playbook to install snarkOS.

```sh
ansible-playbook playbooks/install.yml
```

### Upgrade snarkOS

Run the upgrade playbook to upgrade snarkOS to the latest version.

```sh
ansible-playbook playbooks/upgrade.yml
```

### Start snarkOS Service

Run the start playbook to start the snarkOS service.

```sh
ansible-playbook playbooks/start.yml
```

### Stop snarkOS Service

Run the stop playbook to stop the snarkOS service.

```sh
ansible-playbook playbooks/stop.yml
```

### Show Logs

Run the logs playbook to show the last 100 lines of the snarkOS log.

```sh
ansible-playbook playbooks/logs.yml
```

## Files and Directories

### Inventories

**File:** `inventories/hosts`

Defines the hosts and groups of hosts upon which commands, modules, and tasks in a playbook operate.

### Playbooks

- **setup.yml**: Sets up the initial environment, installs necessary dependencies, and prepares the server.
- **install.yml**: Installs snarkOS on the remote server.
- **upgrade.yml**: Upgrades snarkOS to the latest version.
- **start.yml**: Starts the snarkOS service.
- **stop.yml**: Stops the snarkOS service.
- **logs.yml**: Shows the last 100 lines of the snarkOS log.

### Roles

**Role:** `snarkos`

- **tasks/main.yml**: Main task file that includes other task files.
- **tasks/install_dependencies.yml**: Installs required system packages and sets up the environment.
- **tasks/configure_firewall.yml**: Configures firewall rules for snarkOS.
- **tasks/install_snarkos.yml**: Checks out snarkOS from Git, builds it, and moves the binary to the appropriate location.
- **tasks/upgrade_snarkos.yml**: Stops the snarkOS service, updates the repository, rebuilds snarkOS, and starts the service again.
- **tasks/manage_service.yml**: Manages the snarkOS service (start, stop, restart).
- **handlers/main.yml**: Handlers to restart snarkOS when needed.
- **vars/main.yml**: Default variables for the role.

### Variables

**File:** `vars/snarkos_vars.yml`

Contains variables used in the playbooks and roles.

### Configuration

**File:** `ansible.cfg`

Ansible configuration file to set default options.

---

By following this structure and using the provided playbooks, you can effectively manage the snarkOS service on remote servers. Each playbook addresses a specific task, ensuring modularity and ease of management.
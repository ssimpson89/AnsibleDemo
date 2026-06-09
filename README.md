# AnsibleDemo

Standard Ansible project scaffold with a reusable role and a playbook that installs Nginx.

## Project Structure

.
|-- .github/
|   `-- workflows/
|       `-- ansible-lint.yml
|-- ansible.cfg
|-- group_vars/
|   `-- all.yml
|-- playbooks/
|   `-- install_nginx.yml
|-- requirements.yml
`-- roles/
    `-- nginx/
        |-- defaults/
        |   `-- main.yml
        |-- handlers/
        |   `-- main.yml
        |-- meta/
        |   `-- main.yml
        `-- tasks/
            `-- main.yml

## Quick Start

1. Install required collections:

   ```bash
   ansible-galaxy collection install -r requirements.yml
   ```

2. Run against localhost:

   ```bash
   ansible-playbook -i "localhost," -c local playbooks/install_nginx.yml
   ```

3. Run against a remote host directly (example):

   ```bash
   ansible-playbook -i "203.0.113.10," -u ubuntu --become playbooks/install_nginx.yml
   ```

## Notes

- The role uses package and service modules for portability.
- Since no inventory file is included, pass hosts with `-i` when running playbooks.
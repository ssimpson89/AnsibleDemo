# AnsibleDemo

Standard Ansible project scaffold with inventories, reusable roles, and a playbook that installs Nginx.

## Project Structure

.
|-- .github/
|   `-- workflows/
|       `-- ansible-lint.yml
|-- ansible.cfg
|-- group_vars/
|   `-- all.yml
|-- inventories/
|   |-- production/
|   |   `-- hosts.yml
|   `-- staging/
|       `-- hosts.yml
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

1. Update target hosts in the inventory files under `inventories/`.
2. Install required collections:

	```bash
	ansible-galaxy collection install -r requirements.yml
	```

3. Run the Nginx install playbook (staging example):

	```bash
	ansible-playbook -i inventories/staging/hosts.yml playbooks/install_nginx.yml
	```

4. Run the Nginx install playbook (production example):

	```bash
	ansible-playbook -i inventories/production/hosts.yml playbooks/install_nginx.yml
	```

## Notes

- The role currently targets Debian-family hosts and uses package and service modules for portability.
- `ansible.cfg` defaults to the staging inventory; override with `-i` as needed.
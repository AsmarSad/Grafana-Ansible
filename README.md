# Grafana-Ansible
This project automates the creation of a DigitalOcean droplet, configures it with SSH, and installs Grafana with Nginx as a reverse proxy. 
## Project Structure:
```
.
├── ansible.cfg
├── main.yml
├── README.md
├── roles
│   ├── configure_grafana
│   │   ├── defaults
│   │   │   └── main.yml
│   │   ├── handlers
│   │   │   └── main.yml
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── templates
│   │       ├── grafana.conf.j2
│   │       └── nginx.conf.j2
│   └── provision_droplet
│       ├── defaults
│       │   └── main.yml
│       └── tasks
│           └── main.yml
└── secrets.yml
```
## secrets.yml
Sensitive data such as `do_token` and `ssh_pub_key_path` are securely stored using Ansible Vault.

```
ansible-vault create secrets.yml
```
Inside secrets.yml:

```
do_token: "<digital_ocean_token>"
ssh_pub_key_path: "/path/to/key/file"
```
## First Task: Creating Droplets

✅ Uploads SSH key to DigitalOcean.

✅ Creates a droplet using the specified configuration.

✅ Waits for the droplet to be reachable.

✅ Adds the droplet to Ansible inventory dynamically.

## Second Task: Configuring Grafana

✅ Updates system packages.

✅ Installs Grafana and required dependencies.

✅ Configures Nginx as a reverse proxy for Grafana.

✅ Starts and enables the Grafana service.

## Result
Grafana is accessible on port 80.
# selfserv Project

## Purpose

The selfserv project is a suite of ansible playbooks to provision and manage a home email stack using a cloud gateway to provide a static ip. Currently, The gateway vpn connection is operational, but it only serves a dummy web page.

## Prerequisites

To run this project, you need to have the following software installed:
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

To easily use a VM as your home server, you also need the following:
- [Vagrant](https://www.vagrantup.com/downloads)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (or another Vagrant-compatible provider)

## Setup and Usage

### Step 1: Clone the Repository

Clone this repository to your local machine using the following command:

```bash
git clone <repository_url>
```

### Step 2: Navigate to the Project Directory

Go to the project directory:

```bash
cd selfserv
```

### Step 3: Create the `secrets.yml` File

Create a `secrets.yml` file in the `secrets` directory to store sensitive information. This file should contain the necessary variables for your setup. Here is a template:

```yaml
---
# filepath: secrets/secrets.yml
vpn_psk: <generate with "openssl rand -base64 32">
aws_access_key: <YOUR_AWS_ACCESS_KEY>
aws_secret_key: <YOUR_AWS_SECRET_KEY>
aws_subnet_id: <YOUR_AWS_SUBNET>
aws_region: <YOUR_AWS_REGION>
aws_security_group: <YOUR_AWS_SECURITY_GROUP>
aws_public_ip: <YOUR_ELASTICIP_STATIC_IP_ADDRESS>
```

### Step 4: Start the Vagrant Environment

Start the Vagrant environment, which will set up the virtual machines according to the configuration in the `Vagrantfile`:

```bash
vagrant up
```

## Playbooks

The project includes the following Ansible playbooks:

1. `playbook.yml` - The main playbook that sets up everything, running the other playbooks.
1. `aws.yml` - Spins up an aws ec2 instance for gateway and adds it to the ansible inventory.
2. `gateway.yml` - Configures the gateway (vpn connection and firewall).
3. `server.yml` - Configures the server (vpn connection and web services).

## Contributing

Contributions are welcome! Please submit a pull request or open an issue to discuss any changes.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Acknowledgments

- The [Vagrant](https://www.vagrantup.com/) and [Ansible](https://www.ansible.com/) teams for their excellent tools.

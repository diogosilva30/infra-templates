# Packer Templates for Proxmox
This folder contains various sub-folders, each with a Packer VM template for Proxmox. These templates allow you to easily create new virtual machines on Proxmox based on a pre-configured image.

## Requirements
To use these templates, you'll need to install [Packer](https://developer.hashicorp.com/packer/tutorials/docker-get-started/get-started-install-cli).

## Getting started

- Clone this repository to your local machine using `git clone https://github.com/diogosilva30/infra-templates`.
- Navigate to the packer-proxmox folder.

## Building a VM template
To build a virtual machine using one of these templates, follow these steps:

1. Edit the credentials.pkr.hcl file with your proxmox URL and API credentials.
You can create an API token in the Proxmox web interface by going to "Datacenter" > "Permissions" > "API Tokens" and clicking "Add".

2. Open the Packer template file and `http/user-data` file and carefully review the variables and customize them to your needs (`ssh_username`, `ssh_private_key_file`, `ssh_authorized_keys` , etc...)

3. Validate the Packer template using:

```sh
packer validate -var-file="creedentials.pkr.hcl" ./ubuntu-server-jammy-docker/ubuntu-server-jammy-docker.pk.hcl # Replace this folder and file with your desired VM template
```

1. Build the virtual machine image template using:

```sh
packer build -var-file="creedentials.pkr.hcl" ./ubuntu-server-jammy-docker/ubuntu-server-jammy-docker.pk.hcl# Replace this folder and file with your desired VM template
```

This will create a new virtual machine on Proxmox based on the pre-configured image.

That's it! You should now have a new virtual machine template on your Proxmox host!
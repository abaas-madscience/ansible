# 🚀 VM Provisioning with Ansible

Welcome to the ultimate VM provisioning adventure! This project automates the creation of virtual machines (VMs) using Ansible and libvirt. It sets up the environment, generates cloud-init configuration files, creates VM disks, and launches the VMs. Ready to dive in? Let's go! 🌟

## Prerequisites

Before we embark on this journey, make sure you have the following tools installed:

- Ansible 🛠️
- libvirt 🖥️
- qemu-img 💾
- genisoimage 📀

## Setup

1. Clone the repository and navigate to the directory:
    ```sh
    git clone <repository-url>
    cd <repository-directory>
    ```

2. Install the required Ansible roles:
    ```sh
    ansible-galaxy install -r requirements.yml
    ```

3. Define your inventory and variables in `inventory/hosts` and `group_vars/all.yml`.

## Usage

Ready to provision some VMs? Run the playbook:
```sh
ansible-playbook -i inventory -K
```

Need to tear down the VMs? No problem:
```sh
ansible-playbook -i inventory --tags vm_teardown -K
```

## Playbook Structure

Here's a quick tour of the playbook structure:

- `roles/vm_provision/tasks/provision_vm.yml`: Main task file for provisioning VMs.
- `roles/vm_provision/tasks/pre_vm_tasks.yml`: Pre-tasks for preparing the SSH environment.
- `templates/`: Directory containing Jinja2 templates for cloud-init configuration.

## Variables

Customize your VM setup with these variables:

- `cloud_init_dir`: Directory for cloud-init files.
- `cloud_image_path`: Path to the base cloud image.
- `node`: Dictionary containing VM-specific information (name, mac, etc.).
- `virtual_memory`: Amount of memory for the VM.
- `virtual_cpu`: Number of CPUs for the VM.
- `virtual_network`: Network to attach the VM to.

## Error Handling

Don't worry if something goes wrong! The playbook includes error handling to clean up resources if VM provisioning fails.

## A Better Way? 🤔

Looking for a more streamlined and powerful way to deploy VMs and clusters? Check out these awesome projects:

- **Terraform Libvirt K3s Cluster**: [terraform-ansible-lab](https://github.com/abaas-madscience/terraform-ansible-lab) - Use Terraform to create VMs and then deploy a cluster using Ansible.
- **Ansible K3 Rancher**: [ansible-k3-rancher](https://github.com/abaas-madscience/ansible-k3-rancher) - Deploy a Kubernetes cluster with Rancher using Ansible.

## License

This project is licensed under the MIT License. Enjoy your VM provisioning adventure! 🎉
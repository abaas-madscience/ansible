# VM Provisioning with Ansible

This project automates the provisioning of virtual machines (VMs) using Ansible and libvirt. It prepares the environment, generates cloud-init configuration files, creates VM disks, and starts the VMs.

## Prerequisites

- Ansible
- libvirt
- qemu-img
- genisoimage

## Setup

1. Clone the repository:
    ```sh
    git clone <repository-url>
    cd <repository-directory>
    ```

2. Install required Ansible roles:
    ```sh
    ansible-galaxy install -r requirements.yml
    ```

3. Define your inventory and variables in `inventory/hosts` and `group_vars/all.yml`.

## Usage

Run the playbook to provision VMs:
```sh
ansible-playbook -i inventory -K
```

Run the playbook to tear down VMs:
```sh
ansible-playbook -i inventory --tags vm_teardown -K
```

## Playbook Structure

- `roles/vm_provision/tasks/provision_vm.yml`: Main task file for provisioning VMs.
- `roles/vm_provision/tasks/pre_vm_tasks.yml`: Pre-tasks for preparing the SSH environment.
- `templates/`: Directory containing Jinja2 templates for cloud-init configuration.

## Variables

- `cloud_init_dir`: Directory for cloud-init files.
- `cloud_image_path`: Path to the base cloud image.
- `node`: Dictionary containing VM-specific information (name, mac, etc.).
- `virtual_memory`: Amount of memory for the VM.
- `virtual_cpu`: Number of CPUs for the VM.
- `virtual_network`: Network to attach the VM to.

## Error Handling

The playbook includes error handling to clean up resources if VM provisioning fails.

## License

This project is licensed under the MIT License.
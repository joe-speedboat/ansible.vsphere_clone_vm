# joe-speedboat.vsphere_clone_vm

This role clones a VM from a template on a vSphere environment.

## Requirements

- Python packages:
  - pip
  - setuptools
  - [vsphere-automation-sdk-python](https://github.com/vmware/vsphere-automation-sdk-python)
- Ansible collection:
  - community.vmware

## Role Variables

The following variables are used in this role:

- `vcenter_api_url`: The FQDN of the vCenter server.
- `vcenter_username`: The username to authenticate with the vCenter server.
- `vcenter_password`: The password to authenticate with the vCenter server.
- `datacenter_name`: The name of the datacenter in vCenter.
- `cluster_name`: The name of the cluster in vCenter.
- `template_name`: The name of the VM template to clone.
- `vm_name`: The name of the new VM.
- `vm_folder`: The folder where the new VM will be created.
- `vm_network`: The network to connect the new VM to.
- `vm_memory`: The memory size of the new VM.
- `vm_disk_gb`: The disk size (in GB) of the new VM.
- `num_cpus`: The number of CPUs for the new VM.
- `scsi_type`: The SCSI controller type for the new VM.
- `datastore_name`: The datastore where the new VM will be created.
- `vm_power_up`: Whether to power up the new VM after creation.
- `vm_post_setup_template`: The template file containing the commands to run on the new VM after creation.
- `vm_username`: The username to authenticate with the new VM.
- `vm_password`: The password to authenticate with the new VM.
- `validate_certs`: Whether to validate the vCenter server's certificate.
- `datastore_check_size`: If set to true, it checks if the datastore has twice the VM size of free space left.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: localhost
  roles:
    - joe-speedboat.vsphere_clone_vm
  vars:
    vcenter_api_url: "vcenter.example.com"
    vcenter_username: "your_username"
    vcenter_password: "your_password"
    datacenter_name: "datacenter_name"
    cluster_name: "cluster_name"
    template_name: "template_name"
    vm_name: "new_vm_name"
    vm_folder: "vm_folder"
    vm_network: "network_name"
    vm_memory: 1024
    vm_disk_gb: 50
    num_cpus: 2
    scsi_type: "paravirtual"
    datastore_name: "datastore_name"
    vm_power_up: true
    vm_post_setup_template: rhel8.j2
    vm_username: "vm_username"
    vm_password: "vm_password"
    validate_certs: true
    datastore_check_size: true
```

## License

GPLv3

## Testing

Before running the tests, you need to create a `vars.yml` file in the `tests` directory with your specific configuration. You can do this by copying the `vars_example.yml` file:

```bash
cp tests/vars_example.yml tests/vars.yml
```

Then, fill the `vars.yml` file with your specific values.

To run the tests, execute the following command:

```bash
ansible-playbook tests/test.yml -i tests/inventory
```

This command will run the playbook `test.yml` using the inventory file located in the `tests` directory.

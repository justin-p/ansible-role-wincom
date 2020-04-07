# ansible-wincom

This role helps simplifying some basis common tasks for a windows host deployment.

Works on

- Server 2019
- Server 2016
- Server 2012R2
- Server 2012

Not tested (yet) on:


- Server 2008R2
- Server 2008-x64
- Server 2008-x86

## Requirements

- `python3-winrm` (`pywinrm`) is needed for WinRM.

## Role Variables

All variables listed in `default/main.yml` reference variables from `vars/main.yml`.  
If you want to change any variables overwrite the ones listed in `vars/main.yml`.

### `vars/main.yml`

| Variable                         | Default value                       |
|:---------------------------------|:------------------------------------|
| wincom_choco_packages            | [BGInfo]                            |
| wincom_service_delayed           | [WinRM, NlaSvc]                     |
| wincom_required_psmodule         | [xPSDesiredStateConfiguration, NetworkingDsc, ComputerManagementDsc] |
| wincom_power_plan                | "high performance"                  |
| wincom_dns_nics                  | "Ethernet"                          |
| wincom_dns_server                | [8.8.8.8, 8.8.4.4]                  |
| wincom_hostname                  | "{{ inventory_hostname }}"          |

## Dependencies

N/A

## Example Playbook

    - hosts: windowshosts
      roles:
         - { role: justin_p.wincom }

## Local Development

This role includes a Vagrantfile that will spin up a local Windows Server 2019 VM in Virtualbox.  
After creating the VM it will automatically run our role.

### Development requirements

`pip3 install pywinrm`

#### Usage

- Run `vagrant up` to create a VM and run our playbook
- Run `vagrant provision` to reapply our playbook
- Run `vagrant destroy -f && vagrant up` to recreate the VM and run our playbook.
- Run `vagrant destroy` to remove the VM.

## License

MIT

## Authors

- Justin Perdok ([@justin-p](https://github.com/justin-p/)), Orange Cyberdefense

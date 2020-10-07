# ansible-role-wincom

[![Ansible Role Name](https://img.shields.io/ansible/role/51182?label=Role%20Name&logo=ansible&style=flat-square)](https://galaxy.ansible.com/justin_p/wincom)
[![Ansible Quality Score](https://img.shields.io/ansible/quality/51182?label=Ansible%20Quality%20Score&logo=ansible&style=flat-square)](https://galaxy.ansible.com/justin_p/wincom)
[![Ansible Role Downloads](https://img.shields.io/ansible/role/d/51182?label=Ansible%20Role%20Downloads&logo=ansible&style=flat-square)](https://galaxy.ansible.com/justin_p/wincom)
[![Github Actions](https://img.shields.io/github/workflow/status/justin-p/ansible-role-wincom/CI?label=Github%20Actions&logo=github&style=flat-square)](https://github.com/justin-p/ansible-role-wincom/actions)

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

`defaults/main.yml`

| Variable                 | Description                                      | Default value                                                        |
| :----------------------- | :----------------------------------------------- | :------------------------------------------------------------------- |
| wincom_required_psmodule | Powershell modules that should be installed.     | [xPSDesiredStateConfiguration, NetworkingDsc, ComputerManagementDsc] |
| wincom_service_delayed   | Services that should have delayed startup.       | [WinRM]                                                              |
| wincom_power_plan        | The desired settings of the windows power plan.  | "high performance"                                                   |
| wincom_dns_nics          | On what NIC should we update DNS.                | "\*"                                                                 |
| wincom_dns_server        | The DNS servers to configure on the NICs.        | [8.8.8.8, 8.8.4.4]                                                   |
| wincom_hostname          | Change the hostname of the system to this value. | "{{ inventory_hostname }}"                                           |

## Dependencies

- WinRM on the windows host should configured for Ansible.
- justin_p.posh5

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

## Contributing

Feel free to open issues, contribute and submit your Pull Requests. You can also ping me on Twitter ([@JustinPerdok](https://twitter.com/JustinPerdok)).

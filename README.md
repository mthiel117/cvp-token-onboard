# CVP Token Based Authentication

Automate copying CVP registration token to switches and updfate TerminAttr string to use token based auth

## Setup

- Update `token` value from CVP in the playbook
- Update inventory.yml to match environment
- Update terminattr.j2 template with proper string
- Update `ansible_user: admin` and `ansible_password: admin` to login to switches with ssh
- Ensure that eos_config galaxy module is installed

``` bash
ansible-galaxy collection install arista.eos
```

- Ensure netcommon galaxy modules is installed for sftp

``` bash
ansible-galaxy collection install ansible.netcommon
```

## Run Playbook

Push token to all switches in inventory

``` bash
ansible-playbook onboard_to_cvp.yml
```

Limit pushing token to `switch1`

``` bash
ansible-playbook onboard_to_cvp.yml -l switch1
```
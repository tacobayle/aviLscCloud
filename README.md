# aviLscCloud
## Prerequisites:
1. Make sure the controller is available at the IP defined in vars/creds.json
2. Make sure avisdk is installed:
```
pip install avisdk==18.1.5b3
ansible-galaxy install -f avinetworks.avisdk
```

## Input:
1. Make sure vars/creds.json is defined properly
```
{"avi_credentials": {"username": "admin", "controller": "172.16.1.5", "password": "Avi_2019", "api_version": "17.2.14"}, "avi_cluster": false}
```

## Use the ansible playbook to:
1. Configure a cloud user
2. Configure the SEs with ssh key
3. Configure a LSC cloud with all SE from the ansible inventory (group 'SE')
4. Configure VRF with BGP (if VS.0 has enable_rhi enabled)
5. Configure a health monitor
6. Configure a pool
7. Configure a VS

## Parameters:
All the paramaters/variables are stored in var/params.yml

## Run the playbook:
ansible-playbook -i hostsLocal main.yml

## Tests:
Playbooks have been tested against:
- Environment: LSC (wo cluster)
- Avi 18.1.5
- Ansible 2.7.0, 2.8.0.dev0

## Improvement:
Many!

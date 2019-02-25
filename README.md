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
3. Configure Network, Ipam and DNS profiles
3. Configure a LSC cloud with all SE from the ansible inventory (group 'SE'), with Ipam and DNS profiles
4. Configure VRF:
- update vrf with BGP parameters (if VS.0 has enable_rhi enabled)
- configure gateway monitor (if VS.0 has enable_rhi disable)
4. Configure VS(s):
- DNS VS
- Configure health monitor
- Configure Pool with associated health monitor
- non DNS VS (with Ipam and DNS): with BGP (if VS.0 has enable_rhi enabled), default is without BGP, with DNS fqdn

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

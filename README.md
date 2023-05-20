# slingnode-ethereum-examples
Example playbooks for SlingNode's Ethereum Ansible roles. 

This repo contians sample inventories, group vars and playbooks that cover common usage scenarios for SlingNode roles.
The examples are meant to showcase ways of structuring inventories and group vars to accomplish various deployment scenarios from deploying a whole stack (execution, consensus, validator) on a single server all the way up to deploying hundreds of servers in a multi tier architecture and full observability stack. 

Each directory corresponds to a role. 

## slingnode.ethereum

View the role on Ansible-Galaxy: https://galaxy.ansible.com/slingnode/ethereum

Review the source code and contribute on GitHub: https://github.com/SlingNode/slingnode-ansible-ethereum

Each sub-directory corresponds to a deployment scenario. For full documentation of the role and description of each scenario vist https://docs.slingnode.com/slingnode.ethereum/using-the-role.

We recommend that you review the documentation first however if you just want to get going and deploy your first node follow the steps below.

Clone the repo:

```shell
git clone git@github.com:SlingNode/slingnode-ethereum-examples.git
```
 Update execution-and-consensus-only/inventory.ini with your servers DNS name or IP address.
 
 For example let's say:
 - your server's IP address is 88.1.1.88
 - the server's user name is ubuntu
 - the SSH private key is ~/.ssh/ubuntu.privatekey
 
The inventory would be:
 
```ini
[ethereum_servers]
88.1.1.88
```

To execute the playbook and deploy the node using the default client (Geth & Lighthouse)

```shell
cd slingnode-ethereum-examples/slingnode.ethereum
ansible-galaxy install -r requirements.yml
cd execution-and-consensus-only
ansible-playbook deploy-execution-and-consensus-only-default-clients.yml -i inventory.ini --private-key ~/.ssh/ubuntu.privatekey  --user ubuntu
```

## slingnode.ethereum_node_mgmt

slingnode.ethereum_node_mgmt is designed to manage nodes deployed using slingnode.ethereum role. Having said that, most settings are templated out and factored out into variables. Therefore, it should be possible to adapt it and use it with any Ethereum node. 

View the role on Ansible-Galaxy: https://galaxy.ansible.com/slingnode/ethereum_node_mgmt

Review the source code and contribute on GitHub: https://github.com/SlingNode/slingnode-ansible-ethereum-node-mgmt

For full documentation of the role and description of example playbooks vist https://docs.slingnode.com/slingnode.ethereum_node_mgmt/using-the-role.


## slingnode.ethereum_observability 

slingnode.ethereum_observability is an Ansible role used to deploy a full observability stack that seamlessly integrates with Ethereum nodes deployed by slingnode.ethereum role. 

Both roles use the same naming for common variables. This means you can define them once in your Playbook, group_vars or host_vars and deploy a full Ethereum node along with the observability stack. 

View the role on Ansible-Galaxy: https://galaxy.ansible.com/slingnode/ethereum_observability

Review the source code and contribute on GitHub: https://github.com/SlingNode/slingnode-ansible-ethereum-observability

For full documentation of the role and description of example playbooks vist https://docs.slingnode.com/slingnode.ethereum_observability/using-the-role.

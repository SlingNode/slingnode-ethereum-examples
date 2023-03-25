# ethereum-examples
Example playbooks for SlingNode's Ethereum Ansible roles.

This repo contians sample inventories, group vars and playbooks that cover common usage scenarios for slingnode.ethereum role.
The examples are meant to showcase ways of structuring inventories and group vars to accomplish various deployment scenarios from deploying
a whole stack (execution, consensus, validator) on a single server all the way up to deploying hundreds of servers in a multi tier architecture.

Each directory in this project corresponds to a deployment scenario. For full documentation of the role and descriptions of each scenario
vist OURDOCSGITBOOKSITE.

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
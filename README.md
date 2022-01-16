# Setting up a k8s cluster with Ansible

### Prerequisites
- [Ansible](https://www.ansible.com/): Ansible is an open-source software provisioning, configuration management tool. 
- VMs. Your cluster will contain at least 3 nodes. One will serve as the master node, while the other two will serve as workers for running workloads. You can get VMs (droplets) for free on Digital Ocean when you click [this link](https://m.do.co/c/e40fed4d7bec)

### Getting started
- Clone the repository
- Add the appropriate IPs of your nodes in the `hosts` file. This is called an inventory. Read more [here](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html#how-to-build-your-inventory)
- Run `ansible-playbook -i hosts initial.yaml`
- Run `ansible-playbook -i hosts kube-dependencies.yml`
- Run `ansible-playbook -i hosts master-configuration.yml`
- Run `ansible-playbook -i hosts workers-config.yml`
- Run `ansible-playbook -i hosts install-helm.yml`

Verify your cluster is working by sshing into the master node and run `kubectl cluster-info`

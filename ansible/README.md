# Create Kubernetes cluster with Ansible
* [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## Check all nodes
```
ansible -i inventory.ini all -u root -m ping
```

## Install software
```
ansible-playbook -i inventory.ini install_software.yml
```

## Create cluster and master
```
ansible-playbook -i inventory.ini create_cluster.yml
```

## Join nodes to cluster
```
ansible-playbook -i inventory.ini join_nodes_to_cluster.yml
```

## Delete cluster
```
ansible-playbook -i inventory.ini delete_cluster.yml
```

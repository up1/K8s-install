# Deploy K8s cluster
* [Kubespray](https://github.com/kubernetes-sigs/kubespray)
* Python 3

## ETCD :: What is failure tolerance?
* https://etcd.io/docs/v3.2/faq/#what-is-failure-tolerance

## Download and install Kubespray
```
git clone https://github.com/kubernetes-sigs/kubespray.git
cd kubespray
pip install -r requirements.txt
```

## Create config to create cluster
```
cp -rfp inventory/sample inventory/mycluster
```

Edit your servers in cluster
```
// List of nodes (control plan, etcd, kube_node)
vi inventory/mycluster/inventory.ini

// Config network plugin, kubernetes version
vi inventory/mycluster/group_vars/k8s_cluster/k8s-cluster.yml

// Enable dashboard, metric server
vi inventory/mycluster/group_vars/k8s_cluster/addons.yml
```

Run and waiting
```
ansible-playbook -i inventory/mycluster/inventory.ini cluster.yml -b -v
```

Access to master node
```
// Get all nodes in cluster
kubectl get no -o wide

// Get images
nerdctl images
```

Deploy simple pods
```
kubectl create deployment nginx --image=nginx
kubectl expose deployment nginx --port 80 --type ClusterI

kubectl get po
kubectl get service
kubectl get deployment
kubectl get all
```

## Delete cluster and remove nodes
```
ansible-playbook -i inventory/mycluster/inventory.ini remove-node.yml -b -v
ansible-playbook -i inventory/mycluster/inventory.ini reset.yml -b -v
```
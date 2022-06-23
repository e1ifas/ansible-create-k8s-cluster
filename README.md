# ansible-create-k8s-cluster
Ansible playbook to create Kubernetes cluster

# Usage

## Edit inventory

Edit inventory based on `inventory/inventory_sample.yaml`.

## Edit variables.yaml

Edit inventory based on `vars/variables.yaml`.

+ `COMPATIBLE_OS_DIST`
    + Currently only Ubuntu.
+ `POD_NETWORK_CIDR`
    + This variable is used to execute `kubeadm init`. See [Installing a Pod network add-on](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/#pod-network) for details.
    + Default: `"192.168.0.0/16"`
+ `INSTALL_AS_USER`
    + Directory `~/.kube` is created under the home directory of this user.
    + This user is added to `docker` group.
    + Default: `"ubuntu"`

# Run playbook

## if apply to all server listed on inventory

```bash
ansible-playbook -i ansible-create-k8s-cluster.yaml
```

## if apply to specific server

Specify the target server after `-l` flag.

For example:

```bash
ansible-playbook -i ansible-create-k8s-cluster.yaml -l control_plane_1
```

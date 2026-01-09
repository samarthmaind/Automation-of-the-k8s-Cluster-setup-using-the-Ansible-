# Automation-of-the-k8s-Cluster-setup-using-the-Ansible-
Automation of the k8s Cluster setup using the Ansible 

# Kubernetes Cluster Automation using Ansible

This repository provides a **fully automated, idempotent, and production-tested**
Kubernetes cluster installer using Ansible and kubeadm.

## Features
- One-command cluster creation
- containerd runtime (SystemdCgroup fixed)
- Calico networking
- Master + worker automation
- Re-runnable and safe


## Usage
```bash
ansible-playbook site.yml





# Automating RKE2 Cluster Setup with Vagrant and Ansible Playbook

<p align="center">
    <img width=400 src="https://ranchergovernment.com/hubfs/horizontal-rke-2.png" alt="rke2" />
</p>

## Quick Start

To quickly get started with the RKE2 cluster setup using Vagrant, follow these steps:

```sh
git clone https://github.com/sylvain-pierrot/playbook-rke2-vagrant.git
cd playbook-rke2-vagrant
vagrant up --no-parallel
```

The `--no-parallel` flag ensures that the provisioning is done sequentially instead of in parallel, which can help avoid any potential resource conflicts.

Once the provisioning process is complete, you will have your RKE2 cluster up and running.

The kubeconfig file for the cluster will be created at the root of the project. You can use the following command to interact with the cluster using kubectl:

```sh
kubectl --kubeconfig ./kubeconfig [command]
```

Replace **[command]** with the desired kubectl command.

## Delete Cluster

To delete the RKE2 cluster, run the following command:

```sh
vagrant destroy --force
```

## Tech stack

<p align="left">
    <a href="https://www.gnu.org/software/bash/" target="_blank" rel="noreferrer">
        <img src="https://www.vectorlogo.zone/logos/gnu_bash/gnu_bash-icon.svg" alt="bash" width="40" height="40"/>
    </a>
    <a href="https://kubernetes.io" target="_blank" rel="noreferrer">
        <img src="https://www.vectorlogo.zone/logos/kubernetes/kubernetes-icon.svg" alt="kubernetes" width="40" height="40"/>
    </a>
    <a href="https://www.vagrantup.com/" target="_blank" rel="noreferrer">
        <img src="https://www.vectorlogo.zone/logos/vagrantup/vagrantup-icon.svg" alt="vagrant" width="40" height="40"/>
    </a>
    <a href="https://www.ansible.com/" target="_blank" rel="noreferrer">
        <img src="https://www.vectorlogo.zone/logos/ansible/ansible-icon.svg" alt="ansible" width="40" height="40"/>
    </a>
</p>

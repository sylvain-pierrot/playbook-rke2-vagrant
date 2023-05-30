# Setting Up RKE2 Cluster with Vagrant using Ansible Playbook

<p align="center">
    <img width=400 src="https://ranchergovernment.com/hubfs/horizontal-rke-2.png" alt="rke2" />
</p>

## Quick Start

To quickly get started with the RKE2 cluster setup using Vagrant, follow these steps:

```sh
git clone https://github.com/sylvain-pierrot/playbook-rke2-vagrant.git
cd playbook-rke2-vagrant
VAGRANT_NO_PARALLEL=yes vagrant up
```

The VAGRANT_NO_PARALLEL=yes flag ensures that the provisioning is done sequentially instead of in parallel, which can help avoid any potential resource conflicts.

Once the provisioning process is complete, you will have your RKE2 cluster up and running.

## Custom installation instructions

To set up the RKE2 cluster using Vagrant, follow these steps:

1. Ensure that you have Vagrant installed on your machine. If not, you can download and install it from the [Vagrant website](https://www.vagrantup.com/downloads.html).

2. Clone the repository or download the necessary files for the RKE2 cluster setup.

3. Open the `Vagrantfile` and locate the following code block:

    ```ruby
    Vagrant.configure("2") do |config|
        # Configuration details...
    end
    ```

4. Modify the configuration details according to your requirements. You can adjust the number of CPUs, memory allocation, IP addresses, and other parameters for the master and worker nodes.

5. Make sure to set the `ENV['BOX_IMAGE']` and `ENV['WORKER_NODES_COUNT']` environment variables to the appropriate values. These variables define the base box image and the number of worker nodes for the cluster.

6. Save the changes to the `Vagrantfile`.

7. Open a terminal or command prompt and navigate to the directory where the `Vagrantfile` is located.

8. Run the following command to start provisioning the cluster:

    ```sh
    VAGRANT_NO_PARALLEL=yes vagrant up
    ```

   Vagrant will create and configure the virtual machines according to the `Vagrantfile` specifications. It will also execute the Ansible playbooks specified for provisioning the master and worker nodes.

9. Wait for the provisioning process to complete. Once finished, you should have a fully functional RKE2 cluster set up with the specified number of worker nodes.

10. You can now interact with your RKE2 cluster using tools like `kubectl` or other Kubernetes utilities.

Feel free to customize the `Vagrantfile` and Ansible playbooks to suit your specific requirements.

**Note:** Make sure you have the necessary dependencies and box image specified in your `Vagrantfile` before running the `vagrant up` command.

For additional information and advanced usage, please refer to the project documentation or the relevant files in the repository.

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
    <a href="https://docs.rke2.io" target="_blank" rel="noreferrer">
        <img src="data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4KPCEtLSBHZW5lcmF0b3I6IEFkb2JlIElsbHVzdHJhdG9yIDI0LjEuMywgU1ZHIEV4cG9ydCBQbHVnLUluIC4gU1ZHIFZlcnNpb246IDYuMDAgQnVpbGQgMCkgIC0tPgo8c3ZnIHZlcnNpb249IjEuMSIgaWQ9IkxheWVyXzEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHg9IjBweCIgeT0iMHB4IgoJIHZpZXdCb3g9IjAgMCAzNDUuOTk3NjUwMSAxMTEuMzYyMzgxIiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCAzNDUuOTk3NjUwMSAxMTEuMzYyMzgxOyIgeG1sOnNwYWNlPSJwcmVzZXJ2ZSI+CjxzdHlsZSB0eXBlPSJ0ZXh0L2NzcyI+Cgkuc3Qwe2ZpbGw6IzM4NDc0NTt9Cgkuc3Qxe2ZpbGw6IzJFNjhFOTt9Cjwvc3R5bGU+CjxnPgoJPGc+CgkJPGc+CgkJCTxwYXRoIGNsYXNzPSJzdDAiIGQ9Ik0xNjMuODE5ODU0NywzMC4zMTM5MDc2aDIwLjgwMjk0OGM5Ljg3NzczMTMsMCwxNi41Mzc1OTc3LDQuNzg5MDU4NywxNi41Mzc1OTc3LDE0LjA2NzU1ODMKCQkJCWMwLDcuNTU4NzI3My01LjE2Mjk3OTEsMTIuMTIzNjgwMS0xMC4xNzczNjgyLDEzLjY5NDg2MjRjMS40OTY4ODcyLDEuMjcxNTYwNywyLjYxOTg1NzgsMi45OTI1NTM3LDMuNTE3NTAxOCw0Ljc4OTA1ODcKCQkJCWMyLjA5NDkwOTcsNC4yNjUzMzUxLDMuNTE2MjgxMSw4Ljk3ODg4MTgsNy45MzE0MjcsOC45Nzg4ODE4YzEuMTIyOTcwNiwwLDIuMDIwNjE0Ni0wLjM3MzkxNjYsMi4wMjA2MTQ2LTAuMzczOTE2NgoJCQkJbC0wLjk3MzE1OTgsOC45MDQ1NzkyYzAsMC0yLjY5MjkzMjEsMC42NzM1MzgyLTUuMDEzMTY4MywwLjY3MzUzODJjLTUuOTg2MzI4MSwwLTkuNDI4MzE0Mi0yLjMyMDIzNjItMTIuOTQ1ODAwOC0xMC4zMjcxNzEzCgkJCQljLTEuNDk1NjgxOC0zLjU5MDU3NjItMy41OTE3OTY5LTkuODc3NzQyOC02LjM2MDI0NDgtOS44Nzc3NDI4aC0yLjg0Mzk2MzZWODAuODIzMTQzaC0xMi40OTYzODM3VjMwLjMxMzkwNzZ6CgkJCQkgTTE3Ni4zMTYyMzg0LDM5LjM2ODMwMTR2MTIuNDIwODY0MUgxODAuODA2OWMzLjU5MTc4MTYsMCw3Ljc4MTYwMS0xLjEyMTc1MzcsNy43ODE2MDEtNi41MDg4MzQ4CgkJCQljMC00LjQxNTE0NTktMi44NDI3NDI5LTUuOTEyMDI5My02LjI4NTkzNDQtNS45MTIwMjkzSDE3Ni4zMTYyMzg0eiIvPgoJCQk8cGF0aCBjbGFzcz0ic3QwIiBkPSJNMjA5LjY5MTA3MDYsMzAuMzEzOTA3NmgxMi40OTYzNjg0djE0LjE0MzA3NGMwLDEuNTcxMTgyMy0wLjIyNDEwNTgsMy44OTAxOTc4LTAuMzczOTE2Niw1LjYxMjQwNzcKCQkJCWgwLjI5OTYyMTZjMC44MjMzNDktMS4yNzE1NjA3LDEuODcwODAzOC0zLjIxNzg3NjQsMy4xNDIzNjQ1LTQuNzE0NzYzNmwxMi4zNDc3OTM2LTE1LjA0MDcxODFoMTMuNDY4MzA3NQoJCQkJbC0xNi40NjIwODE5LDE5LjgyOTc3NjhsMTcuMzYwOTQ2NywzMC42Nzk0NTg2SDIzNy42MDMzMDJsLTExLjY3NDI1NTQtMjEuMTc1NjMyNWwtMy43NDE2MDc3LDQuNTY0OTUyOVY4MC44MjMxNDNoLTEyLjQ5NjM2ODQKCQkJCVYzMC4zMTM5MDc2eiIvPgoJCQk8cGF0aCBjbGFzcz0ic3QwIiBkPSJNMjU1LjkzNzQwODQsMzAuMzEzOTI2N2gzMy40NDc5MDY1djkuMjc4NDkyaC0yMC45NTE1MzgxdjEwLjg1MDg5MTFoMTcuNTg1MDUyNXY5LjI3ODQ5MmgtMTcuNTg1MDUyNQoJCQkJVjcxLjU0NDYzMmgyMS43MDA1OTJ2OS4yNzg0OTU4aC0zNC4xOTY5NjA0VjMwLjMxMzkyNjd6Ii8+CgkJPC9nPgoJCTxnPgoJCQk8Y2lyY2xlIGNsYXNzPSJzdDEiIGN4PSIzNC45MDgwNTgyIiBjeT0iNzYuMzk0MjEwOCIgcj0iNyIvPgoJCQk8cGF0aCBjbGFzcz0ic3QxIiBkPSJNNzEuNDU4NjE4Miw1OC42ODE4MjM3Yy0wLjIwOTE4MjcsMC0wLjQxNjk5MjItMC4wMTA4MTA5LTAuNjIzMDkyNy0wLjAyOTM5NjEKCQkJCWMxLjgwMzQ4OTcsMy44OTkxNzc2LDIuOTU4OTMxLDguMTU2ODk4NSwzLjMwNjE5ODEsMTIuNjM5OTkxOGgxNC45NjU1NzYyCgkJCQljMi4xMzM2NjctMy43NjMwNTM5LDUuNjE4OTcyOC02LjY2MDY4MjcsOS43OTM1MDI4LTguMDI5MDIyMnYtNC41ODMyODI1aC0yNy40MTM0NzUKCQkJCUM3MS40Nzc5MjgyLDU4LjY4MDE1NjcsNzEuNDY4MTg1NCw1OC42ODE4MjM3LDcxLjQ1ODYxODIsNTguNjgxODIzN3oiLz4KCQkJPHBhdGggY2xhc3M9InN0MSIgZD0iTTQyLjEwNzE1NDgsMjcuNzQ0MDc5NnY5LjY0NjQwNDNjOC4yNDQzMDg1LDEuMTEyNDIyOSwxNS42MzY4NjM3LDQuOTM4MTEwNCwyMS4yNDkxNjg0LDEwLjU0OTMwNQoJCQkJbC00Ljg4ODAzODYtMjAuMTk1NzA5Mkg0Mi4xMDcxNTQ4eiIvPgoJCQk8Y2lyY2xlIGNsYXNzPSJzdDEiIGN4PSIxMDQuMzM4Mjc5NyIgY3k9Ijc5Ljg5NDIxMDgiIHI9IjMuNSIvPgoJCQk8cGF0aCBjbGFzcz0ic3QxIiBkPSJNMTIxLjU4Njg5MTIsMEgxNC4zOTIzODI2QzYuNDc2NTM4MiwwLDAsNi40NzY2MjM1LDAsMTQuMzkyNDY4NXY4Mi41Nzc0Mzg0CgkJCQljMCw3LjkxNTg0NzgsNi40NzY1MzgyLDE0LjM5MjQ3MTMsMTQuMzkyMzgyNiwxNC4zOTI0NzEzaDEwNy4xOTQ1MTE0YzcuOTE1ODQwMSwwLDE0LjM5MjM4NzQtNi40NzY2MjM1LDE0LjM5MjM4NzQtMTQuMzkyNDcxMwoJCQkJVjE0LjM5MjQ2ODVDMTM1Ljk3OTI3ODYsNi40NzY2MjM1LDEyOS41MDI3MzEzLDAsMTIxLjU4Njg5MTIsMHogTTM0LjkwODA1ODIsOTcuMzk0MjEwOAoJCQkJYy0xMS41NzkzOTUzLDAtMjEuMDAwMDAxOS05LjQyMDU2MjctMjEuMDAwMDAxOS0yMVMyMy4zMjg2NjI5LDU1LjM5NDIwNywzNC45MDgwNTgyLDU1LjM5NDIwN3MyMSw5LjQyMDU2NjYsMjEsMjEuMDAwMDAzOAoJCQkJUzQ2LjQ4NzQ0OTYsOTcuMzk0MjEwOCwzNC45MDgwNTgyLDk3LjM5NDIxMDh6IE0xMDQuMzM4Mjc5Nyw5Ny4zOTQyMTA4CgkJCQljLTcuNzY2MTM2MiwwLTE0LjM2MzE1OTItNS4wODY1Nzg0LTE2LjY0NDE0MjItMTIuMTAxNzkxNGgtMjAuNDM2MjAzYy0zLjg2Mjk4NzUsMC02Ljk5NTIxNjQtMy4xMjkxNTA0LTctNi45OTE3OTg0CgkJCQlsLTAuMDA0NzgzNi00LjEwODA1NTFjMC0xMi43NjUwODcxLTEwLjM3ODMyMjYtMjMuMTQzNDA5Ny0yMy4xMzQ4NjQ4LTIzLjE0MzQwOTdIMjUuNjA4NjE3OGMtMy44NjU3MjI3LDAtNy0zLjEzMzkzNC03LTcKCQkJCXMzLjEzNDI3NzMtNyw3LTdoMi40OTg1MzUydi05LjMwNTA3NjZoLTIuNDk4NTM1MmMtMy44NjU3MjI3LDAtNy0zLjEzMzkzNTktNy03czMuMTM0Mjc3My03LDctN2gzOC4zNjczODU5CgkJCQljMy4yMzEzNDk5LDAsNi4wNDI5NjQ5LDIuMjEyMTA5Niw2LjgwMzgwNjMsNS4zNTMyMjE5bDYuMTkyMzM3LDI1LjU4MjgxMzNoMjYuNDE1MDg0OAoJCQkJYzUuMjQ1OTAzLDAsOS41MTM1NzI3LDQuMjY3Njc3Myw5LjUxMzU3MjcsOS41MTM1NzI3djEwLjQ0Njg5MThjNS4zMjg2MTMzLDMuMDAzMTEyOCw4LjkzNzQ3NzEsOC43MTMzMDI2LDguOTM3NDc3MSwxNS4yNTM2MzE2CgkJCQlDMTIxLjgzODI3OTcsODkuNTQzNzMxNywxMTMuOTg3ODkyMiw5Ny4zOTQyMTA4LDEwNC4zMzgyNzk3LDk3LjM5NDIxMDh6Ii8+CgkJPC9nPgoJPC9nPgoJPGc+CgkJPHBhdGggY2xhc3M9InN0MCIgZD0iTTM0NS45OTc2NTAxLDgwLjY0ODgxMTNoLTM3LjMwMDc4MTJ2LTguODU1MjkzM2wxMi41NTA3ODEyLTEyLjI5NTIyMzIKCQkJYzMuNTg1OTM3NS0zLjYzMjk0MjIsNS45Mjk2ODc1LTYuMTEzNTU1OSw3LjAzMTI1LTcuNDQxODQ4OHMxLjg2OTE0MDYtMi40NjkyNjUsMi4zMDI3MzQ0LTMuNDIyOTA4OAoJCQljMC40MzM1OTM4LTAuOTUzNjQ3NiwwLjY1MDM5MDYtMS45NTI3MDU0LDAuNjUwMzkwNi0yLjk5NzE3NzFjMC0xLjI5NDIzMTQtMC40MzM1OTM4LTIuMzE1OTk4MS0xLjMwMDc4MTItMy4wNjUyOTI0CgkJCWMtMC44NjcxODc1LTAuNzQ5MjkwNS0yLjA4NTkzNzUtMS4xMjM5Mzk1LTMuNjU2MjUtMS4xMjM5Mzk1Yy0xLjYxNzE4NzUsMC0zLjI1MTk1MzEsMC40NDg0NDA2LTQuOTA0Mjk2OSwxLjM0NTMyNTUKCQkJYy0xLjY1MjM0MzgsMC44OTY4ODExLTMuNTIxNDg0NCwyLjIxOTQ5NzctNS42MDc0MjE5LDMuOTY3ODQ5N2wtNy42Mjg5MDYyLTguNjUwOTM2MQoJCQljMi42NDg0Mzc1LTIuMjkzMjkzLDQuODc1LTMuOTMzNzkyMSw2LjY3OTY4NzUtNC45MjE0OTczczMuNzY3NTc4MS0xLjc0MjY3NTgsNS44ODg2NzE5LTIuMjY0OTA5NwoJCQljMi4xMjEwOTM4LTAuNTIyMjM1OSw0LjUwNTg1OTQtMC43ODMzNTE5LDcuMTU0Mjk2OS0wLjc4MzM1MTljMy4zMjgxMjUsMCw2LjI5ODgyODEsMC41Njc2NDYsOC45MTIxMDk0LDEuNzAyOTQKCQkJYzIuNjEzMjgxMiwxLjEzNTI5MjEsNC42NDA2MjUsMi43NTMwODYxLDYuMDgyMDMxMiw0Ljg1MzM3ODNzMi4xNjIxMDk0LDQuNDU2MDI4LDIuMTYyMTA5NCw3LjA2NzE5OTcKCQkJYzAsMS45NTI3MDU0LTAuMjUxOTUzMSwzLjc1NzgyMzktMC43NTU4NTk0LDUuNDE1MzUxOXMtMS4yODMyMDMxLDMuMjg2Njc0NS0yLjMzNzg5MDYsNC44ODc0MzU5CgkJCWMtMS4wNTQ2ODc1LDEuNjAwNzY1Mi0yLjQ1NTA3ODEsMy4yODY2NzQ1LTQuMjAxMTcxOSw1LjA1NzczMTZzLTUuNDY2Nzk2OSw1LjEzMTUyNjktMTEuMTYyMTA5NCwxMC4wODE0MDE4djAuMzQwNTkxNGgxOS40NDE0MDYyCgkJCVY4MC42NDg4MTEzeiIvPgoJPC9nPgo8L2c+Cjwvc3ZnPgo=#gh-light-mode-only" alt="rke2"  height="40"/>
    </a>
</p>

# ANSIBLE CONFIGURATION for KUBERNETES CLUSTER

Installing Ansible on the ansible server.

- Execute below command.

```
$ sudo apt update
$ sudo apt upgrade -y
```

- Ansible package and its dependencies are available in the default package repositories of Ubuntu 22.04/20.04, but it is not latest Ansible version. So, to install latest and stable ansible, enable its PPA repository, run following commands.

```
$ sudo apt install -y software-properties-common
$ sudo add-apt-repository --yes --update ppa:ansible/ansible
$ sudo apt update
```

- Install Ansible latest version with below command.

```
sudo apt install -y ansible
```

- Check the version with below command.

```
ansible --version
```

---

**_Clone the Ansible script repository outside of the cluster VM or Master Node and follow below instruction._**

1.  Check ping of all hosts - Master and Worker nodes.

    ```
            ansible -i hosts all -m ping
    ```

2.  Create a linux User with below command.

    ```
            ansible-playbook -i hosts users.yml --ask-become-pass
    ```

3.  Install K8s with below command.

    ```
            ansible-playbook -i hosts install-k8s.yml --ask-become-pass
    ```

4.  Configure Master Node with below command.

    ```
            ansible-playbook -i hosts master.yml
    ```

5.  Configure to join with Worker Nodes with below command.

    ```
            ansible-playbook -i hosts join-workers.yml
    ```

---

### Notes:

**_You may skip defining password within the hosts file, follow hostsV2 and execute below command_**

```
ansible -i hosts all -m ping --ask-pass
```

Execute below command to create user with password defined as variable and provide password.

```
ansible-playbook -i hosts users.yml --ask-pass --extra-vars="upassword=Pass123$" --ask-become-pass
```

**_Variable can be pass within the file._**

Example:

```
msg: "fruit is {{ fruit }}"


Command:
----------------------------------------------
ansible-playbook --extra-vars="fruit=apple"
----------------------------------------------
```

## References:

- https://jianjye.medium.com/how-to-update-user-password-with-ansible-f971f41a3b3e

- https://www.linuxtechi.com/how-to-install-ansible-on-ubuntu/
- https://linuxhint.com/pass-ansible-username-and-password/
- https://buildvirtual.net/deploy-a-kubernetes-cluster-using-ansible/
- https://medium.com/opsops/how-to-pass-password-to-ansible-from-environment-variable-bd5c566bc8a1
- https://www.ansiblepilot.com/articles/pass-variables-to-ansible-playbook-in-command-line-ansible-extra-variables/#:~:text=The%20easiest%20way%20to%20pass,pre%2Dexistent%20automation%20or%20script.
- https://stackoverflow.com/questions/19292899/creating-a-new-user-and-password-with-ansible

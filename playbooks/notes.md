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

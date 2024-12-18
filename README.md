# Ansible - Personal Playbook
--------

To start follow these steps to set your linux user and group names in Ansible:
1. Navigate to `environments` directory
2. In `environments` directory navigate to `all` directory.
3. Click on `vars.yml` and change `user` and `group` vars to your name and group
    ```
    user: alialsada
    group: alialsada
    ```
Note that `vars.yml` in all directory contains global settings that will be accesible to every role in the playbook



## Run Playbook
To run all the roles in the playbook, execute this command in the terminal:
```
sudo ansible-playbook -i inventory.ini all.yml
qtile cmd-obj -o cmd -f restart
```
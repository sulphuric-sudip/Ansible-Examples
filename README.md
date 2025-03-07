# Ansible Playbooks

**Note:** These are the playbooks collection I had used to automate my DevOps tasks.

Refer Ansible Documentation For Details: [https://docs.ansible.com/ansible/latest/getting_started/index.html](https://docs.ansible.com/ansible/latest/getting_started/index.html)

## Usage
- #### Check connectivity to hosts
    ```ansible all -m ping -i inventory.ini```   
    ```ansible kafka-servers -m ping -i inventory.ini```

- #### Check the syntax of a playbook without executing it
    ```ansible-playbook <playbook.yml> --syntax-check -i inventory.ini```

- #### Dry run a playbook to see what changes would be made
    ```ansible-playbook <playbook.yml> --check -i inventory.ini```

- #### Run a playbook with displaying the changes made
    ```ansible-playbook <playbook.yml> --diff -i inventory.ini```

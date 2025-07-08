# Ansible-tutorial

This is my awesome Ansible tutorial repository.

# ansible.cfg
Where we can put default settins

# Run specefic host like ubuntu and kali 

    ansible all -i inventory.ini -m ping -l ubuntu,kali
Here `-l` is the limit option

Other option to skip windows hosts

    ansible all -i inventory.ini -m ping --limit 'all:!windows'

Create role   

    ansible-galaxy role init test

ansible-galaxy is the command followed `role` to create `role` then init to initialize then role name like `test`.   

    .
    ├── defaults
    │   └── main.yml
    ├── files
    ├── handlers
    │   └── main.yml
    ├── meta
    │   └── main.yml
    ├── README.md
    ├── tasks
    │   └── main.yml
    ├── templates
    ├── tests
    │   ├── inventory
    │   └── test.yml
    └── vars
        └── main.yml


ansible-galaxy Created this file structure under the test folder.













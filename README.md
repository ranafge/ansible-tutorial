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

    $ ansible-playbook -i inventory.ini ping_playbook.yml --limit 'all:!windows' --become --ask-become-pass
    BECOME password: 

    PLAY [Check the reachability of Ubuntu and kali hosts] *********************************

    TASK [Gathering Facts] *****************************************************************
    ok: [192.168.11.103]
    ok: [192.168.11.102]

    TASK [Ping hosts to check reachability] ************************************************
    ok: [192.168.11.102]
    ok: [192.168.11.103]

    PLAY RECAP *****************************************************************************
    192.168.11.102             : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
    192.168.11.103             : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

Successfully check the hosts reachability.

### Amazon ansible install command  
    ansible-galaxy collection install amazon.aws
    













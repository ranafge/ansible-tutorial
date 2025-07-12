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
    


    - name: Create 5 EC2 instances with unique names
  hosts: localhost
  connection: local
  gather_facts: false

  vars:
    key_name: ansible-ec2-create
    region: ap-south-1
    ami_id: ami-09dcba964a9c51505
    instance_type: t3.small
    subnet_id: subnet-037d62220ca04ba91
    security_group: default

  tasks:
    - name: Launch EC2 instances
      amazon.aws.ec2_instance:
        name: "ubuntu{{ item }}"
        key_name: "{{ key_name }}"
        instance_type: "{{ instance_type }}"
        image_id: "{{ ami_id }}"
        region: "{{ region }}"
        wait: true
        count: 1
        vpc_subnet_id: "{{ subnet_id }}"
        network:
          assign_public_ip: true
          groups:
            - "{{ security_group }}"
        tags:
          Name: "ubuntu{{ item }}"
          Project: "ansible-ec2-create"
      loop: "{{ range(1, 6) | list }}"

## It will create multipe ubuntu ec2 instance.










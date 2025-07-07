# ansible-tutorial

This is my awesome Ansible tutorial repository.

# ansible.cfg
Where we can put default settins

# run specefic host like ubuntu and kali 

    ansible all -i inventory.ini -m ping -l ubuntu,kali
Here `-l` is the limit option

Other option to skip windows hosts
#### `ansible all -i inventory.ini -m ping --limit 'all:!windows'`

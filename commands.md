# Ansible Configuration File 
    sudo nano /etc/ansible/ansible.cfg
- `host_key_checking = false` - Disable Fingerprint checking to avoid manual confirmation 
- `inventory = /home/dima/ansible_playbooks/hosts` - Specify the inventory file location

# Generage SSH key on Ansible Server
   - `ssh-keygen -b 4096` - Generate a 4096-bit SSH key
   - `ssh-copy-id User@Destination_Server` - Copy SSH Public Key to Destination Server

# Inventory File
    [LINUX] # Group_Name
    ubuntu01 ansible_host=192.168.0.55

# Group Variables ( Create `group_vars` Folder )
      nano group_vars/LINUX # Same as Group_Name
   - `ansible_user=root`
   - `ansible_ssh_private_key_file= /root/.ssh/id_rsa`
   - `environment: Prod`
   - `owner: Dima_Dolgov`
   - `OS: Linux`


## **Directory Structure:**
    └── ansible_playbooks  - Main Ansible Directory
        ├── group_vars     - Directory for Variables
        │   └── LINUX      - Exact Group_Name like in hosts file
        └── hosts          - Inventory File

# Commands
- `ansible all -m ping` - Ping all hosts using Ansible to check connectivity
- `ansible all -m setup` - Gather facts about all hosts using Ansible
- `ansible-inventory --list` - List all inventory information
- `ansible-inventory --graph` - Generate a visual graph of the inventory
- `ansible all -m shell -a "command"` - Run a shell command on all hosts ad-hoc
- `ansible all -m copy -a "src=file dest=/home/dima mode=777"` - Copy file from Ansible Server to destination path with new Permissions
- `ansible all -m file -a "path=/home/dima/file state=absent"` - Remove a file from the specified path on all hosts
- `ansible all -m get_url -a "url=http://speedtest.lt.cherryservers.com/test-100mb dest=/home/dima"` - Download file to all hosts
- `ansible all -m apt -a "name=docker.io state=latest" -b --ask-become-pass` - Install Package to all hosts with root (-b)
- `ansible all -m apt -a "name=docker.io state=absent" -b --ask-become-pass` - Remove Package to all hosts with root (-b)
- `ansible all -m uri -a "url=https://www.google.com"` - Check Internet Connectivity
- `ansible all -m uri -a "url=https://www.google.com return_content=yes"` - Check Internet Connectivity with content
- `ansible all -m apt -a "name=apache2 state=latest" -b --ask-become-pass` - Install Package Apache
- `ansible all -m service -a "name=apache2 state=started enabled=yes" -b --ask-become-pass` - Ensure the service is started and enabled







# Install Amazon AWS Collection
    ansible-galaxy collection install amazon.aws

# REInstall Requirements ( pip install -r ansible_requirements --force )
    ansible
    ansible-core
    boto
    boto3
    botocore

# AWS Inventory
    ansible-inventory -i aws_ec2.yml --graph

# Run Playbook
    ansible-playbook -i aws_ec2.yml all Playbook_Name


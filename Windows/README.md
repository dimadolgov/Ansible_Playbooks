# Directory Structure

```plaintext
/etc
├── krb5.conf

/etc/ansible
├── ansible.cfg

/root/ansible
├── var
│   └── main_variables.yaml
├── group_vars
│   └── windows.yml
├── playbooks
│   ├── sql_server.yml
│   └── vm_vmware.yml
└── roles
    ├── vm_disk
    │   └── tasks
    │       ├── main.yml
    │       ├── add_disk.yaml
    │       └── create_disk.yaml
    └── vm_sql
        └── tasks
            ├── main.yml
            ├── Create_SQL_Disk.yaml
            ├── Prerequirements.yaml
            └── SQL_Install.yaml

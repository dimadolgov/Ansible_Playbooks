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

# krb5.conf
[libdefaults]
    default_realm = DOMAIN.LOCAL
    dns_lookup_realm = false
    ticket_lifetime = 24h
    renew_lifetime = 7d
    forwardable = true
    rdns = false

[logging]
    default = FILE:/var/log/krb5libs.log
    kdc = FILE:/var/log/krb5kdc.log
    admin_server = FILE:/var/log/kadmind.log

[realms]
    DOMAIN.LOCAL = {
        admin_server = dc.DOMAIN.LOCAL
        kdc = dc.DOMAIN.LOCAL
    }

[domain_realm]
    domain.local = DOMAIN.LOCAL
    .domain.local = DOMAIN.LOCAL

# user-management-ansible

## Details

Ansible version: [2.9.7](https://docs.ansible.com/ansible/latest/reference_appendices/release_and_maintenance.html)

[Setting Up Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

### Examples

##### List Users
Lists users on hosts

```
ansible-playbook ./list_users.yml
```

##### User Management (Add & Remove Users)
[Users File](/users/vars.yml)

**Add User(s)**

Required: 
- name: example_username

```
web_app_users:
  - { name: user1, create_home: yes, comment: "test 1" }
```

**Remove User(s)**

Required:
- state: absent
- remove: yes

```
web_app_users:
  - { name: user1, create_home: yes, comment: "test 1", state: absent, remove: yes, pubKey: "..." }
```

Sync Users (run updates, additions, deletions)
```
ansible-playbook ./update_users.yml -e @./users/vars.yml
```
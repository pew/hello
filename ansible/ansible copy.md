# ansible
!

## aws ec2
### setup
    mv ec2.py /etc/ansible/hosts

### run shell commands on specific tags
    ansible tag_Name_*test* -m shell -a "uptime"

### run playbook for specific names
    ANSIBLE_HOSTS=/etc/ansible/hosts ansible-playbook os_update.yaml

os_update.yaml:

```
---
- hosts:
  - tag_Name_ansible-test
  tasks:
  - name: OS Update
    yum: name=* state=latest
```
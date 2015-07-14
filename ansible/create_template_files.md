# create ansible template files

get config without comments

```
grep -v ^# /etc/sshd_config > sshd_config.j2
```

make your changes, add variables (see ansible docu), for example:

```
#{{ ansible_managed }}
Port 22
ListenAddress {{ ansible_ssh_host }}
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
UsePrivilegeSeparation yes
```

# use it in a playbook

place it to the templates folder, for example: `roles/common/templates/sshd_config.j2` and use it in a playbook, for example: `roles/common/tasks/main.yml`

```
- name: deploy sshd config
  template: src=sshd_config.j2 dest=/etc/ssh/sshd_config backup=yes owner=root group=root mode=0644
  notify:
  - restart sshd
```

to restart sshd add the following file `roles/common/handlers/main.yml`

```
---
- name: restart sshd
  service: name=sshd state=restarted
```

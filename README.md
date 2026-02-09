# Ansible_P1

This project demonstrates basic Ansible usage starting from localhost execution and extending to remote EC2 server automation.

---

## Copying files from Local System to EC2

```sh
C:\Users\AVULLA UTEJ> scp -i pem-file.pem pem-file.pem ubuntu@ec2-xx-xx-xxx-xx.xx:/home/ubuntu/
```
Syntax Check for Ansible Playbook
```sh
ubuntu@ip-172-31-37-66:~/Ansible_P1/ansible_test$ ansible-playbook --syntax-check playbook1.yml
```
```sh
[WARNING]: No inventory was parsed, only implicit localhost is available
[WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does
not match 'all'

playbook: playbook1.yml
```
Playbook 1 – Running on Localhost
```sh
ubuntu@ip-xxx-xx-xx-xx:~/Ansible_P1/ansible_test$ ansible-playbook playbook1.yml
```
```sh
[WARNING]: No inventory was parsed, only implicit localhost is available
[WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does
not match 'all'

PLAY [First Playbook] *****************************************************************************************

TASK [Gathering Facts] ****************************************************************************************
ok: [localhost]

TASK [Test Connectivity] **************************************************************************************
ok: [localhost]

PLAY RECAP ****************************************************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

Playbook 2 – Install and Start Nginx (Localhost)
```sh
ubuntu@ip-172-31-37-66:~/Ansible_P1/ansible_test$ ansible-playbook playbook2.yml
```
```sh
[WARNING]: No inventory was parsed, only implicit localhost is available
[WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does
not match 'all'

PLAY [Install and start the Nginx] ****************************************************************************

TASK [Gathering Facts] ****************************************************************************************
ok: [localhost]

TASK [Installing nginx] ***************************************************************************************
changed: [localhost]

TASK [Starting nginx service] *********************************************************************************
ok: [localhost]

PLAY RECAP ****************************************************************************************************
localhost                  : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
Verifying Nginx Service Status
```sh
ubuntu@ip-172-31-37-66:~/Ansible_P1/ansible_test$ systemctl status nginx
```
```sh
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2026-02-09 13:28:50 UTC
     Main PID: 3702 (nginx)
     Tasks: 3
     Memory: 5.4M
     CPU: 30ms
```
Playbook 3 – Running on Remote EC2 Server
```sh
ubuntu@ip-172-31-37-66:~/Ansible_P1/ansible_test$ ansible-playbook playbook2.yml
```
```sh
PLAY [Install and start the Nginx] ****************************************************************************

TASK [Gathering Facts] ****************************************************************************************
[WARNING]: Platform linux on host 172.31.37.104 is using the discovered Python interpreter at
/usr/bin/python3.12, but future installation of another Python interpreter could change the meaning of that
path.
ok: [172.31.37.104]

TASK [Installing nginx] ***************************************************************************************
changed: [172.31.37.104]

TASK [Starting nginx service] *********************************************************************************
ok: [172.31.37.104]

PLAY RECAP ****************************************************************************************************
172.31.37.104              : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
Summary
- Ansible defaults to localhost when no inventory is provided
- Inventory enables remote EC2 automation
- Same playbook works for both localhost and remote servers
- Ansible ensures idempotent configuration management

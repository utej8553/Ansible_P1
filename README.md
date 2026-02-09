# Ansible_P1
Copying from local system into ec2:
```sh
C:\Users\AVULLA UTEJ>scp -i pem-file.pem pem-file.pem ubuntu@ec2-xx-xx-xxx-xx.xx:/home/ubuntu/
```
Syntax checK:
```sh
ubuntu@ip-172-31-37-66:~/Ansible_P1/ansible_test$ ansible-playbook --syntax-check playbook1.yml
[WARNING]: No inventory was parsed, only implicit localhost is available
[WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does
not match 'all'

playbook: playbook1.yml
```
playbook1:
```sh
ubuntu@ip-xxx-xx-xx-xx:~/Ansible_P1/ansible_test$ ansible-playbook playbook1.yml
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
Playbook2:
```sh
ubuntu@ip-172-31-37-66:~/Ansible_P1/ansible_test$ ansible-playbook playbook2.yml
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

ubuntu@ip-172-31-37-66:~/Ansible_P1/ansible_test$ systemctl status nginx
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2026-02-09 13:28:50 UTC; 15s ago
       Docs: man:nginx(8)
    Process: 3606 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/S>
    Process: 3607 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
   Main PID: 3702 (nginx)
      Tasks: 3 (limit: 2268)
     Memory: 5.4M
        CPU: 30ms
     CGroup: /system.slice/nginx.service
             ├─3702 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
             ├─3704 "nginx: worker process" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" >
             └─3705 "nginx: worker process" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" >

Feb 09 13:28:50 ip-172-31-37-66 systemd[1]: Starting A high performance web server and a reverse proxy server.>
Feb 09 13:28:50 ip-172-31-37-66 systemd[1]: Started A high performance web server and a reverse proxy server.

```

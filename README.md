# Ansible_P1
Copying from local system into ec2:
```sh
C:\Users\AVULLA UTEJ>scp -i pem-file.pem pem-file.pem ubuntu@ec2-xx-xx-xxx-xx.xx:/home/ubuntu/
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

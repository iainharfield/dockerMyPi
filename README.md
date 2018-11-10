# dockerMyPi

Execute the playbooks in the following order
--------------------------------------------
1) sudo ansible-playbook -v sshcpy.yml -u ${USER} -k
2) sudo ansible-playbook -v docker-install-raspbian.yml
3) sudo ansible-playbook -v sudoers.yml --ask-become-pass
4) sudo ansible-playbook -v portainer.yml 

# dockerMyPi

A set of Ansible scripts to set up a Raspberry Pi with Docker and some utilities.

Minimum Pre-requisits:
----------------------
1) Down load the headless image from here:  https://www.raspberrypi.org/downloads/raspbian/
2) Burn the image
3) Edit the image to activate the SSH. Create a file named ssh in the boot partition (the file does not expect any extension). 
4) plug into your Pi and SSH should work

Execute the playbooks in the following order from Ansible server:
-----------------------------------------------------------------
1) sudo ansible-playbook -v sshcpy.yml -u ${USER} -k
2) sudo ansible-playbook -v docker-install-raspbian.yml
3) sudo ansible-playbook -v sudoers.yml --ask-become-pass
4) sudo ansible-playbook -v portainer.yml 

When propted for SSH password - its the RPI password.

To access the Portainer UI:
  <ipaddress of RPI>:9000


Sometimes I get Unreachable message- dont really know why.  To fix this I execute:
    ansible all -m ping
and then retry the playbook.   Not spent any time figuring it out.

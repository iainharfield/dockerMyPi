# dockerMyPi

A set of Ansible scripts to set up a Raspberry Pi with Docker and some utilities.

Minimum Pre-requisits:
----------------------
1) Ansible and ansible_hosts file is already configured on Ansible server.
2) Download the headless image from here:  https://www.raspberrypi.org/downloads/raspbian/
3) Burn the image onto  your SD card (e.g. Win32DiskImager,balenaEtcher etc.)
4) Edit the SD card image to activate the SSH. Create a file named "ssh" in the boot partition (no file extension). 
5) Plug SD card into your Pi and SSH should work.

Execute the playbooks in the following order from Ansible server:
-----------------------------------------------------------------
1) sudo ansible-playbook -v sshcpy.yml -u ${USER} -k
2) sudo ansible-playbook -v docker-install-raspbian.yml
3) sudo ansible-playbook -v sudoers.yml --ask-become-pass
4) sudo ansible-playbook -v portainer.yml 

When prompted for SSH password - its the RPI password.

To access the Portainer UI from a browser enter:
------------------------------------------------
<blockquote>
<p>"ipaddress-of-RPI":9000</p>
</blockquote>

Issues
------
Sometimes I get "Unreachable" message when executing a playbook - don't know why at the moment.  To bypass this I execute:
<blockquote>
<p>ansible all -m ping</p>
</blockquote>
    
and then retry the playbook which then seems to run fine. I've not spent any time figuring it out.

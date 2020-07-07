First, we need to install Ansible.  Ansible is written in python, so we generally have two options to install it.
* Install using `pip` (i.e., `pip install ansible`)
* Install using your system's package manager
  *  MacOS: `brew install ansible`
  *  Ubuntu: `apt install ansible`
  *  Red Hat: `yum install ansible`
  
**Note**: If you're doing this on Windows 10, I strongly recommend just using WSL (preferably WSL2, which was released
in the early 2020 update.  It's just a lot easier.)

After getting Ansible installed, it's time to move on to the next step, 
[setting up test VMs](02-setting-up-test-vms.md)
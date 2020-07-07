## Installing test VMs for this tutorial
The easiest option for doing this is to use VMs.

For the purpose of this tutorial, we want Ubuntu VMs.  We can use VMWare, VirtualBox, Fusion, anything we want, but
there are a few requirements that we want to make sure are met:
* We need to be able to `sudo` from the user we'll be logging in as
* The user we'll be logging in as should be set up with SSH key-based access
  * If this isn't feasible for some reason, you'll need to install `sshpass` (outside the scope of this), but it's
  well worth avoid this problem.
  * If you can log in via a password to the VM, just run `ssh-copy-id user@ip` and your default key will be set up as
  an allowed IP address.
  
If you want to use an alternative key, or you are going to be doing this tutorial using AWS EC2 instances (or similar
key-based cloud provider), see [appendix a - using alternative keys](a-using-alternative-keys.md).

You should be able to log in to your VMs (either a VM on your machine or running 'in the cloud') using a username and
key.  Ideally, set up three, but even one is sufficient.

Once that's done, move on to learn about [the basics of inventory](03-basics-of-inventory.md).
Now that we have our inventory ready and configure, we can start getting some actual mileage out of our work so far!

It's easy to start.  From a command line, run this:

`ansible -i inventory all -m ping`

As long as you can connect to the hosts, you should get a lot of output, and we've run our first bit of Ansible!

## What's going on here
* `ansible` is just that - the ansible binary
* `-i inventory` is us specifying 
* `all` is the group (or host) we want to run the module against
* `-m ping` is us specifying the `ping` module.  This isn't ICMP ping (what we typically think of as ping), this is just
a connection test.  This is the "hello world" of Ansible.


We should get some output now.

After this, move on to the next step to learn [how to write a playbook]()
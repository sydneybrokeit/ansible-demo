The first thing to making use of Ansible is inventories.  Inventories are pretty much exactly what they sound like --
lists of our servers under management.

There are two styles of inventory that Ansible can handle - YAML based inventory and ini-style inventory.  You can even
use both of these in the same set, but for the purpose of this, we'll just go over the ini-style for now.

## Anatomy of an inventory file
Let's take a look at the inventory file I've included here:
```
[app_server]
192.168.0.3

[database_server]
192.168.0.2

[proxy_server]
192.168.0.1

[private_servers:children]
app_server
database_server
```

In this file, we've defined four groups.  Groups are just that - groups of _hosts_, the machines under management.
Hosts can be defined by IP or by a DNS name.

`[app_server]`, `[database_server]`, and `[proxy_server]` are groups that are made up of individual hosts.  The part
between the `[]` is the name of the group, and everything listed under it is a member of that group.

`private_servers` is a group made up of other groups, which is why it's listed as `[private_servers:children]`.  Now
all the hosts in the groups under it are now a part of the `private_servers` group.

We have two places where we can store information about individual hosts - either within the inventory file (or files!)
itself, or within the `host_vars` directory.  We'll get into that in the next bit 
[using host and group variables](04-host-and-groups-vars.md)

### Exercise
Put your VMs into the inventory file and remove the existing ones.

If you only have 1 or 2 VMs, it's fine if they overlap.
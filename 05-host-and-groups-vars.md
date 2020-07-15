When we're working with our invetory, we will frequently need to store information about the host or the group.  This
can include things like usernames, passwords, firewall rules, hostnames, or anything else you might want to configure
as part of the setup of an individual machine or group of machines.

There are several types of variables we can use as part of the setup.  For now, we're going to look at host
variables and group variables.

Host variables are variables applied to an individual host, while group variables are applied to -- you guessed it! --
groups from our inventory.

## How to set up host and group variables
To use host or group variables, we need to create a `host_vars` or `group_vars` directory in the same location as our
inventory.  If we are using an inventory directory, we should have these directories in the same level as the other
inventory files (i.e., 'beside' them).

Inside the appropriate directory, create a file with the name of the host or group you want to set variables for,
followed by `yml`.  If I am creating host variables for a host named `app1.example.com` in the inventory file, I need
to create to create a file in `host_vars` called `app1.example.com.yml`.  For a group called `app_servers`, I would
create a file called `app_servers.yml` inside `group_vars`.  

### What a vars file looks like
`app1.example.com`
```
---
hostname: app1.example.com
```

In this example, this will set a variable for this host (which is tied to the name in the inventory).  We can use
any sort of compliant YAML, including hosts, maps, and lists.  We'll eventually go over how to use all of these, so
don't worry.

## When should I use host vs group variables?
In general, host variables should be used for variables that will be different from host to host, and group
variables should be used for variables that will be consistent from host to host within a group (at least mostly).

Something that is important to understand, at least in a general sense, is the variable precedence rules of Ansible.
While we'll get into this more later, for now, it's enough to know that host variables are a higher precedence than
group variables, so if we set a variable for a group and then set that same variable for a specific host within that
group, the host variable's value will 'win'.  This is very helpful when a group will be *mostly* consistent, but we
may have one or two hosts that need a specific value, or for when we want a default value.

In general, remember that variables will also follow order of specificity - the smaller a set is (groups are bigger
than hosts), the higher its precedence.

## The `all` group
There is also one special group name - `all`.  As its name suggests, we can assign variables to everything at once 

## Exercise
Go ahead and create the host variables files for our three existing hosts, in line with our existing inventory file.
Specifically, we want to tell Ansible how to log in, so we'll want to set the username for the host either at the 
host or group level.  Hint: you'll want to set the `ansible_user` variable for the host or group.

## Next steps
The next thing we'll look at is [how to run Ansible](06-running-ansible.md)
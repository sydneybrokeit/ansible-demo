So, now we've been able to run a module, but we can't really do much useful with just modules.  The next thing we're
going to look at is _playbooks_.  Playbooks are the collections of steps that make up the core of the power we can
harness from Ansible.

## Anatomy of a task:
So what goes into making a playbook?  Let's take a look at [07-install-webserver.yml](07-install-webserver.yml).

```
---
- hosts: app_server
  tasks:
    - name: Ensure apt repository is up to date
      apt:
        update_cache: yes
      become: yes

    - name: Ensure apache is installed
      apt:
        name: apache
      become: yes
```

First, we have our header, `---`

Then, we are starting a list.  We can have have multiple sets of these in a playbook.  This is useful when we want
to do a full set of something before moving on, but right now, we won't worry about.

So, the next line
```
  - hosts: app_server
```
is us starting the list and specifying the hosts we want to run against.  We can specify either hosts or we can
specify a group name here.

The next bit is us defining a variable named `tasks`:
```
    tasks:
```

Inside our `tasks` variable, we create another list.  In our example, the list has two elements:
```
    - name: Ensure apt repository is up to date
      apt:
        update_cache: yes
      become: yes
```
There's a few elements here:
* `name` is the name we're going to give to the task itself.  In this case, we're saying the name of the task is
`Ensure apt repository is up to date`.  *When you're naming tasks, try to think in terms of ensuring a state, rather
than performing a task*.  It can be helpful to think in terms of the word "ensure".
* `apt` is the module we are using.  Many modules have specific internal variables that can be used; in this case,
we are specifying the `update_cache` variable within the map that makes up the configuration for `apt`.  Note the
indentation!

**Important**: Ansible has a lot of modules.  Most standard tasks can be accomplished with pure Ansible modules and
should be done as such whenever possible to help ensure idempotence.

* `become: yes` tells Ansible we need to become root (or potentially another user) in order to take this action.  At
 its simplest, Ansible only requires `become: yes` to become root, but this is highly configurable.
 
 So this step will become root in order to update our apt cache.
 
```
    - name: Ensure apache is installed
      apt:
        name: apache
      become: yes
``` 

In this case, we are using the apt module to ensure the package named `apache` is installed.  It's very similar to
the previous step, so I won't dig into it much.

## Exercise
Using the [service module](https://docs.ansible.com/ansible/latest/modules/service_module.html#service-module), 
ensure that the `apached` service is both `enabled` and `started`.

## Note
Ansible has many modules; if you want to do something on a host, there is likely already a module.  Check the
[official Ansible docs for modules!](https://docs.ansible.com/ansible/latest/modules/modules_by_category.html)
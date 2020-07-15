## Conditional Logic in Ansible
There may be times when we only want to perform a particular step under certain circumstances.  To do this, we can
use the `when` modifier on a task (or other things we'll get into later).

```
    - name: Restart haproxy when the configuration has changed
      service:
        name: haproxy
        state: restarted
      become: yes
      when: haproxy_cfg.changed
```

We can use the `when` line to tell Ansible what conditions should result in the task running.  In this case,
we're only going to restart haproxy when `haproxy_cfg.changed` is `true` (like Python, we can simply use the boolean
directly, rather than ` == true`).  We can use a lot of the standard operators (>, <, ==, >=, <=) along with some
filters (which we'll get into later).

But where does `haproxy_cfg.changed` come from?  That's a good question!  We have to teach Ansible how to do it!

The step of generating the configuration comes before this task:
```
    - name: Generate haproxy config
      template:
        src: haproxy.cfg.j2
        dest: /etc/haproxy/haproxy.cfg
      become: yes
      register: haproxy_cfg
```

The key part here is the `register: haproxy_cfg`.  When we use `register`, we're creating a variable specific to this
host that contains information about the step, including whether it actually resulted in a change.

So putting these together
```
    - name: Generate haproxy config
      template:
        src: haproxy.cfg.j2
        dest: /etc/haproxy/haproxy.cfg
      become: yes
      register: haproxy_cfg
    - name: Restart haproxy when the configuration has changed
      service:
        name: haproxy
        state: restarted
      become: yes
      when: haproxy_cfg.changed
```
So now we're going to end up with a consistent haproxy configuration, and only restart when it's actually changed.

### Exercise
Use the apt module to install `haproxy` on the proxy servers group, and keep it always up-to-date and restart haproxy
on any change to the installation.

##
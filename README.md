# What is Ansible?
Ansible is a state and configuration management tool, allowing us to perform tasks and manage state on multiple devices.

## Key Concepts of State/Configuration Management
Before we dig in, let's go over some concepts that help us understand both how Ansible works and why and when it is 
the right tool for the job.
### Pets vs Cattle
Pets are animals we care about; when they get sick, we baby them, we take them to the vet, a lot of us will spare no
expense in getting it healthy.  When a cattle ranch has a sick animal, more often than not, it becomes a case of killing
it and replacing it.

The same thing can apply to infrastructure.  When our devices 'get sick', we can spend time healing them, or we can
shoot them in the head and replace them.  This is a lot easier to do when we're using cloud infrastructure, but it can
be applied to on-premises devices as well.

### Infrastructure as Code
We're all fairly familiar with using tools like Git to manage our codebases - we can see what changed when, who changed
it, and if people are being smart, even why it was changed.

What if we could apply the same thing to our infrastructure?  What if we could apply things like `git diff` or `git
blame` to how we configure servers, or even to how those servers are built in the first place?

Tools like Ansible, along with other things like Terraform, Puppet, and Chef, use code to help us control our
infrastructure.  When done thoroughly and correctly, this can turn into us being able to completely track all of our
infrastructure, giving us the ability to track every change in our infrastructure, from configuration files to firewall
settings.

### Imperative vs Declarative programming
Another thing to understand is imperative vs declarative programming.

What we typically think of as programming is imperative programming - that is, programming where we explicitly
tell the machine exactly what we want it to do, step by step.

In contrast, declarative programming is more about *declaring* the state we want things to be in, whether we are
describing the result set, the final state of something, or a general configuration.

If you're familiar with SQL, you've already done some declarative programming - SQL queries are about the desired state
of the result set, rather than the exact logic the database engine will use to find and return the data you've
requests.

Ansible is declarative; as we learn about Ansible, we will learn more about how to take advantage of the declarative
nature of it.

### Idempotence
In math, there is the concept of idempotence -- a value that, when operated on by itself, does not change.  Or, in the
case of Ansible, idempotence refers to the fact that, if we have a properly crafted Ansible playbook, we can run it
as many times as we want, and our system will always end up in the exact same state - we won't end up with
configuration files with extra lines, we won't end up creating extras of files, we won't end up with multiple copies
of a repository.  The state is going to be always consistent as long as we do our job correctly.

## Index
1. [Installing Ansible](01-installing-ansible.md)
1. [Setting up test VMs](02-setting-up-test-vms.md)
1. [Basics of inventory](03-basics-of-inventory.md)
1. [YAML Syntax](04-yaml-syntax.md)
1. [Host and Group Variables](05-host-and-group-vars.md)
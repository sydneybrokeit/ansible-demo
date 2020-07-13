Almost everything in Ansible is configured using [YAML syntax](https://yaml.org/spec/1.2/spec.html).

## Basics of YAML
The first part of YAML is the header, composed of three `-` and then a newline.  Comments can be placed above this
header.

```
---
```
### Variables
So now we can start adding information to the file.  Let's start off giving it some key-value pairs.

```
---
hostname: host1.example.com
username: admin
```

So now we've created two variables - `hostname` and `username`, which we can use in our playbooks (we'll get into
playbooks soon).

### Lists
We can also do lists of items:
```
---
packages_to_install:
  - ffmpeg
  - build-tools
  - golang
```
Notice that indentation is exactly 2 spaces.

In the above example, we end up with a variable `packages_to_install` that contains three elements, `ffmpeg`, 
`build-tools`, and `golang`.

### Map
We can also have a map of values within a variable:
```
---
user:
  name: admin
  shell: /bin/bash
  password: "totallyNotMyPassword1"
```

Note: Don't actually store passwords in plaintext.  Please.  It's a bad idea.  If I have to explain why... ask me.
I'll tell you.  Oh lordy will I tell you.

In the above example, we have a `user` with `name`, `shell`, and `password` keys.  We can access these using either
"dot notation" like `user.name` or with "bracket notation" like `user["name"]`.

We can also do this all in a single line:
```
---
user: { name: admin, shell: "/bin/bash", password: "totallyNotMyPassword1" }
``` 

This functions identically.

## Exercise
Using the information above, create a variable named `users`, and make it consist of users, each containing:
* `username`
* `password`
* `shell`
* `group`

Once that's done, move on to [host and group variables](05-host-and-groups-vars.md)



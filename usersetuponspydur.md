# User setup on Spydur

This document summarizes how users on Spydur acquire their environment and the shell
functions in it. This kind of user setup is very common, if not completely a "standard."

## User organization

All users are members of the default group. Every computer has a default group for 
the non-system (generic) users. On Spydur, the name associated with the default group
is `people`. On the Parish Lab workstations, the default group is `users`. To determine
the default group on a Linux computer, 

```bash
cat /etc/default/useradd | grep ^GROUP 
```

Each user is also a member of a group associated with a faculty sponsor. The group
is named for the faculty member, and it ends in a dollar sign (just to make it easier
to identify these groups visually). Example, `gflanagi$`. 

Each user who is a member of the `faculty` group has one of these eponymous groups, 
and is a member of that group. So, `gflanagi` is a member of `gflanagi$`.

A user, mainly students, may be a member of more than one of the "dollar sign" groups.

Most users are also a member of one or more department groups. These groups are all
four letters long, again just for ease of visual identification. Examples: `chem`, `econ`,
`maps`, `psyc`.

On Spydur, ordinary users are also a member of the group named `managed`, and that
membership allows the privileged user `installer` to impersonate the user.

## When users login on any Linux computer ...

### /etc/profile, /etc/bashrc, *etc*

All interactive sessions (i.e., login from a text based terminal, or login via ssh) read this
file. This file should never be modified. 

Because we are using the bash shell, the login also reads the contents of `/etc/bashrc`. 
Similarly, this file should not be modified. Customizations are done by adding files
the `/etc/profile.d` directory, and they are read by the last few lines of `/etc/bashrc`, 
and are processed in alphabetic order. 

### $HOME/.bash_profile and $HOME/.bashrc

These files typically setup a user's `$PATH` and other common elements of the environment.
In many/most environments the elements of the environment that apply to all users are
in this file, and it is often read-only to prevent accidental corruption. The last line
of the file usually reads the contents of the `$HOME/.bashrc.d` directory, which is the
ideal place for user customizations.

## When users login on Spydur

The user `$HOME/.bashrc` file reads the file `/usr/local/etc/usersrc`

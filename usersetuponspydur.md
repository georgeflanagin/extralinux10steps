# User setup on Spydur

This document summarizes how users on Spydur acquire their environment and the shell
functions in it. This setup using groups is very common, if not completely a "standard."

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

Students are members of the `student` group. Many students are members of more than 
one of the "dollar sign" groups.

Most users are also a member of one or more department groups. These groups are all
four letters long, again just for ease of visual identification. Examples: `chem`, `econ`,
`maps`, `psyc`.

On Spydur, ordinary users are also a member of the group named `managed`, and that
membership allows the privileged user `installer` to impersonate the user.

The final group of significance is the `trustee` group. Some of the directories that
contain software that is managed by one "power user" but used by several others are
owned by the trustee group with group write. 

## When users login on any Linux computer ...

*NB: The design of this process supports flexibility, but more importantly it supports
the idea that everything has its place. When changes are requested or needed, it is 
clear what file will contain the change.*

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

The user `$HOME/.bashrc` file reads the files in `/usr/local/sw/etc/usersrc` according to
the rules below.

The first file read is `/usr/local/etc/usersrc/common.rc`. It is the one that holds the
system's organization and it dates from October 20, 2021. It contains a number of shell 
functions that would be normally found in the `$HOME/.bashrc` file on systems with only a few users.

The `common.rc` makes a note of all the department groups to which the user belongs. 
It sorts the list of departments, and applies any departmental customizations that are
found in files whose name fits the pattern `/usr/local/etc/usersrc/{department}`. These files
contain shortcuts that make it easier for `chem`'s users to use chemistry software, as an example.

Then `common.rc` goes through the user's "dollar sign" groups to apply customizations
requested by the faculty member associated with the group. These customizations often
relate to a specific research project or a specific class being taught. Many of these files
are empty.

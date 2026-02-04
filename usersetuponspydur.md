# User setup on Spydur

This document summarizes how users on Spydur acquire their environment and the shell
functions in it.

# User organization

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

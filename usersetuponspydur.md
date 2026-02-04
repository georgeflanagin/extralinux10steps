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

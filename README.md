# Linux 10.x -- additional installation steps for workstations

# Disable SELinux

SELinux has its purposes, but it interferes with several scientific packages. The workstations
do not run webservers, and they are only accessible through the UR VPN or on-campus. Consequently, 
the benefits of disabling SELinux far outweigh the perceived benefits of having it 
remain active.

First, disable it within the current session. The effect will be immediate, and you thus
do not need to reboot to observe the effect.
```
setenforce 0
```

Second, edit the `/etc/selinux/config` file so that the first non-comment line reads:
```
SELINUX=disabled
```

# NVIDIA drivers (current on 10 November 2025)

Locating the rpm requires looking for it on the nvidia.com site. Search for "rocky linux 10 driver rpm download site:nvidia.com" and you will likely find yourself on the https://developer.nvidia.com/datacenter-driver-downloads page, which does have a Rocky 10 section after following the prompts. The one most recently retrieved is this one:
```
wget https://developer.download.nvidia.com/compute/nvidia-driver/580.105.08/local_installers/nvidia-driver-local-repo-rhel10-580.105.08-1.0-1.x86_64.rpm
```

# Extra libraries

While these are generally needed in the workstation environment, the locations and
sources of many have changed since 8.10. Additionally, some of the system objects (.so files)
that were current in 8.10 are now in compatibility libraries.

Many of the installations below could be combined into a single `dnf install ...` command,
but they are listed individually for clarity.

```
dnf install epel-release
dnf install environment-modules
dnf install libcrypt\*
dnf install libgfortran\*
dnf install libGLU\*
```

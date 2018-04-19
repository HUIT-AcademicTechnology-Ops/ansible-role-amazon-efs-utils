# Ansible Role: Amazon EFS Utils

Ansible role that installs and configures the AWS EFS utils package on linux instances.   The instructions for building and installing are taken from the [official AWS Github repo | https://github.com/aws/efs-utils] of the library.

The actual mounting is left out of this role.  Note that there are some tasks that don't need `sudo` privileges while some do, so the ones that do are given the `become: yes` flag.


## Requirements

None.

## Role Variables

Below are available variables for configuring the installation and setup of the efs utils package:

```
# Installation options:
# ---
efs_utils_download_source_url: https://github.com/aws/efs-utils/tarball/master
# Default to the official Github source url for Amazon's EFS utils
# library.   Use Github's tarball url to get the source code without
# cloning.  There are currently no numbered versions in the official
# Github repo so we default to master.
efs_utils_download_local_path: /tmp
# Where the unpacked tarball gets stored on the remote host
efs_utils_manage_config: false
# Don't override the base conf file by default


# Configuration for inputs.conf
# ---
# Values represent the current defaults provided by Amazon in the conf file
efs_utils_conf_logging_level: INFO
efs_utils_conf_stunnel_debug_enabled: false
efs_utils_conf_mount_watchdog_enabled: true
efs_utils_conf_mount_watchdog_enabled_poll_interval_sec: 1
efs_utils_conf_mount_watchdog_unmount_grace_period_sec: 30
```

## Dependencies

None.

## Example Playbook

    - hosts: server
      roles:
         - { role: huit-at.amazon-efs-utils }

## License

MIT

## Author Information

This role was created by Jaime Bermudez in 2018 as a member of HUIT's Academic Technology group.
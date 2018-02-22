## Why?
This abomination was created out of a need to walk a remote file system to gather a list of files matching a pattern (with exclusions) but without using any custom or non-stock Ansible modules.  Many features of Ansible were abused to make this role possible.

## Usage
Include the config below in an existing role to get a list of files in the variable "filterfiles\_files"

```yaml
- name: Filter files
  import_role:
    name: filterfiles
  vars:
    filterfiles_paths:
      - /etc/sysconfig/
    filterfiles_include:
      - '^/etc/sysconfig/network-scripts/ifcfg-.*'
    filterfiles_exclude:
      - '^/etc/sysconfig/network-scripts/ifcfg-test.*'

- name: Debug - found files
  debug:
    var: filterfiles_files
```


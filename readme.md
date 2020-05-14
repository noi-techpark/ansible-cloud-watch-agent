Ansible Cloud Watch Agent Role
==============================

Installation of AWS CloudWatch role.

## Role Variables

- `cloud_watch_agent_ssm_config`: The configuration name stored in SSM

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: ansible-cloud-watch-agent
      vars:
        cloud_watch_agent_ssm_config: AmazonCloudWatch-LinuxBasic
```

## Versioning

In order to have a verioning in place and working, create leightweight tags that point to the appropriate minor release versions.

Creating a new minor release:

```bash
git tag 1.0
git push --tags
```

Replacing an already existing minor release:

```bash
git tag -d 1.0
git push origin :refs/tags/1.0
git tag 1.0
git push --tags
```

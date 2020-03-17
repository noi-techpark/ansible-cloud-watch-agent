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

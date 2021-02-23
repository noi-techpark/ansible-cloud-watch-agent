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

## AWS IAM Role

In order for an AWS EC2 instance to be able to send data to AWS CloudWatch, an IAM role must be attached to the EC2 instance to grant access.

1. **Create the AWS IAM role:**  
    - AWS service: EC2
    - Permissions:
      ```json
      {
        "Version": "2012-10-17",
        "Statement": [
          {
              "Effect": "Allow",
              "Action": [
                "cloudwatch:PutMetricData",
                "ec2:DescribeVolumes",
                "ec2:DescribeTags",
                "logs:PutLogEvents",
                "logs:DescribeLogStreams",
                "logs:DescribeLogGroups",
                "logs:CreateLogStream",
                "logs:CreateLogGroup"
              ],
              "Resource": "*"
          },
          {
            "Effect": "Allow",
            "Action": [
              "ssm:GetParameter"
            ],
            "Resource": "arn:aws:ssm:*:*:parameter/AmazonCloudWatch-*"
          }
        ]
      }
      ```
2. **Attach the role to the EC2 instance**

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

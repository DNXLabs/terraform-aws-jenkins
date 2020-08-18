# terraform-aws-jenkins

[![Lint Status](https://github.com/DNXLabs/terraform-aws-jenkins/workflows/Lint/badge.svg)](https://github.com/DNXLabs/terraform-aws-jenkins/actions)
[![LICENSE](https://img.shields.io/github/license/DNXLabs/terraform-aws-jenkins)](https://github.com/DNXLabs/terraform-aws-jenkins/blob/master/LICENSE)

This terraform module deploys Jenkins master and build agents in AWS.

This module deploys a multi-az master using `ebs-pin` and a spot Auto Scaling Group(ASG) for build agents using [Self-Organizing Swarm Plug-in][]. The build agents scale preemtively based on demand using `jenkins-autoscaler`.

The following resources will be created:

 - AWS Key pair
 - AWS Public key
 - AWS Security groups for the Jenkins
 - DNS zone ID used for Jenkins records
 - DNS record created for Jenkins master in dns_zone
 - AWS Identity and Access Management (IAM) roles
 - Jenkins certificates - ACM Certificate Domain Name for Jenkins

 You have the option to:

 - Size of root volume on Jenkins agents.
   - The default value is 50
 - Specify Instance type of agents.
   -  The default value is "C5.large""
 - Set  Max size of agents ASG.
   - The default value is 20
 - Set Minimum size of agents ASG.
   - The default value is 2
 - Set Max price for spot bids on agents
   - The default value is 0.5
 - Set AMI ID used by the Jenkins master instance
   - The default value is ami-08589eca6dcc9b39c
 - Instance type used by Jenkins master instance
   - The default value is "T3.medium"
 - Set Linux agents Userdata
 - Set Linux ASG Userdata
 - Set Userdata for the master Jenkins

[ebs-pin]: https://github.com/aarongorka/ebs-pin
[Self-Organizing Swarm Plug-in]: https://wiki.jenkins.io/display/JENKINS/Swarm+Plugin
[jenkins-autoscaler]: https://github.com/aarongorka/docker-jenkins-autoscaler

<!--- BEGIN_TF_DOCS --->

## Requirements

| Name | Version |
|------|---------|
| terraform | >= 0.12.20 |

## Providers

| Name | Version |
|------|---------|
| aws | n/a |
| template | n/a |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| account\_name | account name | `any` | n/a | yes |
| agents\_disk\_size | Size of root volume on Jenkins agents | `string` | `"50"` | no |
| agents\_instance\_type | Instance type of agents | `string` | `"c5.large"` | no |
| agents\_max\_size | Max size of agents ASG | `string` | `"20"` | no |
| agents\_min\_size | Minimum size of agents ASG | `string` | `"2"` | no |
| agents\_spot\_price | Max price for spot bids on agents | `string` | `"0.5"` | no |
| agents\_subnet\_ids | Subnet IDs for the Jenkins agents. | `list` | n/a | yes |
| ami\_id | AMI ID used by the Jenkins master instance | `string` | `"ami-08589eca6dcc9b39c"` | no |
| asg\_tags | Tags used for ASGs, has an addition attribute propagate\_at\_launch on every map. Do not include 'Name'. | `list` | n/a | yes |
| aws\_key\_pair\_name | Keypair for the Jenkins master instance | `any` | n/a | yes |
| aws\_key\_pair\_public\_key | Public Key in authorized\_keys format | `any` | n/a | yes |
| dns\_base\_name | DNS base zone, e.g. example.com | `any` | n/a | yes |
| dns\_name | DNS record created for Jenkins master in dns\_zone | `any` | n/a | yes |
| dns\_zone | DNS zone ID used for Jenkins records | `any` | n/a | yes |
| http\_proxy | HTTP Proxy used in the Jenkins userdata script | `any` | n/a | yes |
| instance\_type | Instance type used by Jenkins master instance | `string` | `"t3.medium"` | no |
| jenkins-cert | ACM Certificate Domain Name for Jenkins | `any` | n/a | yes |
| jenkins\_unique\_id | Unique ID used to identify the EBS volume accross instance terminations | `any` | n/a | yes |
| lb\_subnet\_ids | Subnet IDs for the ALB. | `list` | n/a | yes |
| linux\_workers | If set to true, enable linux workers | `bool` | n/a | yes |
| master\_ebs\_jenkinshome\_size | Size of the master jenkins home volume | `string` | `"50"` | no |
| master\_ebs\_root\_size | Size of the master EBS root volume | `string` | `"20"` | no |
| master\_subnet\_ids | Subnet ID for the Jenkins master instance. Multi AZ is supported :) | `list` | n/a | yes |
| no\_proxy | Proxy exceptions used in the Jenkins userdata script | `any` | n/a | yes |
| tags | Tags used for all resources except asgs | `map` | n/a | yes |
| vpc\_id | VPC ID used by the Jenkins master instance | `any` | n/a | yes |
| windows\_ami\_id | AMI ID used by the Jenkins master instance | `string` | `"ami-0bbaefd8648c81cc8"` | no |
| windows\_workers | If set to true, enable windows workers | `bool` | n/a | yes |

## Outputs

| Name | Description |
|------|-------------|
| master\_ssh | SSH to access the Jenkins master instance |
| url | URL to access the Jenkins UI |

<!--- END_TF_DOCS --->

## Authors

Module managed by [DNX Solutions](https://github.com/DNXLabs).

## License

3-Clause BSD Licensed. See [LICENSE](https://github.com/DNXLabs/terraform-aws-jenkins/blob/master/LICENSE) for full details.
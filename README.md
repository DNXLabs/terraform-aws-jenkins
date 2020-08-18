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

<!--- END_TF_DOCS --->

## Authors

Module managed by [DNX Solutions](https://github.com/DNXLabs).

## License

3-Clause BSD Licensed. See [LICENSE](https://github.com/DNXLabs/terraform-aws-jenkins/blob/master/LICENSE) for full details.
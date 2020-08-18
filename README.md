# terraform-aws-jenkins

[![Lint Status](https://github.com/DNXLabs/terraform-aws-jenkins/workflows/Lint/badge.svg)](https://github.com/DNXLabs/terraform-aws-jenkins/actions)
[![LICENSE](https://img.shields.io/github/license/DNXLabs/terraform-aws-jenkins)](https://github.com/DNXLabs/terraform-aws-jenkins/blob/master/LICENSE)

A Terraform module that deploys a multi-az master using [ebs-pin][] and a spot ASG for build agents using [Self-Organizing Swarm Plug-in][]. The build agents scale preemtively based on demand using [jenkins-autoscaler][].

[ebs-pin]: https://github.com/aarongorka/ebs-pin
[Self-Organizing Swarm Plug-in]: https://wiki.jenkins.io/display/JENKINS/Swarm+Plugin
[jenkins-autoscaler]: https://github.com/aarongorka/docker-jenkins-autoscaler

<!--- BEGIN_TF_DOCS --->

<!--- END_TF_DOCS --->

## Authors

Module managed by [DNX Solutions](https://github.com/DNXLabs).

## License

3-Clause BSD Licensed. See [LICENSE](https://github.com/DNXLabs/terraform-aws-jenkins/blob/master/LICENSE) for full details.
# terraform-aws-kops-route53 [![Build Status](https://travis-ci.org/cloudposse/terraform-aws-kops-route53.svg?branch=master)](https://travis-ci.org/cloudposse/terraform-aws-kops-route53)

Terraform module to lookup the roles associated with `kops` masters and nodes, and attach an IAM policy to the roles with permissions to modify Route53 record sets.

It provides the IAM permissions needed by [route53-kubernetes](https://github.com/cloudposse/route53-kubernetes) for `kops`.

This is useful to make Kubernetes resources discoverable via AWS DNS services.


## Usage

```hcl
module "kops_route53" {
  source       = "git::https://github.com/cloudposse/terraform-aws-kops-route53.git?ref=master"
  namespace    = "cp"
  stage        = "prod"
  name         = "route53"
  masters_name = "masters"
  nodes_name   = "nodes"

  tags = {
    Cluster = "k8s.domain.com"
  }
}
```


## Variables

|  Name              |  Default     |  Description                                                                     | Required |
|:-------------------|:-------------|:---------------------------------------------------------------------------------|:--------:|
| `namespace`        | ``           | Namespace (_e.g._ `cp` or `cloudposse`)                                          | Yes      |
| `stage`            | ``           | Stage (_e.g._ `prod`, `dev`, `staging`)                                          | Yes      |
| `name`             | ``           | Name (_e.g._ `route53`)                                                          | Yes      |
| `attributes`       | `[]`         | Additional attributes (_e.g._ `policy` or `role`)                                | No       |
| `tags`             | `{}`         | Additional tags  (_e.g._ `map("Cluster","k8s.domain.com")`                       | No       |
| `delimiter`        | `-`          | Delimiter to be used between `namespace`, `stage`, `name`, and `attributes`      | No       |
| `masters_name`     | `masters`    | K8s masters subdomain name in the Kops DNS zone                                  | No       |
| `nodes_name`       | `nodes`      | K8s nodes subdomain name in the Kops DNS zone                                    | No       |


## Outputs

| Name             | Description         |
|:-----------------|:--------------------|
| `policy_id`      | Policy ID           |
| `policy_name`    | Policy name         |
| `policy_arn`     | Policy ARN          |


## Help

**Got a question?**

File a GitHub [issue](https://github.com/cloudposse/terraform-aws-kops-route53/issues), send us an [email](mailto:hello@cloudposse.com) or reach out to us on [Gitter](https://gitter.im/cloudposse/).


## Contributing

### Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/cloudposse/terraform-aws-kops-route53/issues) to report any bugs or file feature requests.

### Developing

If you are interested in being a contributor and want to get involved in developing `terraform-aws-kops-route53`, we would love to hear from you! Shoot us an [email](mailto:hello@cloudposse.com).

In general, PRs are welcome. We follow the typical "fork-and-pull" Git workflow.

 1. **Fork** the repo on GitHub
 2. **Clone** the project to your own machine
 3. **Commit** changes to your own branch
 4. **Push** your work back up to your fork
 5. Submit a **Pull request** so that we can review your changes

**NOTE:** Be sure to merge the latest from "upstream" before making a pull request!


## License

[APACHE 2.0](LICENSE) Â© 2018 [Cloud Posse, LLC](https://cloudposse.com)

See [LICENSE](LICENSE) for full details.

    Licensed to the Apache Software Foundation (ASF) under one
    or more contributor license agreements.  See the NOTICE file
    distributed with this work for additional information
    regarding copyright ownership.  The ASF licenses this file
    to you under the Apache License, Version 2.0 (the
    "License"); you may not use this file except in compliance
    with the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing,
    software distributed under the License is distributed on an
    "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
    KIND, either express or implied.  See the License for the
    specific language governing permissions and limitations
    under the License.


## About

`terraform-aws-kops-route53` is maintained and funded by [Cloud Posse, LLC][website].

![Cloud Posse](https://cloudposse.com/logo-300x69.png)


Like it? Please let us know at <hello@cloudposse.com>

We love [Open Source Software](https://github.com/cloudposse/)!

See [our other projects][community]
or [hire us][hire] to help build your next cloud platform.

  [website]: https://cloudposse.com/
  [community]: https://github.com/cloudposse/
  [hire]: https://cloudposse.com/contact/


## Contributors

| [![Erik Osterman][erik_img]][erik_web]<br/>[Erik Osterman][erik_web] | [![Andriy Knysh][andriy_img]][andriy_web]<br/>[Andriy Knysh][andriy_web] |[![Igor Rodionov][igor_img]][igor_web]<br/>[Igor Rodionov][igor_img]
|-------------------------------------------------------|------------------------------------------------------------------|------------------------------------------------------------------|

[erik_img]: http://s.gravatar.com/avatar/88c480d4f73b813904e00a5695a454cb?s=144
[erik_web]: https://github.com/osterman/
[andriy_img]: https://avatars0.githubusercontent.com/u/7356997?v=4&u=ed9ce1c9151d552d985bdf5546772e14ef7ab617&s=144
[andriy_web]: https://github.com/aknysh/
[igor_img]: http://s.gravatar.com/avatar/bc70834d32ed4517568a1feb0b9be7e2?s=144
[igor_web]: https://github.com/goruha/

# terraform-provider-agentiik

The Terraform provider: namespaces, workflow repositories, grants, groups, service
accounts, API tokens, secret declarations and triggers. A client of `/api/v1` holding no
authority of its own — a plan applies as the presenting principal and is refused by the
same grants that refuse the console.

Two things it deliberately does not manage. The contents of a workflow, because
`agentiik.yaml` is already the source of truth and HCL would be a second one that
disagrees with it at the first push. Secret values, because a value passing through
Terraform is a value in the state file.

Runs it does manage, in a shape that keeps an apply idempotent: `agentiik_run` declares
that a run of a workflow, at a commit, with given inputs, has happened — change none of
those and applying again starts nothing. For the genuinely imperative case there is a
provider action, requiring Terraform 1.14.

Published to the Terraform registry. The provider is Apache-2.0 and is built on a plugin
framework that is MPL-2.0, so nothing source-available enters this repository; Terraform
itself has been under the Business Source License since 2023, which is a choice its users
made and not one this project makes for them. OpenTofu implements the same plugin
protocol and is not excluded, but it is not tested there.

Nothing is implemented yet. The provider is specified at
<https://agentiik.github.io/docs#terraform>.

## Licence

Apache-2.0, see [LICENSE](LICENSE). Copyleft on a provider would reach into the
infrastructure code that calls it, which is somebody else's work.
[LICENSING.md](https://github.com/agentiik/.github/blob/main/LICENSING.md) has the
reasoning.

## Contributing

[CONTRIBUTING.md](https://github.com/agentiik/.github/blob/main/CONTRIBUTING.md), under
the Developer Certificate of Origin 1.1.

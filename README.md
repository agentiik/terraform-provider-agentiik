# terraform-provider-agentiik

The Terraform provider: namespaces, workflow repositories, grants, groups, service
accounts, API tokens, secret declarations and triggers. A client of `/api/v1` holding no
authority of its own — a plan applies as the presenting principal and is refused by the
same grants that refuse the console.

Three things it deliberately does not manage. The contents of a workflow, because
`agentiik.yaml` is already the source of truth and HCL would be a second one that
disagrees with it at the first push. Runs, because starting one is an act rather than a
state and would make an apply non-idempotent in the one way the tool cannot tolerate.
Secret values, because a value passing through Terraform is a value in the state file.

Built against the plugin protocol and published to the Terraform registry and the
OpenTofu one, and tested against both. Terraform moved to the Business Source License in
2023 and is no longer open source; a project that declined to ship source-available
software cannot then require its users to run some. Which of the two you run is your
decision and costs you nothing here.

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

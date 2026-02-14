# terraform-iac

Terraform infrastructure-as-code: AWS tasks, projects, and examples.

## Layout

```
aws/
├── tasks/          # One-off / experimental configs (VPC transit GW, peering, ALB+EC2, ECS, etc.)
├── projects/       # Full stacks (secure VPC, remote state, S3 static, tf-ansible-nginx, etc.)
└── examples/       # Reference examples (e.g. auto-imports)
```

- **tasks** — standalone envs (e.g. `vpc-transit-gw/env/dev`, `alb-ec2`, `vpc-peering`). Run from the task or env dir.
- **projects** — multi-env or multi-component (e.g. `remote-tf-state/{dev1-vpc,dev2-ec2,dev3-alb}`, `aws-secure-vpc/envs/{dev,prod}`). Each subdir is a root module.
- **examples** — copy-paste / learning snippets.

## Usage

From any `.tf` root (e.g. `aws/tasks/vpc-transit-gw/env/dev` or `aws/projects/remote-tf-state/dev1-vpc`):

```bash
terraform init
terraform plan
terraform apply
```

Backend and provider config live in each root; some use S3 remote state (see `backend "s3"` in `main.tf`).

## License

MIT — see [LICENSE](LICENSE).

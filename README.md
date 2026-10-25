# Lab-Terraform: CI/CD Infrastructure

Quản lý hạ tầng AWS bằng Terraform thông qua GitHub Actions CI/CD.

## Môi trường

| Môi trường | Account   | Region              | Directory        |
|------------|-----------|---------------------|------------------|
| STG        | Gconfig   | Seoul (ap-northeast-2) | `envs/stg/gconfig/` |
| PRD        | WebAPK    | Singapore (ap-southeast-1) | `envs/prd/webapk/` |

## Cấu trúc thư mục

```
Lab-Terraform/
├── modules/
│   └── s3/                  # Reusable S3 module
│       ├── main.tf
│       ├── variables.tf
│       └── outputs.tf
├── envs/
│   ├── stg/
│   │   └── gconfig/         # Gconfig STG — Seoul
│   │       ├── main.tf
│   │       ├── variables.tf
│   │       ├── outputs.tf
│   │       ├── providers.tf
│   │       └── backend.tf
│   └── prd/
│       └── webapk/          # WebAPK PRD — Singapore
│           ├── main.tf
│           ├── variables.tf
│           ├── outputs.tf
│           ├── providers.tf
│           └── backend.tf
└── .github/
    └── workflows/
        ├── terraform-stg.yml
        └── terraform-prd.yml
```

## Quy trình CI/CD

1. Mọi thay đổi → mở Pull Request
2. GitHub Actions tự động chạy `terraform plan`
3. Review và approve PR
4. Merge → GitHub Actions chạy `terraform apply`

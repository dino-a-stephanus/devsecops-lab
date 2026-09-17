# DevSecOps Lab

Hands-on lab untuk mempelajari dan mempraktikkan prinsip DevSecOps: mengintegrasikan security scanning ke dalam CI/CD pipeline secara otomatis.

## Tujuan

Repo ini dipakai untuk:
- Belajar SAST (Static Application Security Testing) dengan Semgrep/CodeQL
- Belajar SCA (Software Composition Analysis) dengan Dependabot/Trivy
- Belajar container image scanning dengan Trivy/Grype
- Belajar IaC (Infrastructure as Code) scanning untuk Terraform/Bicep
- Mendokumentasikan temuan dan proses remediasi tiap scan

## Struktur Repo

```
devsecops-lab/
├── app/                    # Sample vulnerable app (target scanning)
├── .github/
│   └── workflows/          # Pipeline CI/CD (SAST, SCA, container scan)
├── iac/                    # Contoh Terraform/Bicep untuk IaC scanning
└── docs/                   # Catatan pembelajaran & findings
```

## Tools yang Digunakan

| Kategori | Tool |
|---|---|
| SAST | Semgrep, CodeQL |
| SCA | Dependabot, Trivy |
| Container Scanning | Trivy, Grype |
| IaC Scanning | Checkov / tfsec |
| CI/CD | GitHub Actions |

## Status

🚧 Work in progress — lab ini dibangun bertahap, satu scanner per iterasi.

## Progress Log

- [ ] Setup struktur folder awal
- [ ] Tambahkan sample vulnerable app
- [ ] Workflow SAST (Semgrep)
- [ ] Workflow SCA (Dependabot/Trivy)
- [ ] Workflow container scanning
- [ ] Workflow IaC scanning
- [ ] Dokumentasi findings di /docs

## Catatan

Repo ini bagian dari pembelajaran DevSecOps pribadi — dokumentasi findings dan proses remediasi di folder `/docs` untuk setiap scan yang dijalankan.

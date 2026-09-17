# Security Policy

## Scope

Repo ini adalah lab pembelajaran DevSecOps, mensimulasikan praktik security
yang lazim diterapkan di lingkungan enterprise/regulated industry (mis. perbankan).

## Kontrol Keamanan yang Diterapkan

| Kontrol | Tujuan | Tool |
|---|---|---|
| SAST | Deteksi vulnerability di source code | Semgrep, CodeQL |
| SCA | Deteksi vulnerability di dependency | Trivy, Dependabot |
| Secret Scanning | Cegah kredensial/API key ter-commit | Gitleaks |
| SBOM | Audit trail komponen software (compliance) | Syft (CycloneDX) |
| Container Scanning | Deteksi vulnerability di image | Trivy |
| Code Review Governance | Wajib approval sebelum merge | CODEOWNERS + branch protection |

## Governance / Compliance-as-Code

Branch protection rule yang diterapkan di `main` (dikonfigurasi lewat GitHub
Settings, bukan file — lihat `docs/branch-protection-setup.md`):

- Wajib PR sebelum merge ke `main` (tidak boleh push langsung)
- Wajib minimal 1 approval dari Code Owner
- Wajib semua status check (SAST, SCA, secret scan) lulus sebelum merge
- Wajib branch up-to-date sebelum merge

Ini merefleksikan kontrol yang biasa diminta auditor di industri regulated
(mis. segregation of duties, audit trail perubahan kode).

## Melaporkan Temuan

Karena ini repo lab pribadi, semua findings dicatat di `/docs` menggunakan
template di `docs/findings-template.md`, bukan lewat proses disclosure formal.

## Roadmap Security (Bertahap)

- [x] SAST (Semgrep)
- [x] SCA & container scan (Trivy)
- [x] Secret scanning (Gitleaks)
- [x] SBOM generation (Syft)
- [x] Governance dasar (CODEOWNERS)
- [ ] Branch protection rules (manual setup di GitHub Settings)
- [ ] DAST (untuk app yang di-deploy)
- [ ] IaC policy-as-code (Checkov/tfsec/OPA)
- [ ] Centralized logging — export hasil scan ke SIEM (mis. webhook ke Splunk/ELK)

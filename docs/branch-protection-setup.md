# Setup Branch Protection (Governance Control)

Ini kontrol governance paling dasar di enterprise: mencegah perubahan
langsung ke branch `main` tanpa review dan tanpa lolos security scan.
Diterapkan lewat GitHub Settings (bukan file YAML).

## Langkah Setup

1. Buka repo di github.com → tab **Settings**
2. Di sidebar kiri, klik **Branches**
3. Di bagian "Branch protection rules", klik **Add branch protection rule** (atau **Add rule**)
4. Isi **Branch name pattern**: `main`
5. Centang opsi berikut:
   - ✅ **Require a pull request before merging**
     - ✅ Require approvals → set minimal 1
     - ✅ Require review from Code Owners (memakai file `.github/CODEOWNERS`)
   - ✅ **Require status checks to pass before merging**
     - ✅ Require branches to be up to date before merging
     - Cari dan centang check yang relevan setelah workflow pernah jalan minimal sekali: `Semgrep SAST`, `Trivy Filesystem Scan (SCA)`, `Gitleaks Secret Scan`
   - ✅ **Do not allow bypassing the above settings** (opsional, tapi ini yang bikin rule benar-benar mengikat, termasuk untuk admin repo)
6. Klik **Create** (atau **Save changes**)

## Kenapa Ini Penting (Konteks Enterprise)

Di lingkungan regulated (perbankan, dll), auditor biasanya mengecek:

- **Segregation of duties** — orang yang menulis kode tidak boleh jadi satu-satunya
  yang approve dan merge perubahan itu sendiri
- **Audit trail** — setiap perubahan ke `main` harus tercatat: siapa yang
  request, siapa yang approve, kapan, dan hasil scan security apa
- **No direct push** — mencegah perubahan "siluman" tanpa jejak review

Branch protection rule ini adalah cara GitHub mengimplementasikan ketiga
prinsip itu secara teknis, bukan cuma kebijakan di atas kertas.

## Catatan

Kalau repo masih solo project (cuma kamu sendiri sebagai contributor),
opsi "Require approvals" akan bikin kamu nggak bisa merge PR sendiri kecuali
ada reviewer lain. Untuk lab solo, bisa set approval ke 0 dulu, atau pakai
akun GitHub kedua sebagai reviewer untuk simulasi proses approval yang realistis.

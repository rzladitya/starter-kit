# Architecture-first Starter Kit
## Claude Code + Pstack + Plannotator — New Enterprise Project

Paket siap salin untuk memulai *greenfield project* dengan PRD, NFR, desain arsitektur, approval manusia, lalu implementasi bertahap. **Bukan** aplikasi atau skeleton framework; stack dipilih setelah discovery dan disetujui.

## Quick start (5 langkah)

1. Ekstrak ZIP ini ke folder repository baru (atau salin isinya ke repo kosong).
2. Jalankan:
   ```bash
   git init                 # jika belum di dalam repository Git
   claude
   ```
3. Pastikan `pstack` telah diinstal di Claude Code. Jika belum, jalankan di Claude Code:
   ```text
   /plugin marketplace add cursor/plugins
   /plugin install pstack@cursor-plugins
   /pstack:setup-pstack
   ```
   Di Claude Code, Pstack memakai adapter: beberapa model Cursor dan fitur Cursor-only tidak tersedia. `setup-pstack` perlu memilih model yang benar-benar tersedia pada Claude Code.
4. Pastikan Plannotator terpasang (opsional, tetapi direkomendasikan):
   ```text
   /plugin marketplace add backnotprop/plannotator
   /plugin install plannotator@plannotator
   ```
   Restart Claude Code jika baru memasang plugin. Plan review Plannotator bekerja melalui hook **native Claude Code Plan Mode**. Untuk dokumen Markdown gunakan `/plannotator-annotate docs/PRD.md`; untuk uncommitted diff `/plannotator-review`.
5. Isi ringkasan ide di `docs/PROJECT_BRIEF.md`, lalu salin prompt `prompts/01-discovery.md` ke Claude Code. Jalankan prompt berikutnya hanya setelah fase sebelumnya disetujui.

> Jangan memasukkan *semua* prompt sekaligus. Jalankan satu fase, review artefak, catat keputusan, baru lanjut. Prompt di folder `prompts/` adalah pesan **user** untuk Claude Code; tidak perlu dipindahkan ke `CLAUDE.md`.

## Alur utama dan approval gates

| Fase | Output utama | Kriteria lolos | Reviewer |
|---|---|---|---|
| 0. Discovery | `PROJECT_BRIEF.md`, `PRD.md` | User, masalah, MVP, acceptance criteria jelas | Product owner |
| 1. NFR & constraints | `NFR.md`, `CONSTRAINTS.md` | Kebutuhan keamanan, kinerja, RTO/RPO, data, compliance terisi atau dinyatakan TBD dengan owner | Tech lead / security |
| 2. Architecture | `ARCHITECTURE.md`, `DATA_MODEL.md`, `adr/*` | Alternatif, tradeoff, risiko, deployment dan diagram terbaca | Architect |
| 3. Threat model & implementation plan | `SECURITY_THREAT_MODEL.md`, `IMPLEMENTATION_PLAN.md` | Risiko tinggi punya mitigasi, rencana dipecah per vertical slice | Security / engineering |
| 4. Plan approval | Plannotator review + `DECISION_LOG.md` | User mengonfirmasi **APPROVED** tertulis | Owner |
| 5. Build & verify | Kode, tes, laporan CI, PR | Satu slice berjalan end-to-end; checks nyata dijalankan | Engineering / reviewer |

Lihat `docs/WORKFLOW.md` dan `docs/REVIEW_GATES.md` untuk instruksi rinci. Status awal dokumen adalah **DRAFT**, bukan approved.

## Urutan prompt siap pakai

| File | Kapan digunakan |
|---|---|
| `prompts/01-discovery.md` | Mulai dari ide tanpa menulis kode |
| `prompts/02-nfr-and-constraints.md` | Kunci standar mutu dan kebutuhan nonfungsional |
| `prompts/03-architecture.md` | Eksplorasi opsi, arsitektur & ADR |
| `prompts/04-architecture-challenge.md` | Uji desain secara adversarial dan cek risiko |
| `prompts/05-plan-approval.md` | Buat plan dan ajukan review via Plannotator |
| `prompts/06-first-vertical-slice.md` | Scaffold minimal dan implementasi satu slice setelah approval |
| `prompts/07-code-review.md` | Verifikasi, independent review, dan preview diff |
| `prompts/08-continue-project.md` | Melanjutkan sprint/fitur berikutnya dengan konteks stabil |

## Dokumen mana jadi source of truth?

- Kebutuhan: `docs/PRD.md`.
- Kualitas dan batasan deployment: `docs/NFR.md` dan `docs/CONSTRAINTS.md`.
- Keputusan struktur: `docs/ARCHITECTURE.md` dan `docs/adr/`.
- Scope fase coding dan dependencies: `docs/IMPLEMENTATION_PLAN.md`.
- Persetujuan, perubahan scope, serta pengecualian: `docs/DECISION_LOG.md`.
- Instruksi agent project: `CLAUDE.md` (pendek, merujuk dokumen; jangan tempel semua skill Pstack di sini).

## Safety dan operasional

- Tidak mengklaim check 'PASS' bila perintahnya belum dijalankan; tulis `NOT RUN` beserta alasannya.
- Plannotator memberikan **human review**, bukan bukti bahwa tests, security, atau CI telah lulus.
- Jangan mengaktifkan `autopilot-full`, auto-merge, deploy produksi, atau migrasi destruktif selama fase discovery dan desain.
- Pada project perusahaan, review kebijakan provider AI dan penggunaan informasi sensitif; nonaktifkan fitur share Plannotator bila diperlukan: `PLANNOTATOR_SHARE=disabled`.
- Tentukan runtime checks setelah bahasa/framework dipilih; jangan menyalin perintah lint/test fiktif.

## Dokumentasi resmi
- Pstack: https://github.com/cursor/plugins/tree/main/pstack
- Pstack di Claude Code: https://github.com/cursor/plugins/blob/main/pstack/docs/harness/claude-code.md
- Plannotator: https://github.com/backnotprop/plannotator

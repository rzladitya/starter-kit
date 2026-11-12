# Architecture-first Starter Kit

> **Claude Code + Pstack + Plannotator** untuk memulai *greenfield project* enterprise.

Template dokumen dan prompt untuk membawa ide menjadi PRD, NFR, desain arsitektur, approval manusia, lalu implementasi bertahap.

**Ini bukan aplikasi atau skeleton framework.** Stack teknologi dipilih *setelah* discovery dan disetujui.

---

## Daftar isi

- [Isi repository](#isi-repository)
- [Quick start](#quick-start)
- [Alur fase dan approval gate](#alur-fase-dan-approval-gate)
- [Urutan prompt](#urutan-prompt)
- [Source of truth](#source-of-truth)
- [Safety dan operasional](#safety-dan-operasional)
- [Referensi](#referensi)

---

## Isi repository

```text
.
├── CLAUDE.md                  # Instruksi agent project (ringkas, merujuk ke docs/)
├── README.md
├── docs/
│   ├── STATUS.md              # Fase & status proyek saat ini — baca pertama
│   ├── PROJECT_BRIEF.md       # Ringkasan ide awal
│   ├── PRD.md                 # Kebutuhan produk
│   ├── NFR.md                 # Kebutuhan nonfungsional
│   ├── CONSTRAINTS.md         # Batasan teknis, deployment, compliance
│   ├── ARCHITECTURE.md        # Desain arsitektur
│   ├── DATA_MODEL.md          # Model data
│   ├── SECURITY_THREAT_MODEL.md
│   ├── IMPLEMENTATION_PLAN.md # Rencana per vertical slice
│   ├── DECISION_LOG.md        # Catatan keputusan & approval
│   ├── WORKFLOW.md            # Detail alur kerja per fase
│   ├── REVIEW_GATES.md        # Checklist gate G0–G4
│   └── adr/
│       └── ADR-0001-template.md
└── prompts/                   # Prompt per fase (01–08)
```

---

## Quick start

**1. Siapkan repository**

```bash
git clone https://github.com/rzladitya/starter-kit.git my-project
cd my-project
claude
```

> Atau salin isi kit ini ke repository kosong, lalu jalankan `git init` bila belum ada Git.

**2. Pasang Pstack** (jalankan di dalam Claude Code)

```text
/plugin marketplace add cursor/plugins
/plugin install pstack@cursor-plugins
/pstack:setup-pstack
```

Di Claude Code, Pstack memakai *adapter*: beberapa model dan fitur Cursor-only tidak tersedia. Saat `setup-pstack`, pilih model yang benar-benar tersedia di Claude Code.

**3. Pasang Plannotator** (opsional, direkomendasikan)

```text
/plugin marketplace add backnotprop/plannotator
/plugin install plannotator@plannotator
```

Restart Claude Code setelah memasang plugin. Cara pakai:

| Kebutuhan | Cara |
|---|---|
| Review plan implementasi | Native **Plan Mode** Claude Code (hook Plannotator terbuka otomatis) |
| Review dokumen Markdown | `/plannotator-annotate docs/PRD.md` |
| Review uncommitted diff | `/plannotator-review` |

**4. Mulai discovery**

Isi ringkasan ide di [`docs/PROJECT_BRIEF.md`](docs/PROJECT_BRIEF.md), lalu salin isi [`prompts/01-discovery.md`](prompts/01-discovery.md) ke Claude Code.

> [!IMPORTANT]
> Jangan menjalankan semua prompt sekaligus. Jalankan satu fase → review artefak → catat keputusan → baru lanjut.
> Prompt di `prompts/` adalah pesan **user** untuk Claude Code; tidak perlu dipindahkan ke `CLAUDE.md`.

---

## Alur fase dan approval gate

| Fase | Output utama | Kriteria lolos | Gate | Reviewer |
|---|---|---|---|---|
| **0. Discover** | `PROJECT_BRIEF.md`, `PRD.md` | User, masalah, MVP, dan acceptance criteria jelas; owner mengesahkan scope | G0 | Product owner |
| **1. Constrain** | `NFR.md`, `CONSTRAINTS.md` | Keamanan, kinerja, RTO/RPO, data, compliance terisi atau TBD dengan owner | G1 | Tech lead / security |
| **2. Design** | `ARCHITECTURE.md`, `DATA_MODEL.md`, `adr/*` | Alternatif, trade-off, risiko, deployment, dan diagram terbaca; ADR berstatus Accepted | G2 | Architect |
| **3. Risk & Plan** | `SECURITY_THREAT_MODEL.md`, `IMPLEMENTATION_PLAN.md`, `DECISION_LOG.md` | Risiko tinggi punya mitigasi; plan per vertical slice di-review via Plannotator; owner mencatat **APPROVED** tertulis | G3 | Security / engineering / owner |
| **4. Scaffold** | Project files, test harness, fondasi CI | Inisialisasi minimal setelah approval; build & smoke test benar-benar jalan | — | Engineering |
| **5. First slice** | Kode, tes, docs, laporan CI, PR | Satu slice berjalan end-to-end; checks nyata dijalankan; independent review + Plannotator | G4 | Engineering / reviewer |

Semua dokumen berstatus awal **DRAFT**, bukan approved. Penomoran fase mengacu ke [`docs/WORKFLOW.md`](docs/WORKFLOW.md); checklist gate ada di [`docs/REVIEW_GATES.md`](docs/REVIEW_GATES.md).

---

## Urutan prompt

| # | File | Kapan digunakan |
|---|---|---|
| 01 | [`01-discovery.md`](prompts/01-discovery.md) | Mulai dari ide, tanpa menulis kode |
| 02 | [`02-nfr-and-constraints.md`](prompts/02-nfr-and-constraints.md) | Kunci standar mutu dan kebutuhan nonfungsional |
| 03 | [`03-architecture.md`](prompts/03-architecture.md) | Eksplorasi opsi, arsitektur, dan ADR |
| 04 | [`04-architecture-challenge.md`](prompts/04-architecture-challenge.md) | Uji desain secara adversarial dan cek risiko |
| 05 | [`05-plan-approval.md`](prompts/05-plan-approval.md) | Buat plan dan ajukan review via Plannotator |
| 06 | [`06-first-vertical-slice.md`](prompts/06-first-vertical-slice.md) | Scaffold minimal dan satu slice setelah approval |
| 07 | [`07-code-review.md`](prompts/07-code-review.md) | Verifikasi, independent review, dan preview diff |
| 08 | [`08-continue-project.md`](prompts/08-continue-project.md) | Lanjut ke sprint/fitur berikutnya dengan konteks stabil |

---

## Source of truth

| Topik | Dokumen |
|---|---|
| Kebutuhan produk | [`docs/PRD.md`](docs/PRD.md) |
| Kualitas & batasan deployment | [`docs/NFR.md`](docs/NFR.md), [`docs/CONSTRAINTS.md`](docs/CONSTRAINTS.md) |
| Keputusan struktur | [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md), [`docs/adr/`](docs/adr/) |
| Scope coding & dependencies | [`docs/IMPLEMENTATION_PLAN.md`](docs/IMPLEMENTATION_PLAN.md) |
| Persetujuan, perubahan scope, pengecualian | [`docs/DECISION_LOG.md`](docs/DECISION_LOG.md) |
| Instruksi agent | [`CLAUDE.md`](CLAUDE.md) — tetap ringkas; jangan tempel semua skill Pstack di sini |

---

## Safety dan operasional

- **Tidak ada klaim palsu.** Jangan menulis `PASS` bila check belum dijalankan; tulis `NOT RUN` beserta alasannya.
- **Approval ≠ verifikasi.** Plannotator adalah *human review*, bukan bukti bahwa tests, security, atau CI lulus.
- **Tanpa otomatisasi berisiko di fase awal.** Jangan aktifkan `autopilot-full`, auto-merge, deploy produksi, atau migrasi destruktif selama discovery dan desain.
- **Data sensitif.** Untuk project perusahaan, tinjau kebijakan provider AI. Nonaktifkan fitur share Plannotator bila perlu: `PLANNOTATOR_SHARE=disabled`.
- **Checks nyata.** Tentukan perintah lint/test setelah bahasa/framework dipilih; jangan menyalin perintah fiktif.

---

## Referensi

- [Pstack](https://github.com/cursor/plugins/tree/main/pstack)
- [Pstack di Claude Code](https://github.com/cursor/plugins/blob/main/pstack/docs/harness/claude-code.md)
- [Plannotator](https://github.com/backnotprop/plannotator)

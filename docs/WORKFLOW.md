# Architecture-first Workflow (Greenfield)

## Prinsip
- Discovery mendahului pemilihan stack. Arsitektur dipilih dari kebutuhan produk dan NFR, bukan kebiasaan pribadi.
- Tahap harus menghasilkan artefak yang bisa direview, acceptance criteria, dan bukti keputusan.
- Satu tahap boleh punya eksplorasi atau prototipe, namun jangan mencampurnya dengan implementation production.

| Stage | Tugas agent | Deliverable | Stop / approval gate |
|---|---|---|---|
| 0. Discover | Interview + challenge assumptions | Brief, PRD, scope MVP, user journeys | Owner mengesahkan scope |
| 1. Constrain | Rumuskan SLO/security, RTO/RPO, operasional & cost caps | NFR, CONSTRAINTS | Tech/security setuju target atau TBD+owner |
| 2. Design | Bandingkan 2-3 arsitektur bila ada tradeoff nyata; tentukan domain, components, sequence, data shapes | Architecture, Data Model, ADR | ADR berstatus Accepted |
| 3. Risk & Plan | Threat modeling, data governance, vertical slices, rollback | Threat Model, Implementation Plan | Human approve plan melalui Plannotator/record |
| 4. Scaffold | Inisialisasi minimal setelah approval eksplisit | Project files, test harness, CI foundation | Build & smoke test benar-benar jalan |
| 5. First slice | UI/API/persistence atau jalur end-to-end terkecil | Fungsi nyata, tests, docs, evidence | Independent review + Plannotator + CI |

## Definisi gate
**G0 — Product gate:** target user, 3 problem utama, in/out scope, success metrics, acceptance criteria.  
**G1 — Quality gate:** requirement nonfungsional punya target atau TBD ber-owner; data classes, security stance, deployment preference.  
**G2 — Architecture gate:** diagram, dependencies, deploy view, model data, alternatif, ADR; risiko kritis ditangani.  
**G3 — Implementation authorization:** plan approved oleh orang, decision log mengandung otorisasi spesifik; file `docs/STATUS.md` diperbarui.  
**G4 — Release gate:** test/lint/typecheck/secrets/security yang relevan benar-benar jalan; hasil dan kegagalan tercatat.

## Review in Claude Code + Plannotator
1. Pilih native Claude Code Plan Mode untuk perencanaan implementasi; hook Plannotator akan membuka review ketika agent menyelesaikan plan melalui mekanisme host.
2. Jika plan dibuat sebagai Markdown, jalankan `/plannotator-annotate docs/IMPLEMENTATION_PLAN.md`. Ini review dokumen manual dan **bukan** otomatis menyetujui plan mode.
3. Catat keputusan APPROVED/CHANGES REQUESTED dan rujukan artefak ke `DECISION_LOG.md`.
4. Setelah coding, jalankan `/plannotator-review` untuk memeriksa diff (tidak menggantikan test).

## Multi-agent policy
- Gunakan Pstack `arena` jika pilihan arsitektur benar-benar consequential dan 2+ alternatif berguna; jangan wajib setiap task.
- Gunakan independent reviewer untuk security, permissions, migrations, boundary changes dan bug yang sulit direproduksi.
- Saat berjalan di Claude Code, lihat support nyata (Cursor-only feature mungkin di-skip) dan catat fallback.
- Human approval tetap diperlukan untuk production deploy, destructive data changes, auto-merge.

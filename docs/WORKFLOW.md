# Architecture-first Workflow (Greenfield)

## Prinsip
- Discovery mendahului pemilihan stack. Arsitektur dipilih dari kebutuhan produk dan NFR, bukan kebiasaan pribadi.
- Tahap harus menghasilkan artefak yang bisa direview, acceptance criteria, dan bukti keputusan.
- Satu tahap boleh punya eksplorasi atau prototipe, namun jangan mencampurnya dengan implementation production.

> File ini adalah acuan tunggal penomoran fase dan checklist gate. README, `CLAUDE.md` dan `STATUS.md` mengikuti file ini.

| Stage | Tugas agent | Deliverable | Stop / approval gate |
|---|---|---|---|
| 0. Discover | Interview + challenge assumptions | Brief, PRD, scope MVP, user journeys | **G0** — owner mengesahkan scope |
| 1. Constrain | Rumuskan SLO/security, RTO/RPO, operasional & cost caps | NFR, CONSTRAINTS | **G1** — tech/security setuju target atau TBD+owner |
| 2. Design | Bandingkan 2-3 arsitektur bila ada tradeoff nyata; tentukan domain, components, sequence, data shapes | Architecture, Data Model, ADR | **G2** — ADR berstatus Accepted |
| 3. Risk & Plan | Threat modeling, data governance, vertical slices, rollback | Threat Model, Implementation Plan | **G3** — human approve plan melalui Plannotator/record |
| 4. Scaffold | Inisialisasi minimal setelah approval eksplisit | Project files, test harness, CI foundation | Build & smoke test benar-benar jalan |
| 5. First slice | UI/API/persistence atau jalur end-to-end terkecil | Fungsi nyata, tests, docs, evidence | **G4** — independent review + Plannotator + CI |

## Gate checklist (Definition of Ready)

### G0 — Product gate (fase 0)
Target user, 3 problem utama, in/out scope, success metrics, acceptance criteria.
- [ ] Primary user and top jobs-to-be-done are concrete.
- [ ] MVP has verifiable acceptance criteria.
- [ ] Non-goals and dependencies are explicit.
- [ ] Open questions have owners.

### G1 — Quality gate (fase 1)
Requirement nonfungsional punya target atau TBD ber-owner; data classes, security stance, deployment preference.
- [ ] Deployment constraints, sensitive data policy, auth/access model captured.
- [ ] Target performance, capacity and uptime are measured or assigned for discovery.
- [ ] RTO/RPO and data retention requirements decided or owned as TBD.
- [ ] Cost assumptions trace to source or marked provisional.

### G2 — Architecture gate (fase 2)
Diagram, dependencies, deploy view, model data, alternatif, ADR.
- [ ] At least one simpler design considered, not overengineered.
- [ ] Component responsibilities and trust boundaries documented.
- [ ] Contract + domain shapes + failure modes documented.
- [ ] Significant tech choice has ADR with rejected alternatives.
- [ ] Testability, operability, rollback and migration reviewed.

### G3 — Implementation authorization (fase 3)
Plan approved oleh orang, decision log mengandung otorisasi spesifik; `docs/STATUS.md` diperbarui.
- [ ] Threat model critical issues resolved or explicitly blocked.
- [ ] `IMPLEMENTATION_PLAN.md` has a single, bounded first vertical slice.
- [ ] Native Plan Mode review (if used) has finished; feedback incorporated.
- [ ] Plannotator annotation review or explicit human review recorded.
- [ ] `DECISION_LOG.md` contains clear human APPROVED record for coding.

### G4 — Release gate (fase 5)
Test/lint/typecheck/secrets/security yang relevan benar-benar jalan; hasil dan kegagalan tercatat.
- [ ] Tests, static checks, integration checks and security scans executed and reported.
- [ ] Diff reviewed using human review / `/plannotator-review`.
- [ ] Critical issue disposition recorded; no fake green checks.
- [ ] No unapproved merge/deploy/destructive migration.

### Urutan review manusia
PRD → NFR → Architecture + ADR → Threat model → Plan → Code diff → CI → Release decision.

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

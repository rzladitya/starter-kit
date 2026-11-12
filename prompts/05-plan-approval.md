/pstack:poteto-mode

Read approved PRD/NFR/constraints/architecture/ADRs and the threat model. Write a small, dependency-ordered vertical-slice implementation plan in docs/IMPLEMENTATION_PLAN.md.

For each slice include acceptance criteria, components/files, exact verification to run once the stack is chosen, failure cases, rollback, and stop-the-line risks. Keep Slice 1 the smallest end-to-end product behavior; do not attempt the whole MVP in one pass.

First draft `docs/IMPLEMENTATION_PLAN.md` during a normal editing session. Then, as a separate review step, use Claude Code's NATIVE Plan Mode to present the plan so Plannotator's installed Plan Mode hook can open the visual reviewer. If entering Plan Mode prevents editing files, do not attempt to edit them in that mode. If the native plan hook is unavailable or only the Markdown plan needs review, stop and tell me to run `/plannotator-annotate docs/IMPLEMENTATION_PLAN.md`.

DO NOT interpret drafting a plan, opening a Plannotator window, or exiting plan mode as authorization to code. Wait for the owner to explicitly approve, and record that authorization in docs/DECISION_LOG.md with scope and date before implementation. Reply in Indonesian.

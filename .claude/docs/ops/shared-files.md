---
file_class: CLASS_A_LIVE
owner: Command
write_rule: OVERWRITE
purpose: Reference document for the shared file set between BrightSteps and agent-os. Lists all files under byte-identity enforcement and documents the Sentinel comparison protocol.
---

# Shared Files — Byte-Identity Enforcement Reference

## Shared file set (16 files)

All files listed below must be byte-identical between BrightSteps and agent-os. Agent-os is the canonical source. BrightSteps may not independently amend these files.

| # | Path | Type |
|---|------|------|
| 1 | `.claude/commands/dispatch/atlas.md` | Dispatch command |
| 2 | `.claude/commands/dispatch/forge.md` | Dispatch command |
| 3 | `.claude/commands/dispatch/sentinel.md` | Dispatch command |
| 4 | `.claude/commands/dispatch/compass.md` | Dispatch command |
| 5 | `.claude/commands/govern/activate-slice.md` | Governance command |
| 6 | `.claude/commands/govern/close-slice.md` | Governance command |
| 7 | `.claude/commands/govern/express.md` | Governance command |
| 8 | `.claude/commands/govern/init-project.md` | Governance command |
| 9 | `.claude/commands/govern/plan.md` | Governance command |
| 10 | `.claude/commands/review/submission.md` | Review command |
| 11 | `.claude/docs/agents/COMMAND_ID.md` | Agent identity |
| 12 | `.claude/docs/agents/ATLAS_ID.md` | Agent identity |
| 13 | `.claude/docs/agents/FORGE_ID.md` | Agent identity |
| 14 | `.claude/docs/agents/SENTINEL_ID.md` | Agent identity |
| 15 | `.claude/docs/agents/COMPASS_ID.md` | Agent identity |
| 16 | `.claude/docs/chains/TEMPLATE.md` | Chain template |

## Governance rule

When agent-os amends any shared file, the same amendment must be applied to BrightSteps before the next slice that touches shared-file-dependent behavior.

## Sentinel byte-identity enforcement protocol

1. For each file in the shared file set (16 files), compare the BrightSteps version against the agent-os version.
2. **Comparison method:** `diff` or equivalent byte-level comparison.
3. **Comparison paths:** `C:/Users/Cyronick/Documents/brightsteps/.claude/[path]` vs `C:/Users/Cyronick/Documents/agent-os/.claude/[path]`
4. **Finding severity:** Any difference = **HIGH** finding (unauthorized divergence).
5. Zero differences across all 16 files = CLEAR.

## Notes

- `.gitattributes` with `* text=auto` is present to ensure consistent line-ending normalization.
- Master shared-files reference is maintained in agent-os at `.claude/docs/ops/shared-files.md`.

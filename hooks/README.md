# claude-obsidian Hooks

Plugin hooks for the claude-obsidian wiki vault. All hooks are defined in `hooks.json`.

## Events

| Event | Type | Purpose |
|---|---|---|
| `SessionStart` | command + prompt | Loads `wiki/hot.md` into context. Command type runs `[ -f wiki/hot.md ] && cat wiki/hot.md` as the canonical safety check (works for non-vault sessions without erroring). Prompt type complements with semantic context restoration. Matcher: `startup\|resume`. |
| `PostCompact` | prompt | Re-loads `wiki/hot.md` after context compaction. Hook-injected context does NOT survive compaction (only `CLAUDE.md` does), so this hook restores the hot cache mid-session. |
| `PostToolUse` | command | Auto-commits any wiki/ or .raw/ changes after Write or Edit tool calls. **Opt-in** via `CLAUDE_OBSIDIAN_AUTO_COMMIT=1` (see below). Also guarded by `[ -d .git ]` (no error in non-git dirs) and `git diff --cached --quiet` (no empty commits). |
| `Stop` | prompt | Updates `wiki/hot.md` at the end of every Claude response with a brief summary of what changed. |

## Opt-in Auto-Commit

The `PostToolUse` auto-commit is disabled by default. Set `CLAUDE_OBSIDIAN_AUTO_COMMIT=1` in your environment (in `.envrc`, a shell profile, or per-session) to enable it. Auto-commits help during ingestion sessions where many wiki pages are created in sequence and per-file checkpoints provide a safety net. They are noisy during deliberate multi-file edits, because each `Write` or `Edit` produces its own commit and `git add wiki/ .raw/` can sweep unrelated modified files in. Leave the flag unset when you want explicit control over commit boundaries; set it when you want automatic snapshots.

## Known Issue: Plugin Hooks STDOUT Bug

`anthropics/claude-code#10875` documents that **plugin hook STDOUT may not be captured** by Claude Code, while identical inline hooks in `settings.json` work correctly.

**Impact**: If this bug is active in your Claude Code version, the prompt-type SessionStart and PostCompact hooks may not inject context as expected.

**Workaround**: The command-type SessionStart hook (`cat wiki/hot.md`) is the canonical safety check. It relies on STDOUT capture for context injection, so test against this issue if hot cache restoration fails. As a fallback, copy the hook config from `hooks.json` into your user-level `~/.claude/settings.json` instead of relying on plugin hooks.

**Test for the bug**: After installing the plugin, open a fresh Claude Code session in a directory containing a populated `wiki/hot.md`. Ask Claude "what's in the hot cache?". If Claude has no idea, the STDOUT bug is active in your version.

## Non-Vault Sessions

The SessionStart command hook uses `[ -f wiki/hot.md ] && cat wiki/hot.md || true` so it always exits 0, even when no vault is present. This makes the plugin safe to install globally without breaking non-vault Claude Code sessions.

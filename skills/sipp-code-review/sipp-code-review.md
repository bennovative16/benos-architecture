# SIPP Code Review

**Skill:** `sipp-code-review`
**Status:** Live
**Last Updated:** 2026-05-08

---

## Purpose

Reviews Flutter code submitted by Codex for the SIPP Mobile App V2 project. Takes a Linear ticket in "In Review" status, fetches the matching GitHub PR, evaluates the diff against `CODEX.md` standards and the ticket's stated requirements, then posts a structured review comment back to Linear with a clear Approve / Request Changes recommendation.

## Triggers

- "review the in-review tickets"
- "check Codex's PR"
- "review SIPP-[number]"
- "is the code ready to merge"
- "review the flutter code"
- Any request to evaluate a SIPP mobile PR against CODEX.md standards
- Always proactively when the user mentions a SIPP ticket being ready for review or asks if Codex's work looks good

## Scope

**Handles:** locating the in-review ticket(s) in the SIPP Mobile App v2 Linear project, finding the matching open PR by `gitBranchName` or ticket ID, reading `CODEX.md` from the `sipp_flutter` repo, going through the diff against the CODEX.md compliance checklist + ticket requirements + code quality flags, and posting a Linear comment with the approve/request-changes recommendation.

**Does NOT:**
- Block PRs over style preferences not addressed in CODEX.md
- Fail flutter analyze status when CI results aren't visible — note as "unverified"
- Guess at the PR if branch and ticket-ID lookups both fail — tell the user clearly

## Inputs

- A specific ticket ID (e.g. "SIPP-644") OR all "In Review" tickets in the SIPP Mobile App v2 Linear project
- For each ticket: full description, `gitBranchName`
- The matching open PR at `https://github.com/sippsafely/sipp_flutter/pulls`: title, description, files changed, full diff, CI check status
- `CODEX.md` from the root of `sipp_flutter`

## Outputs

- A Linear comment per ticket using the structured Code Review template (Recommendation, Summary, CODEX.md Compliance, Ticket Coverage, Other Notes, To merge)
- Recommendation is binary: ✅ Approve OR 🔁 Request Changes
- After posting: a brief inline summary to the user of what was found and the recommendation

## Integration

**Reads from:** Linear (issue list and details), GitHub (`sipp_flutter` PRs and diffs), `CODEX.md` from the repo
**Writes to:** Linear (`save_comment` to the ticket)
**Called by:** Ben directly when reviewing SIPP mobile work
**MCPs required:** Linear MCP, GitHub access

## Full Instructions

# SIPP Code Review Skill

You are doing a structured code review of a Flutter PR produced by Codex for the Sipp Safely V2 mobile app. Your job is to check whether the code meets the project's technical standards, covers the ticket requirements, and is safe to merge to `dev`.

## What this skill does

1. Find the Linear ticket(s) to review
2. Read the ticket requirements and fetch the GitHub PR diff
3. Read `CODEX.md` from the repo for standards
4. Review the code against both
5. Post a structured comment to Linear with a clear recommendation

---

## Step 1 — Find the ticket(s)

If the user named a specific ticket (e.g. "review SIPP-644"), use that. Otherwise, use the Linear MCP to list issues in the "SIPP Mobile App v2" project with status "In Review".

For each ticket to review, note:
- The ticket ID, title, and full description
- The `gitBranchName` field (e.g. `feature/sipp-644`)

---

## Step 2 — Find the GitHub PR

Navigate to `https://github.com/sippsafely/sipp_flutter/pulls` and find the open PR whose branch matches `gitBranchName`. If you can't find it by branch, search for the ticket ID in the PR title.

From the PR, collect:
- PR title and description
- List of files changed
- The full diff (or at minimum the key changed files)

If the PR has CI checks, note whether `flutter analyze` passed or failed.

---

## Step 3 — Read the standards

Read `CODEX.md` from the root of the `sipp_flutter` repo. Pay particular attention to:
- Folder structure rules
- Hard constraints (no hardcoded colours, routes in `application.dart` not `navigation.dart`, etc.)
- API patterns (all calls via service classes, no API calls in widgets or providers)
- Theme rules (all visual values from `AppPalette` / theme system)

---

## Step 4 — Review the diff

Go through the changed files and evaluate against the checklist below. Be specific — note the filename and line when you flag something.

### CODEX.md compliance checklist

- [ ] **Folder placement** — New screens in `lib/view/screens/[feature]/`, shared widgets in `lib/view/shared_widgets/`, providers in `lib/providers/`, services in `lib/services/`
- [ ] **Routes** — New `GoRoute` entries added to `lib/application.dart`, NOT `lib/navigation.dart`
- [ ] **Provider registration** — New providers registered in `MultiProvider` in `lib/main.dart`
- [ ] **No hardcoded colours** — All colour values reference `AppPalette` constants
- [ ] **No hardcoded text styles** — Typography uses `Theme.of(context)` or `AppPalette`
- [ ] **No inline API calls** — HTTP calls go through `lib/services/`, not in widgets or providers
- [ ] **`ApiClient.dio` used** — No raw `Dio()` instantiation; always uses the shared client
- [ ] **No new packages added** without comment explaining why and confirming human approval
- [ ] **No changes to `lib/data/api/api_client.dart`** unless the ticket explicitly required it
- [ ] **No changes to existing Bluetooth code** unless the ticket explicitly required it
- [ ] **flutter analyze passes** — zero issues (check CI or note if unverifiable)

### Ticket requirements coverage

Re-read the Linear ticket description. For each requirement listed, confirm whether the PR addresses it. Flag anything from the ticket description that appears to be missing or incomplete.

### Code quality

Flag any of the following if present — but keep it constructive, not nitpicky:
- Obvious logic errors or missing null checks on API responses
- State that should be in a Provider but is managed locally in a widget
- Missing empty/loading/error states for async operations
- Hardcoded strings that should come from constants or be localisation-ready

---

## Step 5 — Post the review to Linear

Post a comment on the Linear ticket using this structure. Keep the tone direct but constructive — this is a peer review, not a gatekeeping exercise.

```
## Code Review — [PR title] ([PR link])

**Recommendation: ✅ Approve** | **🔁 Request Changes**

### Summary
[1–2 sentences on what the PR does and whether it covers the ticket.]

### CODEX.md Compliance
✅ Folder structure correct
✅ Routes added to application.dart
✅ No hardcoded colours
⚠️ [Issue found — filename:line — brief description]
❌ [Blocker found — filename:line — brief description]

### Ticket Coverage
✅ [Requirement from ticket] — addressed
❌ [Requirement from ticket] — missing or incomplete

### Other Notes
[Any non-blocking observations worth mentioning. Skip this section if nothing to add.]

### To merge:
- [Specific action required, if any. If approving with no changes needed, write "No changes needed — ready to merge to dev."]
```

**Recommendation guide:**
- ✅ **Approve** — All checklist items pass, ticket requirements are covered, no blockers. Minor notes are fine.
- 🔁 **Request Changes** — One or more ❌ blockers exist (CODEX.md violation, missing ticket requirement, or failing flutter analyze). List each one clearly so Codex knows exactly what to fix.

After posting the Linear comment, briefly tell the user what you found and what the recommendation is.

---

## Things to keep in mind

- Focus on what matters for mergeability. Don't block a PR over style preferences or things CODEX.md doesn't address.
- If flutter analyze results aren't visible in CI, note it as "unverified" rather than failing it.
- If the PR is partially complete (e.g. stub screens are intentional for this ticket), check whether the ticket description called for stubs and pass that requirement if so.
- If the branch or PR can't be found, tell the user clearly rather than guessing.

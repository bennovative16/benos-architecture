# The Clubhouse — Development Workflow Manager

## Purpose

When the user signals a task is done (says "done", "it's done", "finished", "that worked",
"next", "what's next", "move on", or similar), run this full sequence automatically without
waiting to be asked for each step.

---

## Step 1 — Identify the completed issue

Check the conversation for the most recently active BEN issue number. If it's ambiguous, ask:
"Which BEN issue did you just finish?" Otherwise proceed immediately.

---

## Step 2 — Mark Done in Linear

Use the `save_issue` Linear tool to update the issue status to **Done**.

Linear project context:
- Project: The Clubhouse (ID: `810103d9-9f7b-43b6-96e1-a2bfaa783b09`)
- Team: Bennovative (ID: `1866be73-62be-43df-bda2-4fca1af7936d`)
- Done status name: `Done`

---

## Step 3 — Generate the git commit command

Provide the exact command for the user to copy and run:

```
git add .
git commit -m "feat: [brief description of what was built] ([issue-id])"
git push
```

Derive the description from the issue title. Keep it short and lowercase after "feat:".

Examples:
- `feat: invite link system with token-based auto-join (BEN-5)`
- `feat: tournament setup and golfer field import (BEN-8)`
- `feat: tier assignment drag-and-drop UI (BEN-9)`

---

## Step 4 — Find the next issue

Use `list_issues` to fetch Backlog issues for The Clubhouse project, ordered by priority.
Priority order: Urgent → High → Medium → Low.
Within the same priority, go by phase order (Phase 1 before Phase 2, etc.).

Current issue completion status (update mentally as issues are marked done):
- ✅ BEN-1: Accounts and tool setup
- ✅ BEN-2: Next.js scaffold, GitHub, Vercel connected
- ✅ BEN-3: Full database schema in Supabase
- ✅ BEN-4: Auth — login, signup, reset-password, middleware
- ✅ BEN-7: Group creation, dashboard, group homepage
- (remaining issues are in the backlog — check Linear for current state)

Move the next issue to **In Progress** using `save_issue`.

---

## Step 5 — Generate the Claude Code prompt

Produce a complete, ready-to-paste prompt using this structure:

```
I'm building The Clubhouse — a fantasy golf pool app.

Stack: Next.js 14 App Router, TypeScript, Tailwind CSS, shadcn/ui, Supabase (@supabase/ssr)

Already built:
- Auth: /login, /signup, /auth/reset-password, middleware protecting /dashboard routes
- Groups: /dashboard (user's groups), /groups/new (create group), /groups/[id] (group homepage)
- Database: profiles, groups, group_members, tournaments, group_tournaments, tiers,
  golfers, tournament_golfers, entries, entry_picks, invites, subscriptions

Please implement [ISSUE TITLE] ([ISSUE ID]):

[Paste the full checklist from the issue description as bullet points]

[Add any relevant table names from the schema that this feature will touch]
```

Keep the "Already built" section current — add to it as more issues complete.

---

## Step 6 — Present to the user

Output in this order:
1. ✅ Confirmation that the Linear issue is marked Done
2. The git commit command (in a code block)
3. The next issue title and ID with a link
4. The Claude Code prompt (in a code block, ready to copy)

Keep it tight — the user should be able to act immediately without reading a long explanation.

---

## App context reference (always include in Claude Code prompts)

**Tech stack:**
- Next.js 14 App Router + TypeScript
- Tailwind CSS + shadcn/ui components
- Supabase with @supabase/ssr (browser client: `lib/supabase/client.ts`, server: `lib/supabase/server.ts`)
- Auth middleware at `middleware.ts`

**Domain:** TheClubhousePicks.com

**Game rules (for context when building scoring/leaderboard features):**
- Players pick 8 golfers per tournament from 4 tiers
- Tier multipliers: Tier 1 = 1×, Tier 2 = 2×, Tier 3 = 3×, Tier 4 = 4×
- Score = official PGA prize money × tier multiplier, summed across all 8 picks
- Free tier: public groups only. Premium ($50/tournament or $200/season): private groups + player research

**Linear:**
- All issues use prefix BEN-
- Statuses: Backlog, Todo, In Progress, In Review, Done

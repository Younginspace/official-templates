# EdgeSpark Templates — Community Extensions

A friendly fork of [`edgesparkhq/official-templates`](https://github.com/edgesparkhq/official-templates) that adds **5 community templates** alongside the official `fullstack` and `bounty-tasks` starters.

Every template is a plain EdgeSpark app directory — `server/` + `web/` + `configs/` + `edgespark.toml` — so you can inspect it, fork it, or copy pieces out without any custom template format.

> Pull requests to merge these templates upstream are open: [#2](https://github.com/edgesparkhq/official-templates/pull/2) (login templates) and [#3](https://github.com/edgesparkhq/official-templates/pull/3) (game + waitlist). Until they land, point `--template` at this fork. **Official adoption is welcome — that's the whole intent.**

## What's Inside

| Template | Pattern | What's wired |
|---|---|---|
| **`fullstack`** | Generic starter | (upstream) blank Hono server + React Vite SPA |
| **`bounty-tasks`** | Working app | (upstream) bounty/tasks reference implementation |
| **`login-frosted-glass`** ✨ | Auth | Glassmorphism over a live WebGL water-caustic shader. Ships email/password **plus 4 OAuth providers wired** (GitHub, Google, Discord, GitLab). |
| **`login-aurora-split`** ✨ | Auth | Two-column layout — animated aurora curtains and topographic contour lines on the left, sign-in form on the right. Email/password by default. |
| **`login-terminal-cli`** ✨ | Auth | Monospace terminal aesthetic that matches the EdgeSpark CLI / agent feel. Email/password by default. |
| **`flappy-bird-3d`** ✨ | Game + Leaderboard | A working WebGL Flappy Bird kept in `web/src/game/`, a public leaderboard API, three difficulty tiers, and a D1-backed `scores` table with migrations checked in. Replace the game directory and the leaderboard keeps working. |
| **`waitlist-admin`** ✨ | Waitlist + Admin Dashboard | Public email capture + admin sign-in (`/admin/login`) gated by `ADMIN_EMAIL`. Admin dashboard ships stat cards, an inline 7-day trend chart, source breakdown, paginated signups list with email search, and one-click CSV export. |

✨ = added by this fork.

## Use a Template

The shape is the same for every template — official or community:

```bash
edgespark init <project-name> --agent <agent> --template <template-source>
```

For the templates added by this fork:

```bash
# Login screens
edgespark init my-app --agent claude --template github:Younginspace/official-templates/login-frosted-glass
edgespark init my-app --agent claude --template github:Younginspace/official-templates/login-aurora-split
edgespark init my-app --agent claude --template github:Younginspace/official-templates/login-terminal-cli

# Game + leaderboard
edgespark init my-game --agent claude --template github:Younginspace/official-templates/flappy-bird-3d

# Waitlist with admin dashboard
edgespark init my-waitlist --agent claude --template github:Younginspace/official-templates/waitlist-admin
```

`--agent` can be any short agent name: `claude`, `codex`, `gemini`, `cursor`, `copilot`, etc. The CLI uses the value to decide whether to write `CLAUDE.md`, `GEMINI.md`, or `AGENTS.md` into the new project.

Once these PRs are merged upstream, you can drop the `Younginspace/` prefix and use the official shorthand:

```bash
edgespark init my-app --agent claude --template login-frosted-glass
```

## What `init` Does

When you run `edgespark init --template`:

1. The CLI copies or downloads the template into your new project directory.
2. A fresh EdgeSpark project is created on the platform.
3. `project_id` in `edgespark.toml` is rewritten with the new project's id.
4. The rest of the app structure is preserved verbatim.
5. The CLI prints a tailored next-steps list — `npm install` for `server/` and `web/`, plus any combination of `var set`, `secret set`, `db migrate`, `auth apply`, and `deploy` that this specific template needs.

For `flappy-bird-3d` and `waitlist-admin`, the next-steps include `db migrate` (their `scores` / `signups` tables ship with migrations under `server/drizzle/`). For `login-frosted-glass`, you'll be prompted for OAuth client IDs and secrets. The other login templates ship as email/password only — no extra credentials required.

## Template Principles

Templates here aim to be:

- **Practical** — real working starting points, not architectural placeholders
- **Aligned** — follow current EdgeSpark conventions (`AGENTS.md`, `edgespark.toml`, `server/src/defs/runtime.ts`, etc.)
- **Inspectable** — standard EdgeSpark app directories, no custom template engine
- **Maintainable** — small enough to keep current as the platform evolves

## Contributing

PRs welcome — design improvements, additional templates, bug fixes, doc tweaks. Open an issue first if you're proposing a new template so we can align on whether it fills a gap the existing catalog doesn't.

If you're an EdgeSpark maintainer reading this and want to take any of the community templates upstream, please do — you can either merge the open PRs or cherry-pick whichever subset you want.

## License

MIT — same as the upstream repository.

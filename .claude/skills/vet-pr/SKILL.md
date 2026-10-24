---
name: vet-pr
description: Rigorous checklist for triaging PRs on the awesome-real-estate list. Use whenever asked to review, process, triage, or vet open pull requests on this repo — an HTTP 200 on the submitted link is not sufficient by itself.
---

# Vetting a PR on this repo

This is a community "awesome list." The barrier to entry is low (anyone can open a PR adding one line), which means the volume of low-effort, AI-generated, or spam/SEO submissions is high. A link returning HTTP 200 is the *weakest* signal, not the deciding one — treat it as necessary, never sufficient.

For every PR, in this order, run ALL of the following checks — do not skip the author check because the link looks fine, and do not skip the content check because the author looks fine. A single passing check does not offset a failing one.

## 1. Link liveness AND substance
- `curl -sIL` the URL — non-200/3xx final status, parked-domain redirect, or a bare "coming soon" page is an automatic fail.
- Fetch the actual page body, not just headers — and for anything that presents as a directory, listing, "reviews," or "tools" hub, **fetch a listing/inner page too, not just the homepage**. Checking that the homepage `<title>` matches the PR's claim is not enough — the homepage is marketing copy; the listing page is where mass-generated content shows itself.
- On that listing/inner page, look for content-farm tells: dozens/hundreds of entries with near-identical templated one-sentence descriptions (e.g. "X is a Y combining A, B, C, and D"); categories spanning unrelated verticals (NFT tools, retirement planning, video editing, startup communities alongside real estate) despite the site framing itself as niche-specific; boilerplate trust-signal phrases ("no sponsored rankings," "independent reviews," "no pay-to-play") that are themselves a genre marker of SEO directory sites, not evidence of substance. A site that is *itself* a generic multi-vertical AI-tool directory reskinned toward real estate fails "on-topic" and "genuine resource" even though the domain resolves and the title superficially matches — this is a CLOSE, not a formatting nitpick.
- Generic marketing copy with no verifiable substance ("AI-powered," "revolutionary," "graded by AI") on an otherwise single-purpose product page is a yellow flag, not by itself a fail — corroborate against #2.
- **`curl` cannot see JS-rendered content.** Many sites are client-rendered SPAs — `curl` returns a near-empty shell (a bare "Redirecting...", or a `<body>` that's almost all `<script>` tags with a few hundred characters of real text once stripped). If stripping tags/scripts from the curl body yields little to no real text, that is NOT evidence the content is fine — it means the check wasn't actually performed. Do not write "title matches claim" as if that settles it when the body is a JS shell. In that case, either (a) render the page with the `mcp__claude-in-chrome__*` browser tools (`navigate` + `get_page_text` — load them via `ToolSearch` if not already available) and read the real text, or (b) if browser tools aren't practical in this run (e.g. parallel forks risking tab collisions on a shared browser session), say explicitly in the verdict "content not independently verified — JS-rendered, curl saw only a shell" rather than asserting the content is substantive. An unverified claim is not the same as a verified one — never blur the two in the verdict.
- If using the browser tools, create your own tab (`tabs_create_mcp`) rather than reusing one, and close it when done — don't run browser checks in parallel across multiple forks against the same browser session, since tabs can collide.

## 2. Author signal — mandatory for every PR, not just ones you're inclined to merge
Run `curl -s https://api.github.com/users/<login>` and read `name`, `bio`, `company`, `created_at`, `public_repos`, `followers`. Look for:
- Bio/company full of decorative unicode, disconnected buzzword salad, or claims unrelated to the submitted product (e.g. "Pegasus detector," "77+ MCP tools," symbol-stuffed company names). This is a strong spam/noise signal even if the linked site itself loads fine — flag it explicitly and do not silently fold it into a MERGE verdict.
- A brand-new account (days old) is *not* disqualifying on its own — legitimate indie builders often are. But a brand-new account **combined with** a noisy/irrelevant bio, or **combined with** an unfilled PR template, raises the bar for scrutiny.
- A bio/company that plausibly matches the submitted product (e.g. "Founder of X — the thing they're submitting") is a positive signal, not just neutral.

State the author-check result explicitly in your verdict for every single PR — "author checked, no red flags" or name the specific red flag. Never write a verdict that only cites the link check.

## 3. Duplicate check
`grep -i` for the domain root and the product name in README.md — but also scan for near-duplicates (same author/product submitted under a different URL or section, e.g. two PRs from the same person for the same resource in different sections).

## 4. Format compliance (contributing.md)
- One line, ends with a period, doesn't just restate the name as the description.
- Correct existing section, or a reasonable new-section proposal.
- Matches the list's existing punctuation style (plain " - " separator, not em dash) and doesn't break blank-line list structure (would fail `awesome-lint`).

## 5. Mergeable state
`gh pr view <n> --json mergeable` — note conflicts and what's likely causing them (another PR touching the same section).

## Verdict
One of: MERGE / REQUEST_CHANGES (state exactly what's needed) / REBASE_NEEDED / CLOSE (state exactly why). Be decisive. When link + format pass but the author check turns up a real red flag, do not default to MERGE — surface it as a judgment call for the maintainer rather than asserting confidence you don't have.

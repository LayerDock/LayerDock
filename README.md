<div align="center">

<a href="https://layerdock.io">
  <img src="public/logo/lockup-horizontal/svg/lockup-black-typo.svg" alt="LayerDock" height="56">
</a>

<br><br>

### Website feedback, done right.

**Pin comments on any live website. Every pin captures the screenshot, CSS selector, viewport, console logs and network requests, then hands it to Claude Code or Cursor over MCP. Nothing to install.**

<br>

[![Start for free](https://img.shields.io/badge/Start_for_free-layerdock.io-6C47FF?style=for-the-badge)](https://layerdock.io)
[![Indie Hackers](https://img.shields.io/badge/Indie_Hackers-LayerDock-0E2439?style=for-the-badge&logo=indiehackers&logoColor=white)](https://www.indiehackers.com/product/layerdock)
[![Chrome](https://img.shields.io/badge/Layerdock_for_Chrome-optional-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white)](https://layerdock.io)

![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=flat-square&logo=supabase&logoColor=white)
![Cloudflare Workers](https://img.shields.io/badge/Cloudflare_Workers-F38020?style=flat-square&logo=cloudflare&logoColor=white)
![MCP](https://img.shields.io/badge/MCP-ready-6C47FF?style=flat-square)

<br>

<img src="public/shots/hero-dashboard.png" alt="LayerDock dashboard: pins on a live website with the review sidebar open" width="100%">

</div>

---

## What is LayerDock?

A browser-based website feedback and visual bug reporting tool for agencies, freelancers, product teams and QA.

Your client opens a link, clicks the thing that is wrong, and types what they want. You get everything a developer needs to fix it, without a single "can you send me a screenshot?" email.

> **See it. Capture it. Ship it.**

---

## Features

### 📍 Pin comments on the live site

<img src="public/features/feedback.webp" alt="A comment pinned to an element on a live page" width="100%">

Pins stick to the element, not the pixel, and re-anchor after redeploys. Reviewers switch between desktop, tablet and mobile viewports without leaving the page.

### 🤖 Context captured automatically

<img src="public/features/diagnostics.webp" alt="A pin with screenshot, CSS selector, viewport, console logs and network requests" width="100%">

Screenshot · CSS selector · viewport · console logs · network requests · browser and OS. Recorded on every pin, whatever the plan.

### 🔌 Hand pins to your coding agent

<img src="public/features/mcp.webp" alt="A pin opened in Claude Code or Cursor through MCP" width="100%">

The LayerDock MCP server lets **Claude Code** and **Cursor** read a pin, its selector, screenshot and console trace, reply to it and move it to resolved.

### ✏️ Draw, record and inspect

<table>
<tr>
<td width="33%"><img src="public/features/draw.webp" alt="Draw on a screenshot"><br><b>Draw</b><br>Pen, arrow, highlight, text, eraser.</td>
<td width="33%"><img src="public/features/capture.webp" alt="Screen recording"><br><b>Capture</b><br>Screen recordings up to 3 minutes, with audio.</td>
<td width="33%"><img src="public/features/inspect.webp" alt="Inspect an element"><br><b>Inspect</b><br>Element details and in-browser accessibility checks.</td>
</tr>
</table>

### 🔗 Share with clients, no account needed

Clients review through a link. They never sign up, and your internal team notes stay private. Each client sees only their own pins.

---

## How it works

1. **Create a dock**: one website you are reviewing.
2. **Add a layer**: a draft or build to review.
3. **Share the link** with clients and teammates.
4. **Triage and assign** pins through Open, In review, Changes requested, Approved and Resolved.
5. **Ship the fix** with the full technical context attached.

Try it without an account: paste a URL at [layerdock.io/try](https://layerdock.io/try) and get a working review link.

---

## Everything else

- **Dashcam:** a rolling 60 second buffer, so a bug that already happened is still on tape
- **Multi-viewport:** desktop, tablet, mobile, free roam
- **Integrations:** Slack, Jira, Linear, GitHub, Trello
- **Team roles and permissions:** who can edit, assign and invite
- **Email digests:** batched, never one email per pin
- **Layerdock for Chrome:** optional launcher for Pro and Agency, adds a dock from the site you are on

---

## Pricing

| Plan | Price | Highlights |
| --- | --- | --- |
| **Free** | $0 forever | 2 docks, 35 feedback submissions per month, client share link on 1 dock, no credit card |
| **Pro** | $15/mo yearly · $19/mo monthly | 5 docks, unlimited feedback, 7 team members, screen recording, integrations, MCP |
| **Agency** | $59/mo yearly · $69/mo monthly | Unlimited docks, 20 team members, diagnostics on every pin, full-context MCP, team permissions |

Paid plans start with a 14 day free trial. Current prices live at [layerdock.io](https://layerdock.io/#pricing).

---

## Who is it for?

Web design agencies · freelancers · product teams · QA · Framer, Webflow and WordPress teams · engineering teams using Claude Code or Cursor.

Looking for a **BugHerd**, **Marker.io**, **MarkUp.io** or **Jam** alternative? LayerDock captures developer context automatically on every pin.

---

## Under the hood

```
Next.js app (Vercel)          Dashboard, landing, admin, review dock, API routes
embed.js (Webpack)            The pin tool, runs inside the reviewed site's frame
Review proxy (Cloudflare)     Serves the site on a signed subdomain and injects embed.js
Layerdock for Chrome          Optional launcher, talks to the bearer API only
Supabase                      Postgres, Auth (Google), Storage
Paddle                        Billing, merchant of record
Resend                        Email
```

### Run it locally

```bash
git clone https://github.com/LayerDock/LayerDock-Saas.git
cd LayerDock-Saas
npm install
cp .env.example .env.local   # fill in Supabase, Paddle and Resend keys
npm run dev
```

| Script | What it does |
| --- | --- |
| `npm run dev` | Next.js dev server |
| `npm run build:embed` | Builds the pin tool to `public/embed.js` (set `NODE_OPTIONS=--max-old-space-size=6144` on Windows) |
| `npm run build:extension` | Builds Layerdock for Chrome |
| `npm run deploy:proxy` | Deploys the review proxy Worker |
| `npm run verify` | Typecheck, lint and unit tests |

More detail in [`docs/runbooks/`](docs/runbooks).

---

## FAQ

**Do I need to install anything?** No. It runs in the browser.

**Do clients need an account?** No. They use a share link.

**What is captured with each comment?** Screenshot, CSS selector, viewport, console logs, network requests, browser and OS.

**Can I send feedback to my coding agent?** Yes, through MCP with Claude Code or Cursor.

---

<div align="center">

[**layerdock.io**](https://layerdock.io) · [Indie Hackers](https://www.indiehackers.com/product/layerdock)

</div>

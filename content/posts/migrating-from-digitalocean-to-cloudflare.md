---
title: "Retiring the Droplet: Migrating to Cloudflare"
date: 2026-07-19T09:00:00-07:00
tags:
    - cloudflare
    - hosting
    - terraform
    - ai
categories:
    - technology
draft: false
---

Since 2018 nearly everything I host—my sites, a few small apps, and my son's Unity games—has lived on a single DigitalOcean droplet. Caddy in front, PM2 keeping the Node apps alive, about a dozen static sites and eight little APIs all sharing one box. It worked, mostly. But over the past week I moved almost all of it to Cloudflare, and I wish I had done it sooner.

> As always, I am not an expert on this topic. This is just what worked for me and why.

## The Problem with One Server

The droplet was a classic snowflake. Every site meant a Caddy block, maybe a PM2 app, and some deploy mechanism ranging from a webhook to "rsync and hope." I was responsible for OS patches, certificate renewals, process restarts, and a disk that hovered around 90% full. None of this was hard individually, but it was a constant low-grade tax—and a single point of failure for everything my family had online.

The thing is, nothing I run needs a server. It's static sites, single-page apps, and small APIs with modest data behind them. Paying that operational tax to keep a box alive for workloads like this stopped making sense years ago; I just hadn't gotten around to admitting it.

## The New Shape

Everything now maps to a Cloudflare primitive:

* **Pages** serves the websites—static sites, SPAs, and the Unity WebGL games.
* **Workers** run the APIs, ported to [Hono](https://hono.dev), which was close to a drop-in for the existing apps.
* **D1** (SQLite at the edge) holds the data, and **R2** holds large game downloads.
* **Cron Triggers** replaced the scheduled jobs.

One design decision I'm particularly happy with: each app's UI and API share a single hostname. DNS points at Pages, and a Worker route intercepts `/api/*`. Same origin means no CORS configuration in production, which eliminates a whole category of dumb bugs.

Deploys are now boring in the best way. Every project lives in a GitHub repo, and GitHub Actions pushes to Cloudflare on merge. No SSH, no PM2, no "did the webhook fire?"

## Terraform for the Long-Lived Stuff

The piece that turned this from a pile of dashboard clicks into something maintainable is a small infrastructure repo. The division of labor:

* **Terraform** owns the long-lived things: zones, DNS records, Pages projects, redirect rules.
* **Scripts** handle the imperative glue, like minting a scoped CI token per project and pushing it to GitHub secrets.
* **Each site's repo** owns its own Worker code and deployments via `wrangler`.

Workers deliberately stay *out* of Terraform—`wrangler.jsonc` in each repo is already declarative and versioned, and two sources of truth for the same resource is how drift happens. Adding a new site is now one module block and one script run.

## Doing It with AI

I did this migration with Claude over a few days, and it changed the economics of the whole project. This is exactly the kind of work that sits forever on a todo list: not intellectually hard, but full of tedious steps and sharp edges—DNS zone imports where a missed MX record breaks email, API permission names that don't match the dashboard labels, D1 import quirks. Working with an AI that could read the old server's config, port an Express app to Hono, and write the Terraform meant the friction dropped to nearly zero. The gotchas we (yes, I felt like my bot was a partner in this effort) hit got written down as we went, so each site migrated faster than the last.

## Was It Worth It?

For the kind of software I build—personal sites and small apps for family—this architecture is simply a better fit. There is no server to patch, no process manager, no certificate renewal, no disk filling up. Everything deploys from git, DNS and domains are code, and the whole thing scales to zero attention, which is exactly how much attention I want to give it.

A few stragglers remain on the droplet, and then it gets snapshotted and deleted. End of another era—and this time I won't miss it.

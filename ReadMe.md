<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/banner-dark.svg">
  <img src="assets/banner-light.svg" alt="Alexi Dermosesian — full-stack web developer" width="100%">
</picture>

I build full-stack web applications: React and TypeScript on the front, PHP, Laravel and
Node behind them. Currently at **Devotel**, building React interfaces and custom WordPress
platforms and wiring both up to REST APIs.

I like building things, breaking them, fixing them, and occasionally wondering why I wrote
the code that way in the first place.

---

## [Balancil](https://github.com/alexidrs79/Balancil) — a personal ledger

Accounts, transactions, budgets, savings goals and spending analytics. You enter the
records; it never connects to a bank or moves money. React and TypeScript on the front,
Laravel and Sanctum behind it.

Two decisions I'd defend in a review. Every owned record goes through a query scope that
**fails closed**, so console code has to opt out of the filter deliberately rather than leak
by accident. And a stored balance is never trusted on its own — `ledger:reconcile`
recomputes each one from the transactions behind it, so drift surfaces as a failing command
instead of a quietly wrong number.

```mermaid
flowchart LR
  A["React · TypeScript<br/>Vite"] -->|"Sanctum token"| B["Laravel<br/>REST API"]
  B --> C["owned() scope<br/>fails closed"]
  C --> D[("MySQL")]
  E["ledger:reconcile"] -.->|"recomputes every balance"| D
```

`React` · `TypeScript` · `Laravel` · `Sanctum` · `MySQL` · `PHPUnit` · `Vitest`

---

## [Stub](https://github.com/alexidrs79/stub) — a private film and television archive

Track what you've watched, what you're part-way through and what's next, over TMDb's
catalogue. React 19 on the front, Express, Prisma and PostgreSQL behind it.

A title sits in exactly one of three states, and holding that invariant against concurrent
tabs is the part I'd defend in a review. Every transition runs inside one transaction that
first takes `pg_advisory_xact_lock` keyed on `(user, title)`, so a second tab acting on the
same title waits and then re-reads committed state, while two different users never contend
with each other at all.

```mermaid
stateDiagram-v2
  direction LR
  [*] --> Watchlist: add
  Watchlist --> Watching: start · records progress
  Watchlist --> Watched: stamp
  Watching --> Watched: stamp · score, note, date
  Watched --> Watchlist: remove stamp
  Watched --> Watched: revise stamp
```

Stamping a title clears its progress pointer in the same transaction, and stamping again
revises the one entry rather than appending a second. TMDb responses are cached, and an
expired row still serves if TMDb refuses — a stale poster beats a blank one.

`React 19` · `Express 5` · `Prisma` · `PostgreSQL` · `JWT` · `Vitest`

---

## Also

**[wp-themes](https://github.com/alexidrs79/wp-themes)** — five client WordPress themes.
Snap, Lucibook and Devotel are standalone ACF landing themes built from Figma. Superb Painting
and Premier Edge Painting are Kadence children for Melbourne painters — suburb and service
CPTs, quote forms, and the front-end markup in the child rather than in the parent.

**[portfolio-site](https://github.com/alexidrs79/portfolio-site)** — my own site, React and
Vite, built and deployed to Pages by Actions on every push to `main`. Live at
**[alexidrs79.github.io/portfolio-site](https://alexidrs79.github.io/portfolio-site/)**.

---

## Stack

| | |
| --- | --- |
| **Front end** | React, TypeScript, JavaScript, Next.js, TanStack Query, Redux, Tailwind, Vite |
| **Back end** | PHP, Laravel, Node.js, Express, REST APIs |
| **Data** | PostgreSQL, MySQL, Prisma, SQLite |
| **WordPress** | Custom themes and plugins, ACF, Multisite, WooCommerce, Gutenberg blocks |
| **Testing** | Vitest, PHPUnit, Pest, Testing Library, `node:test` |
| **Ops** | Docker, Nginx, Apache, GitHub Actions |

Every repository runs its own checks on push:

[![Balancil](https://img.shields.io/github/actions/workflow/status/alexidrs79/Balancil/ci.yml?branch=main&style=flat-square&label=Balancil&labelColor=161B22)](https://github.com/alexidrs79/Balancil/actions/workflows/ci.yml)
[![stub](https://img.shields.io/github/actions/workflow/status/alexidrs79/stub/ci.yml?branch=main&style=flat-square&label=stub&labelColor=161B22)](https://github.com/alexidrs79/stub/actions/workflows/ci.yml)
[![wp-themes](https://img.shields.io/github/actions/workflow/status/alexidrs79/wp-themes/ci.yml?branch=main&style=flat-square&label=wp-themes&labelColor=161B22)](https://github.com/alexidrs79/wp-themes/actions/workflows/ci.yml)
[![portfolio-site](https://img.shields.io/github/actions/workflow/status/alexidrs79/portfolio-site/ci.yml?branch=main&style=flat-square&label=portfolio-site&labelColor=161B22)](https://github.com/alexidrs79/portfolio-site/actions/workflows/ci.yml)

[Portfolio](https://alexidrs79.github.io/portfolio-site/) ·
[LinkedIn](https://www.linkedin.com/in/alexi-dermosesian/) ·
[alexi.drs79@gmail.com](mailto:alexi.drs79@gmail.com)

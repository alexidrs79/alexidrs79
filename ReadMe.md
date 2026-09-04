## Hey, I'm Alexi

I'm a full-stack web developer in Yerevan, working mostly with React, TypeScript, PHP, Laravel, Node.js and WordPress. I like building things, breaking them, fixing them, and occasionally wondering why I wrote the code that way in the first place.

Currently at Devotel, building React interfaces and custom WordPress platforms and wiring both up to REST APIs.

### Things I've built

**[Balancil](https://github.com/alexidrs79/Balancil)** — a personal ledger. React and TypeScript on the front, Laravel and Sanctum behind it. Accounts, transactions, budgets, savings goals and spending analytics. Records are scoped to their owner by a query scope that fails closed, so console code has to opt out deliberately rather than leak by accident, and a reconcile command checks every stored balance against the transactions behind it.

**[Stub](https://github.com/alexidrs79/stub)** — a private film and television archive. React front end, Express, Prisma and PostgreSQL. Watch-state changes run inside a transaction holding an advisory lock, so two open tabs can't leave a title in an inconsistent state, and TMDb responses are cached so the archive still renders during a TMDb outage.

**[wp-themes](https://github.com/alexidrs79/wp-themes)** — three ACF-driven WordPress themes built from Figma for client products, each one a field group and template part per section so the content stays editable in wp-admin.

**[portfolio-site](https://github.com/alexidrs79/portfolio-site)** — my own site, in React and Vite.

### What I work with

- React, TypeScript, JavaScript, Next.js, TanStack Query, Redux
- PHP, Laravel, Node.js, Express, REST APIs
- PostgreSQL, MySQL, Prisma, SQLite
- WordPress: custom themes and plugins, ACF, Multisite, WooCommerce, Gutenberg blocks
- Vitest, PHPUnit, Testing Library, ESLint, Prettier
- Docker, Nginx, Apache, GitHub Actions

### Elsewhere

[LinkedIn](https://www.linkedin.com/in/alexi-dermosesian/) · [alexi.drs79@gmail.com](mailto:alexi.drs79@gmail.com)

# Vite Plus Full Stack for Web & Mobile Development with AI Agents

**100 stars. I build it. MIT license. Free.**

You already know this story.

You have a product that needs a website and a phone app. So you open twenty tabs. Web framework. Mobile framework. UI kit. API layer. Validation. Auth. Database. Email. Cache. Files. Logs. A Docker setup for your laptop. A way to put it on a server. Then an AI agent that can see the repo without inventing a second architecture.

A few weeks later the tools almost agree with each other. The idea is cold.

Shopping feels like engineering. The product is the part you have not started.

This repo is the vote to skip the shopping. One monorepo for web and mobile, organized by [Vite+](https://viteplus.dev/). The tools you already respect, introduced to each other, so you can ship features.

## The deal

The stack below is the plan. The code is the prize.

When this repo reaches **100 stars**, I build it and publish it under the [MIT license](https://opensource.org/licenses/MIT). Free to use, free to change, free to ship inside your own product. No course. No paywall. No enterprise tier sitting on the parts you actually need.

A star takes two seconds. It says: build the boring system, so I can build the interesting part.

You might wait until the code exists. The code exists when the vote exists. Waiting is how a good stack stays a blog post.

**[Star the repo](https://github.com/VienDinhCom/vite-plus-full-stack)**

[![GitHub stars](https://img.shields.io/github/stars/VienDinhCom/vite-plus-full-stack?style=social)](https://github.com/VienDinhCom/vite-plus-full-stack)

## What you are voting for

Web and mobile. One API. One schema. One auth. One database. Your laptop, then a server.

### The monorepo

[Vite+](https://viteplus.dev/) is the unified toolchain behind the `vp` command. One tool for the pieces you would otherwise wire by hand: Vite, Rolldown, Vitest, tsdown, Oxlint, Oxfmt, and Vite Task. It is free, and the license is MIT.

One configuration file. One set of commands: `vp install`, `vp dev`, `vp check`, `vp test`, `vp build`, `vp run`.

`vp check` formats, lints, and type-checks in a single pass, and it can fix what it knows how to fix. Tests reuse the app's resolve and transform setup. The runner speaks a Jest-compatible API, isolates tests by default, and can run them in a real browser.

The speed claims belong to Vite+, and they are specific. A Rust core. Up to 40× faster production builds than webpack. About 50× to 100× faster linting than ESLint. Up to 30× faster formatting than Prettier. Hot module replacement stays instant. In a monorepo, Vite Task caches work and runs packages in dependency order.

You maintain one toolchain. The same commands mean the same thing in every package.

### Web and mobile, same language

[TanStack Start](https://tanstack.com/start/latest) is the web app. Full-stack React: type-safe routing, server-side rendering, streaming, and server functions, on top of TanStack Router. Routes, loaders, and links stay put. Start adds the server. A server function is visible in the code that calls it, with a validator on the way in.

[Expo](https://expo.dev/) is the mobile app. It is the React Native framework recommended by the React Native team: iOS, Android, and the web, plus a large set of native APIs. File-based routing. Typed routes. If you write React, you can ship the phone app. Swift or Kotlin shows up only when a screen truly needs it.

Same TypeScript. Two clients. One product.

### UI you can own

[Tailwind CSS](https://tailwindcss.com/) on the web and mobile. Utility classes in the markup, composed into the design you actually want. Production builds drop the CSS you never used.

[shadcn/ui](https://ui.shadcn.com/) for the web components. Accessible, composable, and copied into your repo so you can change them. You own the buttons. A library release does not own you.

[React Native Reusables](https://reactnativereusables.com/) on mobile. shadcn/ui, brought to React Native, styled with Nativewind or Uniwind. The phone UI and the site UI can share a taste.

### One API, two clients

[oRPC](https://orpc.dev/) is where the server API is defined and implemented. Both clients call it with end-to-end types. OpenAPI is included when a partner, a document, or another language needs a normal HTTP contract. There are adapters for TanStack Start and Expo, a Better Auth integration, and first-class helpers for [TanStack Query](https://tanstack.com/query/latest).

TanStack Query owns server state. A component declares the data. The cache dedupes in-flight requests, retries, refetches in the background, and keeps stale data on screen while the network catches up. Mutations can update the UI first and reconcile with the server after. Web and mobile share that habit.

### Schemas that travel

[Zod](https://zod.dev/) is the schema language. TypeScript-first, no dependencies, small enough to run on the server and in the client. You describe a payload once. Parse it on the way in. Infer the type from the same object. oRPC accepts Zod through Standard Schema, so the API contract and the validator are the same thing.

[T3 Env](https://env.t3.gg/docs/introduction) parses environment variables with that same Zod schema. Missing keys fail at startup, with a message you can read, which beats a crash three screens later. Server variables and client variables stay apart. Read a server secret from the client and it throws, on purpose.

### Auth, data, and the rest of a real product

[Better Auth](https://better-auth.com/) lives in your application code. Email and password, sessions, social sign-in, organizations, roles, two-factor, passkeys, and a long plugin list. The config is a file you can review in a pull request.

[Drizzle ORM](https://orm.drizzle.team/) manages [Postgres](https://www.postgresql.org/) in TypeScript: schema, queries, and migrations. Row-Level Security stays in the database. A user sees their own rows because Postgres says so, even when a handler forgets a `where` clause.

The product services around that core:

- [React Email](https://react.email/) writes the email as React components, and sends through the provider you already have.
- [Redis](https://redis.io/) holds cache, rate limits, and other short-lived state.
- [Twilio](https://www.twilio.com/) is the phone line.
- [Amazon S3](https://aws.amazon.com/s3/) stores files in production. On your laptop, [RustFS](https://rustfs.com/) speaks the S3 API, so the upload code stays the same. RustFS is open source, Apache 2.0, and written in Rust.
- [OpenTelemetry](https://opentelemetry.io/) collects traces, metrics, and logs once, then exports them to whatever backend you pick later. oRPC can record those spans across the procedure call.

### Your laptop, then a server

Docker runs the local services: Postgres, Redis, RustFS, and [Mailpit](https://mailpit.axllent.org/). Mailpit is a small SMTP server with a web inbox. It renders the HTML, checks links, scores spam, and exposes an API for tests. A password-reset email lands on your machine until you decide a real inbox should see it.

For a VPS, [Kamal](https://kamal-deploy.org/) deploys a containerized app to ordinary Ubuntu servers. Zero-downtime deploys, rolling restarts, and accessory services. Give it IP addresses and an SSH key. It installs Docker and ships. The same idea 37signals used to move their apps onto hardware they control.

You can also deploy wherever you already have an account: Amazon AWS, Vercel, Google Cloud, Railway, Fly.io, and the rest. TanStack Start keeps the routes and server boundaries when the deploy target changes. Kamal is the VPS path. The stack is portable.

### Agents that already know the house

[OpenCode](https://opencode.ai/) is the open-source coding agent. Terminal, desktop app, or IDE. Claude, GPT, Gemini, a local model, or any of 75+ providers. It does not store your code or your context.

Three tools keep it pointed at this repo:

- [CodeGraph](https://github.com/colbymchenry/codegraph) builds a local code knowledge graph and syncs it as files change. The agent spends fewer tokens hunting. The graph stays on your machine, and OpenCode is a supported client.
- [Ponytail](https://github.com/dietrichgebert/ponytail) aims the agent at the smallest change that works. The best line of code is the one nobody had to write.
- [DBHub](https://github.com/bytebase/dbhub) is a token-light MCP server for Postgres and other databases. Two tools by default, so the context window stays free for the task. Read-only mode, row limits, and timeouts are there for when a question should not become a migration.

## What you do with it

Use it. Ship the feature.

The screen is React. The style is Tailwind. The component is yours. The payload is a Zod schema. The call is oRPC. The cache is TanStack Query. The session is Better Auth. The row is Postgres, with RLS behind it. The email is a React component. The file is S3. The trace is OpenTelemetry. The agent can see the graph, the database, and the instruction to write less.

Every one of those tools was already good. The missing piece is the agreement between them.

## Your move

If this is the system you would assemble on a weekend and then maintain for years, cast the vote.

**100 stars. I build it. MIT license. Free.**

[Star VienDinhCom/vite-plus-full-stack](https://github.com/VienDinhCom/vite-plus-full-stack)

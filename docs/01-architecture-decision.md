# Stage 1 — Architecture decision

**Status:** approved 2026-11-11 (option B).

## Decision

WordPress runs headless as the content management system only. A Spring Boot
application renders every public page on the server with Thymeleaf.

```
Editors ──> WordPress (cms.<domain>, noindex, restricted)
                 │  REST API over HTTPS (/wp-json/wp/v2/…)
                 │  webhook on publish/update
                 ▼
Visitors ─> CDN ─> Spring Boot + Thymeleaf (www.<domain>)
                     · routing, HTML, metadata, canonicals
                     · JSON-LD, sitemap.xml, robots.txt, breadcrumbs
                     · lead forms → CRM
                     · in-memory cache, serves stale if the CMS is down
```

## What runs where

| Concern | Java (Spring Boot) | PHP (WordPress) |
|---|---|---|
| Public HTML, URLs, redirects | ✔ | — |
| Title, meta, canonical, Open Graph, JSON-LD | ✔ (generated) | editors enter title/description only |
| XML sitemap, robots.txt, breadcrumbs | ✔ | — |
| Inquiry and consultation forms | ✔ | — |
| Content editing, media library, users, roles | — | ✔ |
| Content types and custom fields | reads them | ✔ (ACF or equivalent) |
| "Content changed" webhook | receives it | ✔ (plugin or a few lines of PHP) |

## Consequences accepted

- Two hosts: a managed WordPress host for the CMS and a JVM host for the app.
  Typical shared PHP hosting cannot run the Java app.
- Front-end WordPress plugins stop applying: page builders (including Divi),
  form plugins, caching plugins, and the front-end output of SEO plugins.
- Live preview of drafts has to be built in the Java app.
- Template changes need a Java developer.
- Spring Boot minor lines get roughly a year of free support, so plan one
  framework upgrade per year.

## Conflict with the EduConnect design system (recorded deviation)

`educonnect-design-system.json` v1.0.0 specifies WordPress + Divi + child-theme
CSS only and lists new frameworks and plugins under "requires EduConnect
approval". Option B departs from that by explicit instruction for this project.
What carries over unchanged: brand voice, compliance lines, claims policy,
terminology, title/meta/heading rules, AEO rules, schema policy, accessibility
and Core Web Vitals targets. What does not apply: every Divi, Rank Math,
WP Rocket and Imagify instruction. In this architecture the Java app is the
only emitter of schema and metadata.

## Options that were rejected

| Option | Why not |
|---|---|
| WordPress only (PHP theme) | Simplest, but no Java |
| Split by path (Java landing pages + WordPress blog) | Two rendering stacks, two designs, split sitemaps |
| Java API + JavaScript frontend + WordPress | Three tiers; adds client-side rendering risk |
| Java only, no WordPress | Loses the editor administrators need |

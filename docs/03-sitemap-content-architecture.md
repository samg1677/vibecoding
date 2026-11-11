# Stage 3 — Sitemap and content architecture

Built on the intent map in `02-keyword-intent-map.md`. Titles and H1s are
drafts; final copy is written in the CMS.

## 1. Assumptions (to confirm)

- Day 1 CPT Programs is its own site. The host name is a configuration value,
  so nothing below depends on the final domain.
- Titles carry no brand suffix for now. "… | Day 1 CPT Programs" would repeat
  the keyword in almost every title; decide once the brand name is settled.
- URLs use lowercase, hyphens and a trailing slash, with a maximum depth of two.

## 2. Launch sitemap (phase 1)

| URL | Page type | Primary keyword | Draft title tag | Conversion objective | Schema |
|---|---|---|---|---|---|
| `/` | Home | day 1 cpt programs | Day 1 CPT Programs: Compare Universities and Degrees | Book a consultation | Organization, WebSite |
| `/what-is-day-1-cpt/` | Guide | what is day 1 cpt | What Is Day 1 CPT? How It Works for F-1 Students | Go to requirements | WebPage, BreadcrumbList |
| `/requirements/` | Guide | day 1 cpt requirements | Day 1 CPT Requirements and Eligibility Checklist | Eligibility review request | WebPage, BreadcrumbList |
| `/how-to-apply/` | Guide (steps) | how to apply for day 1 cpt | How to Apply for Day 1 CPT: Steps and Timeline | Start an application inquiry | WebPage, BreadcrumbList |
| `/is-day-1-cpt-legal/` | Guide | is day 1 cpt legal | Is Day 1 CPT Legal? Rules and Risks Explained | Consultation | WebPage, BreadcrumbList |
| `/h1b-green-card-impact/` | Guide | day 1 cpt h1b rfe | Day 1 CPT and H-1B RFEs: Green Card Impact | Consultation | WebPage, BreadcrumbList |
| `/rule-changes/` | Tracker | day 1 cpt new rules | Day 1 CPT Rule Changes 2026: Current Status | Email updates sign-up | WebPage, BreadcrumbList |
| `/day-1-cpt-vs-opt/` | Comparison | day 1 cpt vs opt | Day 1 CPT vs OPT: Differences and Trade-Offs | Consultation | WebPage, BreadcrumbList |
| `/universities/` | Hub | day 1 cpt universities | Day 1 CPT Universities: How to Compare Schools | Request a shortlist | CollectionPage, BreadcrumbList |
| `/programs/` | Hub | day 1 cpt degree programs | Day 1 CPT Degrees: Master's, MBA or Doctorate? | Request a shortlist | CollectionPage, BreadcrumbList |
| `/programs/masters/` | Program type | day 1 cpt master's programs | Day 1 CPT Master's Programs: What to Know | Program inquiry | WebPage, BreadcrumbList |
| `/programs/mba/` | Program type | day 1 cpt mba | Day 1 CPT MBA Programs for F-1 Students | Program inquiry | WebPage, BreadcrumbList |
| `/programs/dba/` | Program type | day 1 cpt dba programs | Day 1 CPT DBA and Doctorate Programs | Program inquiry | WebPage, BreadcrumbList |
| `/programs/stem/` | Program type | day 1 cpt stem programs | Day 1 CPT STEM Programs and STEM OPT | Program inquiry | WebPage, BreadcrumbList |
| `/after-h1b-layoff/` | Guide (situational) | day 1 cpt after h1b layoff | Day 1 CPT After an H-1B Layoff: Your Options | Urgent consultation | WebPage, BreadcrumbList |
| `/after-opt/` | Guide (situational) | day 1 cpt after opt | Day 1 CPT After OPT Ends or No H-1B Selection | Consultation | WebPage, BreadcrumbList |
| `/faq/` | FAQ index | day 1 cpt faq | Day 1 CPT FAQ: Short Answers With Sources | Consultation | FAQPage (optional), BreadcrumbList |
| `/glossary/` | Glossary | f-1 work authorization terms | F-1 Work Authorization Glossary: CPT, OPT, SEVIS | Go to guides | WebPage, BreadcrumbList |
| `/blog/` and `/blog/{slug}/` | Blog | long-tail and news only | per post | Go to the owning guide | Article, BreadcrumbList |
| `/consultation/` | Conversion | — | Book a Day 1 CPT Consultation | Form submit | WebPage |
| `/contact/` | Conversion | — | Contact | Form submit | ContactPage |
| `/about/` | Trust | — | About: Who Runs This Site | — | AboutPage |
| `/editorial-policy/` | Trust | — | Editorial Policy and Sources | — | WebPage |
| `/privacy/`, `/terms/` | Legal | — | — | — | WebPage |

Not indexed: thank-you pages, internal search, draft previews, the CMS host.

FAQ rich results in Google ended in May 2026 (per the EduConnect design
system's check on 2026-11-06), so FAQPage markup is optional and promises no
search feature.

## 3. Phase 2 (only when verified data exists)

| URL pattern | Blocked on |
|---|---|
| `/universities/{school}/` | Each school's Day 1 CPT policy quoted from its own website, with link and date; permission where EduConnect represents the school |
| `/universities/{state}/` | At least three verified schools in that state |
| `/cost/` | Tuition figures with source link and date per program |
| `/programs/{field}/` (for example data analytics) | Verified programs in the field |

No placeholder pages are published for these.

## 4. Page types

Each type is one Thymeleaf template built from shared components.

| Type | Fixed structure |
|---|---|
| Home | Hero with promise → direct answer → paths by situation → key guides → rule-status strip → consultation |
| Guide | Breadcrumb → H1 → status-as-of line → 40–70 word direct answer → key facts → sections → FAQ (where allowed) → sources → reviewed-by → related pages → CTA |
| Comparison | Guide structure with a one-sentence verdict above a table with identical row labels |
| Hub | Direct answer → how to evaluate → cards for child pages → CTA |
| Program type | Guide structure plus a program list that renders only verified entries |
| Tracker | Current status summary → dated entries, newest first, each with source and status label |
| FAQ index | Questions grouped by topic, short answer, link to the owning page |
| Glossary | Term, one- or two-sentence definition, link |
| Blog article | H1 → direct-answer first paragraph → body → sources → author → link to the owning guide |
| Conversion | Short form, what happens next, compliance line |

## 5. CMS content model (WordPress)

| Content type | Key fields |
|---|---|
| Landing page | slug, parent, page type, primary keyword, search intent, SEO title, meta description, H1, hero lead, direct answer, status-as-of date, key facts (label, value, source URL), sections, comparison table, steps, CTA type and label, related pages, sources (title, publisher, URL, accessed date), reviewed by, last reviewed, index/noindex |
| FAQ | question, answer, topic, owning page, sources |
| University | official name, official URL, accreditor, locations, relationship to the operator (partner / no affiliation), Day 1 CPT policy quote, source URL, last verified |
| Program | university, degree level, field, STEM designation with source, duration, format, on-site requirement, tuition with source and date, start dates, last verified |
| Rule update | date, headline, summary, status (proposed / final / blocked / in effect), source URL |
| Glossary term | term, definition, related page |
| Blog post | standard post fields, author, owning guide, sources |
| Author | name, role, credentials, profile link |
| Site settings | navigation, footer, compliance lines, operator disclosure, default CTAs, redirects |

Rules the Java app enforces, so that accuracy does not depend on memory:

- A fact row, tuition figure or policy quote with no source URL is not rendered.
- University and program entries older than a set review age show "last
  verified {date}" prominently and are flagged in an admin report.
- Duplicate primary keyword, title, meta description or H1 across pages is
  reported and blocks sitemap inclusion of the newer page.
- Regulatory pages without a status-as-of date or reviewer are not indexable.

## 6. Internal linking

- **Hubs:** home → every phase 1 page; `/programs/` → four program-type pages;
  `/universities/` → program-type pages now, school pages in phase 2.
- **Spokes:** every page links to its parent, at least two siblings and the
  page that owns any neighbouring question it mentions.
- **Fixed cross-links:** definition ↔ requirements ↔ how to apply;
  legality ↔ H-1B impact ↔ rule changes; every program-type page → vs OPT;
  both situational pages → how to apply and requirements; every regulatory
  statement → rule changes.
- **Blog:** every post links to the guide that owns its topic.
- **Anchor text** names the target topic. Related-page lists are curated in
  the CMS, not generated.

## 7. Accuracy and compliance rules for content

- Cite USCIS, ICE/SEVP, the eCFR, the Federal Register and official university
  pages. Commercial blogs are never the cited source for a rule.
- No invented university policies, tuition, statistics, testimonials or
  outcomes. Unknown facts stay out until supplied.
- Every page carries the two compliance lines from the EduConnect design
  system (decisions are made by universities, employers and accreditors;
  immigration information is general guidance, confirm with a DSO or attorney).
- No guarantees about visas, employment, admission or search visibility.
- The About page and footer state who operates the site and its commercial
  relationships.

## 8. Open decisions for the owner

1. **Domain and relationship to educonnectusa.com.** New standalone domain,
   subdomain or section of the existing site, or a replacement for it.
2. **Brand.** EduConnect USA's colours and type (the design system is marked
   "draft, pending brand confirmation"), a new brand, or an endorsed sub-brand.
3. **Content split** between this site and the existing EduConnect Day 1 CPT
   pages and posts.
4. **Which universities may be listed,** and who supplies and re-verifies
   their data.
5. **Named reviewer** for immigration content (the E-E-A-T and status-line
   rules need a real person).
6. **CRM destination** for forms (HubSpot is connected to this workspace).
7. **Hosting** for the Java app. The existing WordPress hosting noted in the
   design system (GoDaddy Managed WordPress) can host the CMS but not the app.

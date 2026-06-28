## Research-Driven Additions

- [ ] P0 - Repair README navigation and anchor integrity
  Why: Broken internal links make the directory harder to browse and signal stale curation.
  Evidence: `npx markdown-link-check README.md --quiet`; `npx markdownlint-cli2 README.md .github/ISSUE_TEMPLATE/new-service-proposal.md`; `README.md:50`, `README.md:120`, `README.md:124`.
  Touches: `README.md`.
  Acceptance: Contents links resolve locally for Dictation / ASR, VPNs, WebView, Others, Android subsections, and renamed/moved headings; markdown lint no longer reports MD042/MD051 anchor failures for the table of contents.
  Complexity: S

- [ ] P0 - Triage dead and bot-blocked service links
  Why: Readers use the list to choose privacy tools; dead project, dead demo, and dead documentation links can send them to abandoned or unsafe paths.
  Evidence: `npx markdown-link-check README.md --quiet` reported 57 failures, including `commento.io`, `screenity.io/en`, `github.com/arnowelzel/periodical`, `git.sr.ht/~metalune/simpleweb_peertube`, `github.com/Metastem/wikiless`, and several `anonymousplanet.org` anchors.
  Touches: `README.md`.
  Acceptance: Each failed link is either fixed, replaced with a canonical upstream URL, marked as transient/bot-blocked with a durable source, or removed when the project/service is confirmed dead.
  Complexity: M

- [ ] P0 - Add a local validation section for maintainers
  Why: The repo has no build or test suite, so repeatable local checks are the only practical quality gate for list edits.
  Evidence: `CLAUDE.md` says to use `git diff --check`; `awesome-lint`, `markdownlint-cli2`, and `markdown-link-check` currently surface actionable failures; this fork prohibits GitHub Actions.
  Touches: `README.md`, `.github/ISSUE_TEMPLATE/new-service-proposal.md`.
  Acceptance: Maintainers have documented local commands for whitespace, awesome-list lint, markdown structure, and link checks, plus guidance for known transient link-check statuses.
  Complexity: S

- [ ] P0 - Strengthen new-service proposal evidence fields
  Why: The current template asks why a service helps privacy but does not collect enough evidence to evaluate privacy, security, maintainability, or replacement fit.
  Evidence: `.github/ISSUE_TEMPLATE/new-service-proposal.md`; Privacy Guides criteria; ToS;DR; Exodus Privacy.
  Touches: `.github/ISSUE_TEMPLATE/new-service-proposal.md`.
  Acceptance: Proposals require source/repo URL, license, privacy policy, data collected, trackers, account requirement, self-host/offline support, maintenance status, target service replaced, and section fit.
  Complexity: S

- [ ] P1 - Define concise listing criteria in README
  Why: "Free, open source and privacy respecting" is the stated philosophy, but reviewers need consistent acceptance/rejection rules for closed-source services, paid tiers, abandoned forks, hosted-only products, and privacy frontends.
  Evidence: `README.md` intro; Privacy Guides criteria; awesome-list contribution conventions; recent commits removing discontinued or unsuitable services such as Qwant Maps, DivestOS, hCaptcha, Njal.la, Skiff, SimpleMobileTools, and Bromite.
  Touches: `README.md`.
  Acceptance: README includes a short criteria section covering source availability, data collection, account/payment identity, maintenance activity, license clarity, tracker posture, and when to use caution/dead-project markers.
  Complexity: M

- [ ] P1 - Normalize entry metadata for high-risk categories first
  Why: Health, VPN, payments, crypto, AI, password managers, browsers, and social frontends carry higher privacy/security risk than ordinary utility links.
  Evidence: Privacy Guides category criteria; Exodus Privacy reports; ToS;DR badges already used throughout `README.md`; active upstream churn in AI and removed/discontinued service commits.
  Touches: `README.md`.
  Acceptance: High-risk sections use a consistent compact pattern for license/source, platform, self-host/offline availability, account requirement, and caution notes where evidence is incomplete.
  Complexity: L

- [ ] P1 - Improve accessibility of badges, icons, and image-only links
  Why: Screen-reader users cannot evaluate icon-only ToS;DR badges or decorative symbols without text alternatives.
  Evidence: `markdownlint-cli2` reported MD045 no-alt-text on README badges/images; WCAG 2.2 non-text content guidance.
  Touches: `README.md`, `misc/logo.png` reference.
  Acceptance: Logo and badge links have accessible names or adjacent text; repeated icon meanings are textually clear at point of use or consistently mapped without relying on emoji alone.
  Complexity: M

- [ ] P1 - Add stale-project review rules
  Why: The README already uses a dead-project icon, and recent history shows repeated removals for discontinued/acquired/shutdown services.
  Evidence: `README.md` Icons section; `git log -200` entries for removed discontinued services; markdown-link-check failures for dead repositories and domains.
  Touches: `README.md`.
  Acceptance: README defines when to mark, replace, or remove inactive tools based on release cadence, repository archival, domain status, security relevance, and maintained forks.
  Complexity: M

- [ ] P2 - Rework category taxonomy for duplicated or drifting sections
  Why: Duplicate Android anchors, moved AI speech sections, empty Dictation / ASR contents entry, and missing WebView target indicate the taxonomy is drifting as categories grow.
  Evidence: `awesome-lint README.md`; `markdownlint-cli2 README.md`; `README.md` Contents.
  Touches: `README.md`.
  Acceptance: Contents and headings form a stable hierarchy with no duplicate anchors, empty links, or orphaned sections; category names consistently distinguish apps, services, frontends, protocols, and operating systems.
  Complexity: M

- [ ] P2 - Add migration-oriented notes for major proprietary services
  Why: Comparable directories such as switching.software and degoogle reduce friction by showing what users are replacing and what migration tradeoffs to expect.
  Evidence: switching.software; degoogle; current `README.md` avoid/instead framing.
  Touches: `README.md`.
  Acceptance: Priority sections include short migration notes for data export/import, account deletion, compatibility limits, or self-hosting burden where that affects privacy adoption.
  Complexity: L

- [ ] P2 - Add a link-check triage policy instead of raw delete-on-fail behavior
  Why: Automated link checks mix true 404s with bot-blocking, rate limits, TLS/CDN errors, and temporary Codeberg/GitHub issues.
  Evidence: `markdown-link-check` results include 403, 429, 503, 520, 526, and status 0 alongside true 404s; lychee and markdown-link-check documentation.
  Touches: `README.md`.
  Acceptance: Maintainers have a documented policy for retry count, archive/canonical replacement, acceptable bot-blocked links, and removal thresholds.
  Complexity: S

- [ ] P3 - Consider optional machine-readable companion data
  Why: AlternativeTo and awesome-selfhosted show the value of filters and metadata, but the README should remain the primary product.
  Evidence: AlternativeTo filtering model; awesome-selfhosted metadata conventions.
  Touches: Future data file or generated README workflow if adopted.
  Acceptance: A design note decides whether a small local data source can generate or validate README entries without adding hosted infrastructure or GitHub Actions.
  Complexity: XL

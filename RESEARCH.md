# Research - Awesome Privacy

## Executive Summary
Awesome Privacy is a static CC0-curated directory of free, open-source, privacy-respecting alternatives to proprietary services. Its strongest shape is breadth: `README.md` already covers daily-use categories from 2FA and browsers through health, AI, payments, and social frontends. The highest-value direction is trust operations for a high-stakes recommendation list: repair broken internal navigation, introduce repeatable local validation, make contribution criteria evidence-driven, and add stale-service review mechanics. Top opportunities: fix link and table-of-contents failures; add local-only list validation commands; require privacy/security/license/maintenance evidence in proposals; normalize entry metadata; add accessibility fixes for badge/icon-only content; schedule high-risk category review; triage dead links and discontinued frontends; define category ownership rules for fast-moving AI, health, VPN, crypto/payments, and social frontend sections.

## Product Map
- Core workflows: browse proprietary services to avoid, choose listed alternatives, follow service links, submit new service/section proposals, mirror/read the list from GitHub or Codeberg.
- User personas: privacy-curious mainstream users, self-hosters, FOSS contributors proposing tools, maintainers reviewing additions, readers comparing privacy/security/anonymity tradeoffs.
- Platforms and distribution: one GitHub-rendered `README.md`, image assets in `misc/`, CC0 license, Codeberg mirror link, issue-template intake in `.github/ISSUE_TEMPLATE/new-service-proposal.md`.
- Key integrations and data flows: outbound links to service websites, GitHub/Codeberg repositories, ToS;DR badges, Exodus Privacy reports, browser-rendered GitHub anchors, manual issue/PR review.

## Competitive Landscape
- Privacy Guides: strict recommendation criteria and category-specific evidence requirements. Learn from its explicit review criteria and "not every tool is recommendable" posture. Avoid copying its heavier editorial voice if the project wants to remain an awesome-list style directory.
- PRISM Break: clear category navigation and direct replacement framing for privacy-invasive software. Learn from its concise discovery UX. Avoid its limited depth compared with Awesome Privacy's broad service inventory.
- PrivacyTools.io: familiar privacy-tool taxonomy and mainstream discoverability. Learn from simple consumer-oriented grouping. Avoid opaque criteria drift and controversy-prone governance.
- switching.software: direct "replace X with Y" framing. Learn from low-friction migration-oriented copy. Avoid becoming a general ethical-software catalog disconnected from privacy evidence.
- AlternativeTo: strong filtering and category navigation. Learn from platform/license/filter metadata. Avoid user-rating popularity bias that can reward non-private tools.
- degoogle: focused de-Google migration checklist. Learn from migration sequencing and beginner-friendly framing. Avoid narrowing Awesome Privacy to only one vendor ecosystem.
- awesome-selfhosted: mature list conventions with license/source metadata and consistent entries. Learn from machine-checkable metadata patterns. Avoid admitting self-hosted tools merely because they are self-hosted; privacy posture still needs evidence.
- Personal Security Checklist: practical threat-model and user-action structure. Learn from severity/category tagging. Avoid turning the directory into a long hardening manual.

## Security, Privacy, and Reliability
- Verified: `npx markdown-link-check README.md --quiet` found 57 dead or unreachable links, including broken internal anchors `#others`, `#VPNS`, and `#webview`; several likely stale external entries include `commento.io`, `screenity.io/en`, `github.com/arnowelzel/periodical`, `git.sr.ht/~metalune/simpleweb_peertube`, `github.com/Metastem/wikiless`, and `anonymousplanet.org` anchors.
- Verified: `npx awesome-lint README.md` found 376 errors and 24 warnings, including missing `contributing.md`, table-of-contents mismatches, invalid list item shapes, undefined references, duplicate links, casing issues, and missing Awesome badge next to the main heading.
- Verified: `npx markdownlint-cli2 README.md .github/ISSUE_TEMPLATE/new-service-proposal.md` found structural markdown issues, including an empty `Dictation / ASR` contents link at `README.md:50`, invalid fragments at `README.md:120` and `README.md:124`, image/badge links without alt text, hard tabs, heading jumps, and duplicate headings.
- Verified: `.github/ISSUE_TEMPLATE/new-service-proposal.md` asks for license and privacy rationale, but not source URL, privacy policy, data model, trackers, maintenance status, audit/security history, platform availability, or replacement target.
- Missing guardrails: no repo-local validation script/documented commands, no local link-check allowlist for transient 403/429/503 responses, no stale-entry review cadence, no proposal checklist for high-risk domains such as health, VPNs, payments, crypto wallets, AI, and social frontends.
- Recovery and rollback needs: local-only validation should be documented so maintainers can reproduce lint/link failures before merging list edits; no GitHub Actions should be added in this fork.

## Architecture Assessment
- The project is a single-file content architecture: almost all product value and risk are in `README.md`; there is no package manager, build system, runtime, or test suite.
- `README.md` has navigation and consistency debt that directly affects the reader workflow: duplicate Android anchors, a missing WebView target in the contents, an empty Dictation/ASR link, mismatched subsection labels, inconsistent heading levels, hard tabs, and icon/badge-only links without accessible names.
- `.github/ISSUE_TEMPLATE/new-service-proposal.md` is the right boundary for intake quality, but it should collect evidence that maintainers otherwise have to research manually.
- `misc/README.md` is only "Files and miscellaneous"; if documentation links stay pointed at upstream files, the fork should avoid adding extra markdown other than the required research/roadmap outputs.
- Test and documentation gaps: no documented local commands for `awesome-lint`, markdown lint, or link checks; no acceptance criteria for what makes a service "privacy respecting"; no policy for abandoned projects, alternative frontends that depend on hostile upstream APIs, or links that intermittently block automated checkers.

## Rejected Ideas
- Convert to a full web app: AlternativeTo-style filtering is useful, but this repo's delivery model and audience benefit from a low-maintenance GitHub README first.
- Add GitHub Actions for link checks: automation is common in awesome lists, but this fork's rules prohibit GitHub Actions; use documented local commands instead.
- Add paid/commercial affiliate-style rankings: commercial directories show demand for comparisons, but rankings would weaken the project's FOSS/privacy-first posture.
- Remove all services that return transient 403/429/503 in link checks: many failures are bot-blocking or temporary; create a triage process before removal.
- Require formal third-party audits for every listing: Privacy Guides-style evidence is valuable, but audit-only admission would exclude useful small FOSS tools and overfit to funded projects.
- Expand into general security hardening advice: Personal Security Checklist covers that space better; Awesome Privacy should stay focused on alternatives and privacy evidence.

## Sources
Project and validation:
- https://github.com/pluja/awesome-privacy
- https://github.com/pluja/awesome-privacy/issues
- https://github.com/pluja/awesome-privacy/pulls
- https://github.com/pluja/awesome-privacy/discussions
- https://raw.githubusercontent.com/pluja/awesome-privacy/main/README.md
- https://github.com/pluja/awesome-privacy/blob/main/.github/ISSUE_TEMPLATE/new-service-proposal.md

Comparable directories:
- https://www.privacyguides.org/en/about/criteria/
- https://www.privacyguides.org/en/tools/
- https://prism-break.org/
- https://www.privacytools.io/
- https://switching.software/
- https://alternativeto.net/
- https://github.com/tycrek/degoogle
- https://github.com/Lissy93/personal-security-checklist
- https://github.com/awesome-selfhosted/awesome-selfhosted
- https://github.com/awesome-foss/awesome-sysadmin

List quality and maintenance:
- https://github.com/sindresorhus/awesome
- https://github.com/sindresorhus/awesome-lint
- https://github.com/dkhamsing/awesome_bot
- https://github.com/lycheeverse/lychee
- https://github.com/tcort/markdown-link-check
- https://github.com/DavidAnson/markdownlint
- https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/configuring-issue-templates-for-your-repository

Privacy evidence sources:
- https://tosdr.org/
- https://reports.exodus-privacy.eu.org/en/
- https://www.w3.org/WAI/WCAG22/Understanding/non-text-content.html
- https://www.eff.org/issues/privacy
- https://www.mozilla.org/en-US/privacy/
- https://github.com/arkenfox/user.js/wiki

## Open Questions
- None blocking prioritization. Maintainers can choose the exact strictness level for admission criteria, but the next work can start from local validation failures and the existing issue-template boundary.

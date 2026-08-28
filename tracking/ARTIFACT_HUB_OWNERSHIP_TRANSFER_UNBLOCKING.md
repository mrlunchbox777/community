# Artifact Hub Ownership Transfer Unblocking Log

Last updated: `2026-08-10`

This document tracks the nine remaining rows that require additional evidence, manual investigation, or an explicit executive decision before they can move forward:

- Four source-research rows: `cronce`, `fermosit`, `microsoft`, and `softonic`.
- Five contact-blocked rows: `fold`, `ibm-charts`, `lifen`, `owkin`, and `ruguodangshi`.

The main transfer plan remains the source of truth for the overall 136-row project. This document is the working log for resolving these nine cases one at a time.

## Operating Rules

- Work one repository at a time unless a clearly shared discovery justifies grouping.
- Read-only research may continue without external-write approval.
- A manual or exceptional contact route must be explicitly recorded with its reason, audience, privacy level, and expected evidence.
- Do not treat a private form, guessed email, former maintainer, repository contributor, or general company contact as durable ownership evidence without an explicit decision to accept that limitation.
- Do not contact a project until the exact destination, proposed content, evidence standard, and exception rationale are recorded here.
- Do not change the public inventory or activity overlay until the exact row diff or activity entry has been reviewed and approved.
- Keep internal prioritization and executive rationale out of public GitHub content.
- A case may move to disposition without outreach when evidence supports an archived, dead, duplicate, retired, or otherwise terminal listing.
- A case may remain blocked when the available channel is private, restricted, unauthenticated, or not clearly project-owned.
- Every decision must record what evidence would reverse it.

## Status Model

- `research`: source, chart identity, lifecycle, or owner is unresolved.
- `contact-blocked`: a plausible source exists, but no acceptable project-owned writable channel is available.
- `decision-needed`: evidence is sufficient for an explicit executive choice among outreach, private escalation, disposition, or continued research.
- `contact-approved`: a destination and message are approved, but no external write has occurred.
- `contacted`: an approved external contact was posted or sent and durable evidence was recorded.
- `disposition-candidate`: evidence supports administrator review rather than ownership outreach.
- `resolved`: the row has a documented terminal outcome or has moved into the main transfer workflow.

## Queue Overview

| Repository | Current queue | Current blocker | Initial handling |
| --- | --- | --- | --- |
| `cronce` | source research | Multi-chart feed; tracked chart source and project-owned contact are unresolved. | Reconcile the exact `billet` chart source before contact. |
| `fermosit` | source research | Multi-tenant Harbor feed; tracked chart identity and owner are unresolved. | Identify the tracked chart and publishing owner. |
| `microsoft` | source research | Four charts have mixed provenance; one lacks source mapping; central issue path is restricted. | Reconcile chart by chart and find a writable owner channel. |
| `softonic` | source research | Active tracked package lacks source, maintainer, and chart-specific owner metadata. | Identify the publishing source and owning team. |
| `fold` | contact blocked | Active source, but issue creation is restricted and only private support routes were found. | Decide whether a private escalation is acceptable. |
| `ibm-charts` | contact blocked | IBM excludes the published `stable` directory from GitHub contributions. | Find an IBM-owned channel or route to administrator disposition. |
| `lifen` | contact blocked | Source is archived; GitHub rejected issue creation; no durable public channel found. | Search for a project-owned successor or approve a private escalation. |
| `owkin` | contact blocked | Source is archived; GitHub rejected issue creation; no durable public channel found. | Search for a project-owned successor or approve a private escalation. |
| `ruguodangshi` | contact blocked | Inactive fork with Issues and Discussions disabled; owner relationship is unverified. | Reconcile fork ownership and decide whether further contact is justified. |

## Decision Workflow

For each case:

1. Capture the current Artifact Hub listing, repository ID, package identity, registered feed, and current public row.
2. Record the strongest source, lifecycle, ownership, and contact evidence found.
3. Identify the smallest set of remaining unknowns.
4. List candidate actions: continue research, public outreach, private escalation, administrator disposition, or no action.
5. Make the executive decision for that case and record the exception rationale if it departs from the normal rules.
6. If contact is approved, record the exact destination, title or subject, message, and evidence expected from the response.
7. Request approval before the external write.
8. Re-fetch and verify the external result, then update this log, the local plan, and the public tracker as applicable.

## Case Log

### `cronce`

- Status: `research`
- Evidence: The `billet` package and `https://charts.cronce.io/index.yaml` feed are live, but the feed is multi-chart and provides no canonical source or project-owned maintainer identity for the tracked row.
- Current contacts: `mike@cronce.io` appears in feed metadata; this is personal contact evidence and is not yet sufficient to establish current ownership.
- Unknowns: Exact source repository, current owner, and whether the inventory row represents only `billet` or a broader feed identity.
- Candidate actions: Reconcile package provenance; consider a clearly labeled private contact only with an explicit exception; route to disposition if ownership cannot be established.
- Decision: `pending`
- Next step: Isolate the `billet` chart source and identify a project-owned contact.
- Reversal evidence: A repository or maintainer explicitly identifying the source and Artifact Hub owner.

### `fermosit`

- Status: `research`
- Evidence: The Harbor feed at `https://harbor.fermosit.es/chartrepo/library/index.yaml` is multi-tenant and contains unrelated packages. The tracked inventory row cannot currently be mapped to one chart or owner.
- Current contacts: The inventory contains personal contact evidence only.
- Unknowns: Tracked chart name, publishing project, canonical source, and authoritative owner.
- Candidate actions: Inspect Artifact Hub package history and feed metadata; request clarification from a clearly identified project owner if found; otherwise retain the blocker.
- Decision: `pending`
- Next step: Reconcile the tracked package identity against the Harbor feed.
- Reversal evidence: A unique chart-to-source mapping and a project-owned maintainer channel.

### `microsoft`

- Status: `research`
- Evidence: The feed at `https://microsoft.github.io/charts/repo/index.yaml` is live, but the four tracked packages have mixed Microsoft/Azure provenance. The cognitive-services chart lacks source mapping, and the central `microsoft/charts` issue path is restricted.
- Current contacts: Microsoft organization channels exist, but no chart-specific writable owner path has been validated.
- Unknowns: Chart-by-chart canonical sources, responsible teams, and an acceptable contact route.
- Candidate actions: Reconcile each package separately; use an identified team-owned channel; consider administrator disposition only for a package with terminal evidence.
- Decision: `pending`
- Next step: Build a package-by-package provenance table and identify the owning Microsoft teams.
- Reversal evidence: Exact source and team ownership for each tracked package, plus a usable team channel.

### `softonic`

- Status: `research`
- Evidence: The active `crossplane-softonic-factory` package is present in the large `https://charts.softonic.io/index.yaml` feed, but it has no source, maintainer, or chart-specific owner metadata.
- Current contacts: Related Softonic repositories and organization contacts exist, but they do not establish ownership of this package.
- Unknowns: Publishing source, current chart owner, and project-owned contact.
- Candidate actions: Inspect feed history and package metadata; identify the relevant Softonic team; do not contact a related repository by inference.
- Decision: `pending`
- Next step: Identify the chart publishing pipeline and owning team.
- Reversal evidence: Chart-specific source metadata or an explicit owner response.

### `fold`

- Status: `contact-blocked`
- Evidence: `fold-team/helm-charts` is active and publishes the feed, but GitHub reports issue creation is restricted. Private support routes were found, but no durable public maintainer thread exists.
- Current contacts: No approved public contact.
- Unknowns: Whether a project-owned private support route can provide durable ownership evidence and whether the project wants to retain the listing.
- Candidate actions: Remain blocked; approve a private escalation as an exception; route to disposition only with stronger terminal evidence.
- Decision: `pending`
- Next step: Decide whether private support contact is acceptable and what evidence must be retained.
- Reversal evidence: A public issue/discussion, project-owned support reference, or maintainer confirmation.

### `ibm-charts`

- Status: `contact-blocked`
- Evidence: IBM's `stable` feed is confirmed, but IBM contribution guidance excludes the published `stable` directory from GitHub contributions and routes it through IBM's internal build process.
- Current contacts: No valid public metadata-change path.
- Unknowns: IBM-owned support or maintainer channel capable of handling the `artifacthub-repo.yml` metadata and claim.
- Candidate actions: Find IBM support ownership; do not open a no-change PR; request administrator disposition if IBM confirms the listing is historical or unsupported.
- Decision: `pending`
- Next step: Search for an IBM-owned support or product-maintainer route.
- Reversal evidence: An IBM team accepting responsibility or an explicit terminal disposition.

### `lifen`

- Status: `contact-blocked`
- Evidence: `honestica/lifen-charts` is archived. GitHub rejected issue creation, and the official Lifen forms do not provide a durable public maintainer thread.
- Current contacts: Official private forms only.
- Unknowns: Current Lifen or Honestica owner, successor, and whether the historical listing should be retained.
- Candidate actions: Search for a public successor or organization contact; approve private escalation only as an explicit exception; request disposition after owner review.
- Decision: `pending`
- Next step: Identify a current project-owned owner or successor before contacting a private form.
- Reversal evidence: Current owner confirmation, successor confirmation, or an explicit removal request.

### `owkin`

- Status: `contact-blocked`
- Evidence: `owkin/charts` is archived. GitHub rejected issue creation, and the official Owkin contact form is general/business contact rather than a durable chart-maintainer channel.
- Current contacts: Official private general contact only.
- Unknowns: Current chart owner, successor, and intended disposition of the historical listing.
- Candidate actions: Search for an Owkin platform or infrastructure team; approve private escalation only with a defined evidence plan; request disposition if terminal evidence becomes sufficient.
- Decision: `pending`
- Next step: Find a chart-specific or platform-owned contact.
- Reversal evidence: Explicit Owkin ownership or disposition confirmation.

### `ruguodangshi`

- Status: `contact-blocked`
- Evidence: The source is an inactive fork of `cloudnativeapp/charts`; Issues and Discussions are disabled, and the Aliyun Hub route is unavailable during upgrade. The parent repository does not prove that the fork owner maintains this Artifact Hub listing.
- Current contacts: No authoritative project-owned channel.
- Unknowns: Whether the fork owner controls the listing and whether the listing is a duplicate or historical entry.
- Candidate actions: Reconcile the Artifact Hub package and fork history; search for an owner-controlled channel; route to disposition if the listing is demonstrably orphaned or duplicate.
- Decision: `pending`
- Next step: Establish whether the fork owner has any relationship to the published listing.
- Reversal evidence: Fork-owner confirmation, parent-project ownership confirmation, or administrator duplicate evidence.

## Decision Record Template

Copy this block for each one-at-a-time review:

```md
### Decision: `<repository>` - `<date>`

- Evidence reviewed:
- New evidence:
- Decision:
- Exception to normal policy:
- Exact destination, if contact is approved:
- Exact message or subject:
- Evidence required from the response:
- Public tracker impact:
- Local queue impact:
- External write approval:
- Verification result:
- Reversal evidence:
```

## Current Boundary

No new outreach is authorized by this document. The next action is to select one row, gather or record the missing evidence, and make an explicit decision before preparing any external write.

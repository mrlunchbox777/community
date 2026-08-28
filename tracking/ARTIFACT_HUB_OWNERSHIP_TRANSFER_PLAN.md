# Artifact Hub Repository Ownership Transfer Review Plan

This plan covers the review and cleanup of the 136 Artifact Hub repositories tracked in [helm/community#428](https://github.com/helm/community/issues/428). It is based on a first-pass review performed on 2026-07-23.

## Goals

1. Make the issue accurately reflect completed replies and ownership claims.
2. Identify and validate the canonical source repository for every entry.
3. Identify current maintainers and at least one reliable public contact method.
4. Separate ownership-transfer work from cleanup of abandoned or invalid Artifact Hub entries.
5. Leave evidence for every change so the tracker can be audited and maintained.

## Reporting and Approval Gate

The original inventory in issue #428 is maintained by the issue maintainers. [Issue comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) is a dated activity overlay containing only repositories contacted or otherwise changed. It does not restate or replace the complete inventory. Use a single heading for each date, appending later same-day actions to the existing dated section, so issue maintainers can apply the work to the original inventory. Each date gets one table for repository rows, followed by an optional addendum for explanatory notes or blockers. Mention `@scottrigby` at most once in that date's addendum, never once per batch or repository.

No write action may be performed without the user's explicit approval. This includes changes to local files, GitHub issues, comments, pull requests, or repositories; Artifact Hub; email; Slack; and any other local or external system. Before requesting approval:

1. State the exact destination of the proposed write.
2. Show the exact content or field changes to be made.
3. For issue-inventory updates, provide a before/after diff for every affected row and any summary-count changes. For activity-overlay updates, show the exact dated table rows and optional addendum to be appended. Keep all same-day repository changes in the table; do not create separate batch sections.
4. State any related actions that are not included in the approval request.

Approval applies only to the exact changes presented. Research and other read-only validation may continue without write approval.

For every outreach posting, update the public activity tracker and the local audit log as part of the same completed work; do not treat either record as an optional follow-up. Keep local prioritization labels, including `Tier 1` and `Tier 2`, out of all public GitHub content; record them only in local documents. After every GitHub write, fetch the live object and verify that the rendered Markdown has the intended table structure, line breaks, links, and content before reporting the write complete; repair formatting immediately if verification fails.

Follow-up response policy: propose a response only when either another party has responded and appears to need information or action from Helm, or Helm is the latest responder and that response is more than one month old. Before posting any follow-up response, ask for explicit approval and provide the category (`needs-response` or `stale-latest-response`), the review link to the exact thread, the proposed destination, and the exact response text. Do not post routine reminders or follow-ups without that approval.

## Baseline

The issue contains 86 rows under "Repositories with Identified Git Sources" and 50 rows under "Repositories WITHOUT Identified Git Sources."

| Metric                           | Identified source | Without identified source | Total |
| -------------------------------- | ----------------: | ------------------------: | ----: |
| Repositories                     |                86 |                        50 |   136 |
| Maintainer listed as `_unknown_` |                13 |                        14 |    27 |
| Marked contacted                 |                18 |                         2 |    20 |
| Marked replied                   |                 1 |                         0 |     1 |
| Marked claimed                   |                 1 |                         0 |     1 |

The recorded reply and claim counts are already stale. The first-pass review found evidence for at least six replies and four completed claims. Off-GitHub replies or claims may exist and need confirmation from Helm or Artifact Hub administrators.

## Immediate Corrections

Apply a small, evidence-backed update before beginning new outreach.

| Repository  | Contact evidence                                                                                                           | Replied | Claimed         | Required update                                                                                      |
| ----------- | -------------------------------------------------------------------------------------------------------------------------- | ------- | --------------- | ---------------------------------------------------------------------------------------------------- |
| camel-k     | [apache/camel-k#6434](https://github.com/apache/camel-k/issues/6434#issuecomment-3846946968)                               | Yes     | Yes             | Check both fields; update the deleted `apache/camel-kcharts` source to the validated current source. |
| carlosjgp   | [carlosjgp/open-charts#5](https://github.com/carlosjgp/open-charts/issues/5#issuecomment-3973872213)                       | Yes     | No evidence yet | Check Replied; follow up for completion evidence.                                                    |
| ceph-csi    | [ceph/ceph-csi#5902](https://github.com/ceph/ceph-csi/issues/5902#issuecomment-3744444625)                                 | Yes     | Yes             | Check both fields; record that ownership moved from `helm` to `ceph-csi`.                            |
| couchbase   | [couchbase-partners/helm-charts#152](https://github.com/couchbase-partners/helm-charts/issues/152#issuecomment-3729166499) | Yes     | No              | Check Replied; replace former employees with a current team contact after confirmation.              |
| cowboysysop | [cowboysysop/charts#1013](https://github.com/cowboysysop/charts/issues/1013#issuecomment-3703603394)                       | Yes     | Yes             | No status change; use as the reference example for completion evidence.                              |
| concourse   | [concourse/concourse-chart#404](https://github.com/concourse/concourse-chart/issues/404#issuecomment-3700924568)           | Yes     | Yes             | Check both fields and move the row to the identified-source section.                                 |

Correct two invalid contact attempts before counting them as successful outreach:

- `crate`: [crate/helm-charts#10](https://github.com/crate/helm-charts/issues/10) contains copied `cowboysysop` repository and maintainer details. Correct the issue or open a clean replacement, then retain the valid link.
- `smallstep`: [smallstep/helm-charts#266](https://github.com/smallstep/helm-charts/issues/266) links to the `couchbase` Artifact Hub entry. Correct the issue before following up.

Thirteen contacted threads were unresolved and already stale at the time of review: `adwerx`, `apicheck`, `appdynamics`, `architectminds`, `aws`, `buildkite`, `cetic`, `cgroschupp`, `chubaofs`, `cloudwatch-agent`, `couchdb`, `couchbase`, and `wso2`. Most have no response; `couchbase` has a reply from a former maintainer but no current owner has completed the transfer. These should receive one evidence-based follow-up after their source and contacts are revalidated.

## Tracker Model

Keep the existing `Contacted`, `Replied`, and `Claimed` fields, but apply consistent definitions:

- **Contacted**: a verifiable public issue, pull request, discussion, mailing-list archive, or other durable reference exists and contains correct repository details.
- **Replied**: an identified maintainer or owning organization acknowledged the request. An automated response or a comment only redirecting to an unconfirmed person does not establish a current maintainer.
- **Claimed**: a maintainer explicitly confirmed the Artifact Hub claim or an Artifact Hub/Helm administrator verified the owner change.

Add fields during the review, either in the issue table or in a linked working document:

| Field             | Purpose                                                                                           |
| ----------------- | ------------------------------------------------------------------------------------------------- |
| Canonical source  | Current Git URL after following redirects and verifying chart provenance.                         |
| Contact           | Public issue/discussion URL, team address, or project communication channel.                      |
| Source confidence | `confirmed-by-index`, `confirmed-by-repository`, `strong-candidate`, or `unverified`.             |
| Lifecycle         | `active`, `archived`, `retired/renamed`, `dead-endpoint`, or `unknown`.                           |
| Last verified     | Date the source, maintainers, contact, and transfer status were checked.                          |
| Notes             | Successor projects, invalid contacts, multi-project repositories, or administrator-only evidence. |

Do not treat a repository redirect, recent contributor, historical chart email, or former employee as proof of current ownership.

## Review Workflow

Review each repository using the following order.

1. Capture the current issue row before changing it.
2. Fetch the Helm repository `index.yaml` and inspect the newest relevant chart's `sources`, `home`, `maintainers`, annotations, and package URLs.
3. Normalize GitHub or GitLab URLs by following redirects and preserving canonical owner/name casing.
4. Verify that the source actually publishes the tracked Artifact Hub repository. A similarly named project is not sufficient.
5. Record source lifecycle, including archived repositories, retired organizations, dead chart endpoints, and successor projects.
6. Find maintainers in `artifacthub-repo.yml`, current `Chart.yaml` files, `CODEOWNERS`/`OWNERS`, maintainer documentation, and recent release metadata, in that order.
7. Prefer a project-owned public channel over a personal email. Do not infer ownership solely from commit counts.
8. Review existing contact-thread comments and, where administrators have access, current Artifact Hub organization ownership.
9. Update the tracker with evidence and a verification date.
10. Contact only after source and maintainer validation, using a template containing the exact Artifact Hub repository URL and claim instructions.

Conduct outreach in reviewed batches of five repositories. Fill batches with repositories whose source and current project-owned contact are both confirmed. After those are exhausted, source-confirmed repositories with less-authoritative contacts may be considered, but keep them until last. Research strong but unconfirmed source candidates without contacting them until provenance is confirmed.

## Source Cleanup

### Correct First

These identified-source rows have clear malformed, deleted, or renamed URLs that should be corrected before outreach:

| Repository     | Problem                                    | Candidate canonical source                                                          |
| -------------- | ------------------------------------------ | ----------------------------------------------------------------------------------- |
| apicheck       | Listed source is deleted                   | [BBVA/apicheck](https://github.com/BBVA/apicheck)                                   |
| appdynamics    | Repository transferred                     | [CiscoDevNet/appdynamics-charts](https://github.com/CiscoDevNet/appdynamics-charts) |
| camel-k        | Listed source is deleted                   | [apache/camel-k](https://github.com/apache/camel-k)                                 |
| dacruz21       | Repository renamed/transferred             | [typokign/helm-charts](https://github.com/typokign/helm-charts)                     |
| equinor-charts | Duplicated `charts` in URL                 | [equinor/helm-charts](https://github.com/equinor/helm-charts)                       |
| eventstore     | Organization renamed                       | [kurrent-io/EventStore.Charts](https://github.com/kurrent-io/EventStore.Charts)     |
| gradiant       | Repository moved                           | [Gradiant/bigdata-charts](https://github.com/Gradiant/bigdata-charts)               |
| squidex        | Repository renamed                         | [Squidex/squidex-hosting](https://github.com/Squidex/squidex-hosting)               |
| talend         | Chart path was appended to repository name | [talend/helm-charts-public](https://github.com/talend/helm-charts-public)           |
| waldur         | Repository transferred                     | [waldur/waldur-helm](https://github.com/waldur/waldur-helm)                         |
| wombat         | Malformed repository and chart path        | [esl/helm-chart](https://github.com/esl/helm-chart)                                 |

The chart path and Artifact Hub identity still need to be verified before accepting each candidate. In particular, `k8s-dashboard` now redirects to `kubernetes-retired/dashboard` and `volcano` to `volcano-retired/charts`; these are lifecycle findings, not active maintainer contacts.

Other listed sources currently appear deleted or malformed and require provenance research rather than a guessed replacement: `inspur`, `kiwigrid`, `kremers`, `microsoft`, `mirusresearch`, `pl-helm-charts`, `purestorage`, and `uswitch`.

### Reclassify Known Git Sources

Move rows out of the "WITHOUT Identified Git Sources" section once chart provenance is confirmed. Start with the strongest cases:

| Repository | Candidate source                                                                  | Evidence to verify                                |
| ---------- | --------------------------------------------------------------------------------- | ------------------------------------------------- |
| ibm-charts | [IBM/charts](https://github.com/IBM/charts)                                       | The Helm URL is already a raw GitHub path.        |
| jenkins    | [jenkinsci/kubernetes-operator](https://github.com/jenkinsci/kubernetes-operator) | The Helm URL is already a raw GitHub path.        |
| smueller18 | [smueller18/helm-charts on GitLab](https://gitlab.com/smueller18/helm-charts)     | GitLab Pages namespace and project name.          |
| concourse  | [concourse/concourse-chart](https://github.com/concourse/concourse-chart)         | Existing successful claim issue.                  |
| cloudposse | [cloudposse/charts](https://github.com/cloudposse/charts)                         | Source exposed by the live chart index.           |
| keel       | [keel-hq/keel](https://github.com/keel-hq/keel)                                   | Source exposed by the live chart index.           |
| newrelic   | [newrelic/helm-charts](https://github.com/newrelic/helm-charts)                   | Packages are served from repository releases.     |
| seldon     | [SeldonIO/seldon-core](https://github.com/SeldonIO/seldon-core)                   | Source and chart paths exposed by the live index. |
| simplyzee  | [simplyzee/helm-charts](https://github.com/simplyzee/helm-charts)                 | Publishing repository and chart metadata.         |

Research `banzaicloud-stable`, `larribas`, `softonic`, `soluto`, `trickster`, and `wso2` next. Plausible repositories exist, but dead endpoints or multi-project scope make their identity less certain.

## Maintainer and Contact Cleanup

There are 27 `_unknown_` maintainer rows. At least 21 appear to have an identifiable organization, repository owner, chart maintainer, or authoritative repository contact. Resolve high-confidence entries first:

| Repository         | Candidate maintainer/contact                          | Evidence source                                                                                                         |
| ------------------ | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| ealenn             | Rudy Marchandise / `@Ealenn`                          | Current chart metadata in [Ealenn/charts](https://github.com/Ealenn/charts).                                            |
| gresearch          | Current maintainers listed per chart                  | Current `Chart.yaml` files in [G-Research/charts](https://github.com/G-Research/charts).                                |
| prometheus-msteams | `bzon`, `ckotzbauer`, `kbudde`, `Knappek`, `zhan9san` | [Chart.yaml](https://github.com/prometheus-msteams/prometheus-msteams/blob/master/chart/prometheus-msteams/Chart.yaml). |
| cloudposse         | Cloud Posse repository issues or organization contact | Live index and [cloudposse/charts](https://github.com/cloudposse/charts).                                               |
| newrelic           | New Relic chart team through repository issues        | [newrelic/helm-charts](https://github.com/newrelic/helm-charts).                                                        |
| seldon             | Seldon Core team through repository issues            | [SeldonIO/seldon-core](https://github.com/SeldonIO/seldon-core).                                                        |
| simplyzee          | `@simplyzee` / `@zee-ahmed` through repository issues | Publishing repository and chart metadata.                                                                               |

Use repository-owned issue channels for active organization repositories where no authoritative individual is named: `cryptlex`, `jitterbit`, `snyk`, `crate`, and `ibm-charts`. Use the repository owner as the initial contact for personal repositories such as `dniel`, `pcktdmp`, and `larribas`, but require an explicit ownership confirmation.

Classify dormant or archived projects before outreach: `flink-operator`, `kubedex`, and `pfisterer-knox`. A successor project must explicitly confirm it owns the same Artifact Hub repository; similarity alone is not enough.

## Execution Batches

Keep pull requests, outreach, and activity-log updates reviewable. Research may cover more repositories, but each outreach batch should contain five approved, highest-confidence targets. Each batch should include evidence links and avoid mixing confirmed corrections with speculative source changes. After completing each approved execution batch, request approval to append exact rows to that date's existing activity section, creating the date heading only when the first action for that date is recorded.

### Execution Order Decision

Use a two-track sequence:

1. Complete a read-only population census of all 136 inventory rows, assigning each row a provisional Tier 1, Tier 2, or reason-based queue.
2. Finish Tier 1 outreach and its claim or terminal-outcome processing.
3. Finish Tier 2 outreach in reviewed batches of five.
4. Process the reason queues: source research, lifecycle research, contact-blocked, disposition, deferred, and no-outreach-needed.

Research for the census and reason queues may continue in the background, but public outreach follows the Tier 1 then Tier 2 order. The public tracker continues to record evidence and outcomes without exposing internal tier labels.

### Population Census: 2026-07-30

The read-only census produced a disjoint partition of all 136 inventory rows. Terminal states take precedence over earlier contact history; the public tracker section counts remain 84 identified-source and 52 source-unknown rows until issue maintainers apply the planned 87/49 reclassification.

| Queue | Count |
| --- | ---: |
| Contacted, awaiting outcome, or claimed | 66 |
| Disposition | 16 |
| Lifecycle research | 8 |
| Source research | 40 |
| Tier 1 | 0 |
| Tier 2 | 0 |
| Contact blocked | 5 |
| No outreach needed | 1 |
| **Total** | **136** |

**Tier 1 population:** No uncontacted candidates remain; `talend` was reclassified as an active outreach candidate and contacted.

**Tier 2 population:** Complete. The first five-candidate batch and the two-repository completion batch were posted.

**Disposition:** `appdynamics`, `buildkite`, `cgroschupp`, `chubaofs`, `cloudwatch-agent`, `crate`, `enapter`, `eventstore`, `gradiant`, `infobloxopen`, `pangeo`, `smueller18`, `squidex`, `stardog`, `waldur`, and `wavefront`.

**Lifecycle research:** `dacruz21`, `flink-operator`, `k8s-dashboard`, `kubedex`, `monocular`, `pfisterer-knox`, `quarks`, and `volcano`.

**Contact blocked:** `ibm-charts`, `lifen`, `owkin`, `ruguodangshi`, and `snyk`.

**No outreach needed:** `wombat`.

**Source research:** `astarte`, `balle-petersen`, `banzaicloud-stable`, `brannon`, `camptocamp`, `choerodon`, `cleardata`, `cronce`, `datawire`, `dgraph`, `dragonchain`, `fermosit`, `fold`, `forseti-security`, `franzinc`, `fyipe`, `gomods`, `gp42`, `hue`, `inspur`, `k8s-land`, `kiwigrid`, `kremers`, `larribas`, `microsoft`, `mirusresearch`, `opsdroid`, `pl-helm-charts`, `pomerium`, `purestorage`, `redsky`, `runix`, `softonic`, `soluto`, `sstarcher`, `t3n`, `trickster`, `uswitch`, `ververica`, and `vertigo`. These are not outreach candidates until provenance is verified.

### Batch 1: Reconcile Existing Contacts

- Apply the six evidence-backed reply/claim statuses.
- Repair `crate` and `smallstep` outreach.
- Update source redirects or deletions discovered in those 20 rows.
- Follow up once on stale threads after validating current contacts.

### Batch 2: Repair Source Data

- Correct unambiguous malformed and redirected URLs.
- Reclassify conclusively Git-backed rows from the "WITHOUT" section.
- Label archived, retired, dead, and unverified sources instead of forcing them into an active-source category.

### Batch 3: Resolve Unknown Maintainers

- Replace high-confidence `_unknown_` values from current chart or ownership metadata.
- Add public contact channels for organization-owned repositories.
- Leave unresolved entries explicitly marked `unverified`; do not fill them with contributor guesses.

### Batch 4: Validate Remaining Rows

- Review all remaining known-source rows alphabetically in groups of 10 to 15.
- Review all remaining source-unknown rows by evidence quality: live index metadata, URL inference, dead endpoint, then no lead.
- Open or update contact threads only after each row passes source validation, using approved batches of five.

### Batch 5: Close or Escalate

- Ask Artifact Hub administrators to verify claims that occurred outside public threads.
- Decide whether abandoned, duplicate, or dead repositories should be transferred, disabled, or removed.
- Close issue #428 only when every row is claimed or has a documented terminal disposition.

### Tier 2: Lower-Priority Contactable Repositories

Tier 2 is an internal prioritization queue. Do not add a Tier 2 column to the public tracker; maintainers need the evidence and disposition state, not Helm's internal ordering.

#### Scope

- Include repositories that are source-confirmed and have a plausible project-owned contact, but are lower priority because the feed is legacy, dormant, low-usage, or has weaker lifecycle evidence.
- Exclude repositories with no writable contact channel; keep those in the separate `contact-blocked` queue, as with `snyk`.
- Exclude archived, retired, dead-endpoint, duplicate, or successor-uncertain repositories; keep those in the disposition or source-research queues.
- Do not move a repository into Tier 2 solely because Tier 1 outreach is unanswered. Tier 2 is based on evidence quality and priority, not response status.

#### Routing Outside Tier 2

Do not create a generic Tier 3 unless a distinct, approved workflow is later needed. Route excluded repositories by the reason they failed Tier 2 preflight:

- `contact-blocked`: no project-owned writable contact channel, as with `snyk`.
- `source-research`: canonical source or chart provenance is not yet verified.
- `lifecycle-research`: source is known but active, dormant, successor, or retirement status is unresolved.
- `disposition`: source is dead, archived, retired, duplicate, or otherwise needs transfer, disablement, removal, or administrator decision.
- `deferred`: an explicit reason exists to wait before contacting, as with `crate`.
- `no-outreach-needed`: ownership is already established outside Helm or another terminal state is documented, as with `wombat`.

#### Provisional Queue

The Tier 2 queue is complete. The table below records the two-repository completion batch alongside the first five-target batch:

| Repository | Artifact Hub repository | Canonical source | Lifecycle | Contact | Preflight result |
| --- | --- | --- | --- | --- | --- |
| simplyzee | `452b04d1-7c80-4d06-9ff5-2c441df030cc` | [simplyzee/simplyzee-charts](https://github.com/simplyzee/simplyzee-charts) | dormant | [issue #1](https://github.com/simplyzee/simplyzee-charts/issues/1) | Tier 2 ownership request posted. |
| equinor-charts | `5d42ffed-36d1-4434-9f14-e7f5218d22bc` | [equinor/helm-charts](https://github.com/equinor/helm-charts) | dormant/stale | [issue #12](https://github.com/equinor/helm-charts/issues/12) | Tier 2 ownership request posted. |
| dhiatn | `63c457f1-55ee-4a10-90ce-7ee88566e155` | [DhiaTN/helm-kafka-topics-ui](https://github.com/DhiaTN/helm-kafka-topics-ui) | dormant/legacy | [issue #3](https://github.com/DhiaTN/helm-kafka-topics-ui/issues/3) | Tier 2 ownership request posted. |
| lohmag | `167a46a3-ab4e-4c5f-b2a7-460516274cae` | [lohmag/helm-charts](https://github.com/lohmag/helm-charts) | dormant/legacy | [issue #2](https://github.com/lohmag/helm-charts/issues/2) | Tier 2 ownership request posted. |
| mtls | `802f1dcd-b76e-46b5-8810-ecbecca953c2` | [drGrove/charts](https://github.com/drGrove/charts) | dormant/legacy | [issue #1](https://github.com/drGrove/charts/issues/1) | Tier 2 ownership request posted. |
| qamatic | `0b975caf-0336-4ab6-9911-9ae00f182b72` | [qamatic/charts](https://github.com/qamatic/charts) | dormant/legacy | [issue #1](https://github.com/qamatic/charts/issues/1) | Tier 2 ownership request posted. |
| rasooll | `bdf53655-eccf-4056-9962-b028c159ab3c` | [rasooll/helm-charts](https://github.com/rasooll/helm-charts) | dormant/legacy | [issue #1](https://github.com/rasooll/helm-charts/issues/1) | Tier 2 ownership request posted. |

All seven Tier 2 candidates were contacted in reviewed batches: five in the first batch and two in the completion batch.

The initially considered candidates were classified as follows:

- `dacruz21` has a corrected successor source but a dead endpoint and routes to `lifecycle-research`/`disposition`.
- `stardog` has an archived source and routes to disposition-first outreach, not the normal Tier 2 queue.
- `ibm-charts` has confirmed legacy Git provenance but no writable GitHub contact channel and routes to `contact-blocked`.

#### Selection And Preflight

Review the provisional queue in a fresh read-only pass before contacting anyone:

1. Verify the current Artifact Hub repository URL, repository ID, Helm ownership, and enabled state.
2. Verify that the canonical source still publishes the tracked listing and classify its lifecycle.
3. Confirm a current project-owned contact channel; do not use former maintainers or guessed contributors.
4. Search for duplicate ownership requests and existing project discussions before opening a thread.
5. Assign the repository to Tier 2, `contact-blocked`, `disposition`, or `source-research` based on the evidence.

#### Outreach Execution

- Use the same reviewed batches of five as Tier 1, but do not pad a batch with candidates that fail the preflight.
- Use the standard ownership-transfer message with the exact Artifact Hub URL, canonical source, claim instructions, and redirect request.
- Request approval for the exact destinations and messages before posting.
- Record contacted repositories in the existing dated tracker table; do not create tier or batch sections in the public tracker.
- Keep one optional explanatory addendum after the dated table and mention `@scottrigby` no more than once in that addendum.

#### Completion Criteria

Tier 2 outreach is complete for a repository when the claim is confirmed, the maintainer provides a documented terminal disposition, or no authoritative owner/contact can be established after the approved contact path is exhausted. Move repositories between queues when evidence changes; do not leave a stale Tier 2 label as the final state.

### Disposition Research: 2026-07-30

This read-only review covered the first five disposition candidates. No GitHub, Artifact Hub, or tracker writes were made.

| Repository | Artifact Hub state | Canonical source and current evidence | Local outcome |
| --- | --- | --- | --- |
| `crate` | Listing `crate` remains enabled and owned by `helm`; source index is live. | [crate/helm-charts](https://github.com/crate/helm-charts) is no longer maintained. The project explicitly requested Artifact Hub removal in [issue #10](https://github.com/crate/helm-charts/issues/10#issuecomment-5104176288), after deprecating and archiving the project in [PR #11](https://github.com/crate/helm-charts/pull/11). | Keep in disposition. Request administrator removal; do not seek a replacement owner. |
| `eventstore` | Listing `eventstore` remains enabled and owned by `helm`; the registered `eventstore.github.io/EventStore.Charts` index is 404. | Canonical source is [kurrent-io/EventStore.Charts](https://github.com/kurrent-io/EventStore.Charts), archived by the owner on 2020-03-06. Its README explicitly deprecates the Helm chart. The renamed GitHub Pages URL is live, but the repository remains archived. | Keep in disposition. Recommend disablement or removal; ownership transfer is not appropriate. |
| `gradiant` | Listing `gradiant` remains owned by `helm`; the registered `gradiant.github.io/charts` index is 404. | The old source moved to [Gradiant/bigdata-charts](https://github.com/Gradiant/bigdata-charts), whose `bigdata-charts` index is live. Artifact Hub separately lists the active `gradiant-bigdata` repository as verified under Gradiant. | Keep in disposition. Treat `gradiant` as a stale duplicate and recommend removal or disablement; do not merge it with `gradiant-bigdata`. |
| `squidex` | Listing `squidex` remains enabled and owned by `helm`; the registered `squidex.github.io/squidex-docker` index is 404. | Candidate source is [Squidex/squidex-hosting](https://github.com/Squidex/squidex-hosting), a live Docker/hosting repository updated in 2026. GitHub Issues are disabled; its README directs support to the Squidex community forum. | Keep in disposition pending a project-owned forum decision. Recommend repointing only if the project confirms the chart identity; otherwise remove or disable. |
| `talend` | Listing `talend` remains enabled and owned by `helm`; the registered `/stable` index is live. Latest `vault-sidecar-injector` is version `4.3.2` with app version `7.2.1`. | [Talend/helm-charts-public](https://github.com/Talend/helm-charts-public) is public, active, and explicitly describes itself as Talend's maintained public chart registry. | Do not treat as terminal disposition. Route back to active ownership-outreach review using the corrected source and chart path. |

Disposition review evidence is read-only and current as of 2026-07-30. Any later removal, disablement, repointing, or ownership request requires a separate approved external write.

#### Remaining Disposition Queue Next Steps

| Repository | Current evidence | Next step |
| --- | --- | --- |
| `appdynamics` | The registered Artifact Hub index is dead; the source is now [CiscoDevNet/appdynamics-charts](https://github.com/CiscoDevNet/appdynamics-charts). Existing contact [issue #47](https://github.com/CiscoDevNet/appdynamics-charts/issues/47) is unresolved. | Revalidate the existing thread once, then request disablement or removal of the stale listing unless Cisco confirms it should be transferred. |
| `buildkite` | The source and index are live, but the repository README says the charts are deprecated and points users to [agent-stack-k8s](https://github.com/buildkite/agent-stack-k8s). Existing contact [issue #110](https://github.com/buildkite/charts/issues/110) is open. | Keep as disposition-oriented. Ask the project to choose transfer of the legacy listing or removal; do not treat the live index alone as evidence of active support. |
| `cgroschupp` | The index is live and the repository is unarchived but dormant since 2020. Existing ownership request [issue #1](https://github.com/cgroschupp/helm-charts/issues/1) remains open. | Revalidate the existing contact and follow up once; then record either a claim or a terminal inactive-listing decision. |
| `chubaofs` | The registered index is dead. The chart moved to the active [cubefs/cubefs-helm](https://github.com/cubefs/cubefs-helm), which already has the successor contact [issue #60](https://github.com/cubefs/cubefs-helm/issues/60). | Ask an Artifact Hub administrator to reconcile the old listing with the separately owned successor or remove it; do not open duplicate outreach. |
| `cloudwatch-agent` | The index is live, but [s2504s/charts](https://github.com/s2504s/charts) has GitHub Issues disabled. The existing source correction is a pull request, not a writable ownership channel. | Keep contact-blocked/disposition-oriented and request administrator disablement or removal; do not attempt GitHub outreach. |
| `enapter` | The source repository is archived while the old index remains live. No explicit removal statement or verified successor was found. | Treat as moderate-evidence administrator disposition review; request confirmation of disablement or removal rather than asserting automatic removal. |
| `infobloxopen` | [infobloxopen/cert-manager](https://github.com/infobloxopen/cert-manager) is archived and its README says the repository is no longer needed and will be deleted. | Request removal of the historical listing; no ownership outreach. |
| `lifen` | [honestica/lifen-charts](https://github.com/honestica/lifen-charts) is archived but still publishes an index containing both maintained and explicitly deprecated charts. GitHub rejected issue creation. | Route to contact-blocked. Identify a current Lifen/Honestica owner or successor through a non-GitHub project-owned channel before deciding removal. |
| `owkin` | [owkin/charts](https://github.com/owkin/charts) is archived, but its index remains live and its README describes an Owkin chart registry. GitHub rejected issue creation. | Route to contact-blocked. Seek an organization-level decision through another project-owned channel before disabling, removing, or identifying a successor. |
| `pangeo` | The source is archived and its README explicitly deprecates the chart in favor of [dask/daskhub](https://github.com/dask/daskhub). | Request removal or disablement of the old listing; do not transfer it to the successor without explicit confirmation. |
| `smueller18` | The GitLab source is dormant/retired and the plan already identifies the verified `andibraeu` listing as its successor. | Request removal or disablement of the old listing; do not duplicate outreach to the successor unless ownership reconciliation requires it. |
| `stardog` | The source is archived and explicitly deprecated as of 2026-03-05 in favor of [stardog-oss/kube-stardog-stack](https://github.com/stardog-oss/kube-stardog-stack/). | Request removal or disablement after recording the successor; do not transfer the retired listing by inference. |
| `waldur` | The old listing is separate from the active verified `waldur-charts` listing; the old source is [waldur/waldur-helm](https://github.com/waldur/waldur-helm). | Reconcile the duplicate with the current verified listing and request removal or disablement of the old entry; avoid duplicate ownership outreach. |
| `wavefront` | The source repository is archived and the old index remains live; no validated successor was found in this pass. | Request disablement or removal, or identify an authoritative successor before any transfer request. |

These 14 decisions complete the local next-step assignment for the remaining disposition queue. They are recommendations only; each external action still requires exact-destination approval.

### Lifecycle Research: 2026-07-31

This read-only review covered all eight repositories in the lifecycle-research queue. No GitHub, Artifact Hub, or public tracker writes were made. The findings route all eight to disposition-oriented handling; none should receive normal ownership-transfer outreach without new evidence.

| Repository | Artifact Hub state | Canonical source and current evidence | Lifecycle | Local outcome |
| --- | --- | --- | --- | --- |
| `dacruz21` | Listing `dacruz21` remains enabled and owned by `helm`; the registered `dacruz21.github.io/helm-charts` index returns 404. | [typokign/helm-charts](https://github.com/typokign/helm-charts) is the validated source candidate and is unarchived, but its last push was in 2020. | `dead-endpoint` | Move to disposition. Correct the source if retained, but do not contact until a current owner or supported replacement is established. |
| `flink-operator` | Listing remains enabled and owned by `helm`; the registered index is live but contains only April 2020 chart releases. | [GoogleCloudPlatform/flink-on-k8s-operator](https://github.com/GoogleCloudPlatform/flink-on-k8s-operator) is archived, explicitly marked deprecated, and directs users to [Apache Flink Kubernetes Operator](https://github.com/apache/flink-kubernetes-operator) or Google Cloud Dataproc. | `archived` | Move to disposition. Recommend removal or disablement of the historical listing; do not transfer it to the Apache successor by inference. |
| `k8s-dashboard` | Listing `k8s-dashboard` remains enabled and owned by `helm`; the registered `kubernetes.github.io/dashboard` index returns 404. | [kubernetes-retired/dashboard](https://github.com/kubernetes-retired/dashboard) is archived. The repository identity is explicitly retired, and no validated active owner for this Helm listing was established. | `retired/renamed` | Move to disposition. Recommend administrator review for removal or disablement; do not infer a successor claim. |
| `kubedex` | Listing remains enabled and owned by `helm`; [kubedex.github.io/charts/index.yaml](https://kubedex.github.io/charts/index.yaml) is live. | [Kubedex/charts](https://github.com/Kubedex/charts) is unarchived but dormant; its index was generated in August 2019 and the repository has not been updated since August 2019. | `unknown` | Move to disposition-oriented handling. Treat as a dormant legacy listing and seek an administrator or project decision rather than normal outreach. |
| `monocular` | Listing remains enabled and owned by `helm`; [helm.github.io/monocular/index.yaml](https://helm.github.io/monocular/index.yaml) is live, with the latest chart dated March 2020. | [helm/monocular](https://github.com/helm/monocular) is archived and explicitly described as obsolete. | `archived` | Move to disposition. Recommend removal or disablement; no ownership transfer is appropriate. |
| `pfisterer-knox` | Listing remains enabled and owned by `helm`; [pfisterer.github.io/apache-knox-helm/index.yaml](https://pfisterer.github.io/apache-knox-helm/index.yaml) is live, with the latest chart dated September 2022. | [pfisterer/apache-knox-helm](https://github.com/pfisterer/apache-knox-helm) is archived. No project-owned successor or current maintainer was validated. | `archived` | Move to disposition. Recommend removal or disablement unless a current Apache Knox owner explicitly confirms responsibility. |
| `quarks` | Listing remains enabled and owned by `helm`; [cloudfoundry-incubator.github.io/quarks-helm/index.yaml](https://cloudfoundry-incubator.github.io/quarks-helm/index.yaml) is live, with the latest `quarks` chart dated June 2021. | [cloudfoundry-incubator/quarks-helm](https://github.com/cloudfoundry-incubator/quarks-helm) and its source [quarks-operator](https://github.com/cloudfoundry-incubator/quarks-operator) are archived. | `archived` | Move to disposition. Recommend removal or disablement; do not infer that a current Cloud Foundry successor owns the listing. |
| `volcano` | The Helm-owned `volcano` listing remains enabled; its registered `volcano-sh.github.io/charts` index returns 404. | The old source [volcano-retired/charts](https://github.com/volcano-retired/charts) is a retired organization repository last updated in 2019. The active project now publishes through [volcano-sh/helm-charts](https://github.com/volcano-sh/helm-charts), whose site and repository were updated in July 2026. | `retired/renamed` | Move to disposition. Treat the old listing as a stale retired-source entry; request administrator reconciliation or removal, and do not transfer it to `volcano-sh` without explicit confirmation. |

The eight lifecycle findings increase the local disposition queue from `16` to `24` and reduce lifecycle research to `0`. These are local recommendations only; all removal, disablement, repointing, or ownership requests require separate exact-destination approval.

### Contact-Blocked Research: 2026-07-31

This read-only review searched for project-owned writable channels outside the disabled GitHub Issues and Discussions paths. The initial pass treated IBM's pull requests as a possible channel, but the repository's contribution guidance explicitly excludes the `stable` directory from GitHub contributions. After correction, only `snyk` is locally `contact-ready`; four repositories remain `contact-blocked`. No GitHub, Artifact Hub, or public tracker writes were made.

| Repository | Channel evidence | Result | Local action |
| --- | --- | --- | --- |
| `ibm-charts` | [IBM/charts](https://github.com/IBM/charts) is active and was updated on 2026-07-31. Issues and Discussions are disabled, and although pull requests exist, [IBM's contribution guidance](https://github.com/IBM/charts/blob/master/deprecated/CONTRIBUTING.md) says the `stable` directory cannot be contributed to through GitHub and is handled through IBM's internal build process. | `contact-blocked` | Retain the blocker. Identify an IBM-owned support or maintainer channel that can handle the `repo/stable` metadata and ownership claim. |
| `lifen` | [honestica/lifen-charts](https://github.com/honestica/lifen-charts) is archived. Lifen's [official contact form](https://www.lifen.fr/contact) and [support request form](https://assistance.lifen.fr/hc/fr/requests/new) are writable, but neither provides a public durable project-maintainer thread. | `contact-blocked` | Retain the blocker. A private form may be considered only through a separately approved escalation; do not treat it as public outreach evidence. |
| `owkin` | [owkin/charts](https://github.com/owkin/charts) is archived. Owkin's [official contact form](https://www.owkin.com/contact) is writable, but it is a general/business contact path and does not provide a public durable maintainer thread. | `contact-blocked` | Retain the blocker. Do not infer that a general Owkin contact or current Owkin activity establishes responsibility for the archived chart listing. |
| `ruguodangshi` | [ruguodangshi/charts](https://github.com/ruguodangshi/charts) is an inactive fork of [cloudnativeapp/charts](https://github.com/cloudnativeapp/charts), has Issues and Discussions disabled, and points to the Aliyun Hub homepage, which currently reports that the Hub is being upgraded. The parent repository is not evidence that the fork owner maintains the Artifact Hub listing. | `contact-blocked` | Retain the blocker. No authoritative project-owned channel for the fork or listing was established. |
| `snyk` | Artifact Hub identifies the source as [snyk/kubernetes-monitor](https://github.com/snyk/kubernetes-monitor), an active repository updated on 2026-07-31. Issues and Discussions are disabled, but [pull requests are enabled](https://github.com/snyk/kubernetes-monitor/pulls), with current project activity. [CODEOWNERS](https://github.com/snyk/kubernetes-monitor/blob/staging/.github/CODEOWNERS) names `@snyk/container_container`; recent PR activity includes [#1734](https://github.com/snyk/kubernetes-monitor/pull/1734) and [#1727](https://github.com/snyk/kubernetes-monitor/pull/1727). | `contact-ready` | Use a reviewed pull-request destination, but obtain the current claimant's Artifact Hub account email before preparing the metadata diff. |

The corrected local queue now has `1` contact-ready repository and `4` contact-blocked repositories. Contact-ready means a durable public channel exists for a valid change path; it does not mean outreach has been posted or approved.

### Pull Request Drafts: 2026-07-31

These are approval-ready destinations and message drafts. No pull requests were opened. A pull request must contain an actual repository change; Artifact Hub ownership metadata also requires the claiming maintainer's own Artifact Hub account email. Do not open a no-change PR or invent a claimant identity.

#### `ibm-charts`

- Candidate destination rejected: [IBM/charts pull requests](https://github.com/IBM/charts/pulls), base branch `master`.
- Artifact Hub repository: [helm/ibm-charts](https://artifacthub.io/repositories/helm/ibm-charts), repository ID `5d25cfa5-d7fc-401f-a7d3-2c7645bd2731`.
- Source path requiring metadata: `repo/stable/artifacthub-repo.yml`, alongside the published `repo/stable/index.yaml`.
- Supporting evidence: [IBM/charts README](https://github.com/IBM/charts#readme), [IBM contribution guidance](https://github.com/IBM/charts/blob/master/deprecated/CONTRIBUTING.md), [Artifact Hub repository documentation](https://artifacthub.io/docs/topics/repositories/#ownership-claim).
- Proposed title: `[Artifact Hub] Claim ownership of the ibm-charts repository`
- Proposed body:

```md
### What this does

This PR is intended to help IBM claim the existing Artifact Hub Helm repository:

https://artifacthub.io/repositories/helm/ibm-charts

Artifact Hub currently lists the repository as `helm`-owned. The published source is IBM's `repo/stable` Helm repository:

https://raw.githubusercontent.com/IBM/charts/master/repo/stable/

IBM's contribution guidance states that the `stable` directory cannot be contributed to through GitHub and is handled through IBM's internal build process. Therefore this is not a valid pull-request destination for the Artifact Hub metadata. If IBM still maintains this repository, please identify an IBM-owned support or maintainer channel that can handle the metadata and ownership claim. The repository ID is:

`5d25cfa5-d7fc-401f-a7d3-2c7645bd2731`

After the metadata is merged, please complete the ownership claim from the Artifact Hub control panel and confirm the result here. If IBM no longer maintains the listing, please redirect us to the current owner.

### Notes for the reviewer

No ownership claim has been made by Helm. This request is only to identify the current IBM owner and provide the metadata needed for that owner to claim the listing.
```

- Result: return `ibm-charts` to `contact-blocked`; no valid public PR path for `repo/stable/artifacthub-repo.yml` was established.

#### `snyk`

- Destination: [snyk/kubernetes-monitor pull requests](https://github.com/snyk/kubernetes-monitor/pulls), base branch `staging`.
- Artifact Hub repository: [helm/snyk](https://artifacthub.io/repositories/helm/snyk), repository ID `cd8322aa-ddcf-4c22-9848-281101dc5613`.
- Source path requiring metadata: the repository path published at `https://snyk.github.io/kubernetes-monitor/`; confirm the Pages output path immediately before any write.
- Supporting evidence: [snyk/kubernetes-monitor README](https://github.com/snyk/kubernetes-monitor#readme), [contribution guidance](https://github.com/snyk/kubernetes-monitor/blob/staging/CONTRIBUTING.md), [Artifact Hub repository documentation](https://artifacthub.io/docs/topics/repositories/#ownership-claim).
- Public maintainer evidence: [CODEOWNERS](https://github.com/snyk/kubernetes-monitor/blob/staging/.github/CODEOWNERS) names `@snyk/container_container`; recent durable activity includes [PR #1734](https://github.com/snyk/kubernetes-monitor/pull/1734) and [PR #1727](https://github.com/snyk/kubernetes-monitor/pull/1727) from Snyk contributors.
- Proposed title: `[Artifact Hub] Claim ownership of the Snyk Helm repository`
- Proposed body:

```md
- [ ] Tests written and linted
- [ ] Documentation written
- [ ] Commit history is tidy

### What this does

This PR is intended to help Snyk claim the existing Artifact Hub Helm repository:

https://artifacthub.io/repositories/helm/snyk

Artifact Hub currently lists the repository as `helm`-owned. The validated source is Snyk's Kubernetes Monitor repository and its published Helm repository:

https://github.com/snyk/kubernetes-monitor
https://snyk.github.io/kubernetes-monitor/

If Snyk still maintains this project, please add or amend the `artifacthub-repo.yml` metadata at the published repository path with the Artifact Hub account owner's name and the email address used by that account. The repository ID is:

`cd8322aa-ddcf-4c22-9848-281101dc5613`

After the metadata is merged, please complete the ownership claim from the Artifact Hub control panel and confirm the result here. If Snyk no longer maintains the listing, please redirect us to the current owner.

### Notes for the reviewer

No ownership claim has been made by Helm. This request is only to identify the current Snyk owner and provide the metadata needed for that owner to claim the listing.
```

- Required change before posting: obtain confirmation from the Snyk project team identifying the Artifact Hub claimant and the exact account email, then prepare the root `artifacthub-repo.yml` diff. Public contributor names, CODEOWNERS, or GitHub no-reply addresses are not sufficient substitutes for the Artifact Hub account email.

These drafts are not external writes. Approval, claimant identity, exact metadata diff, and final rendered PR content must be reviewed separately before posting.

### Snyk Support Contact Draft: 2026-07-31

The Snyk contribution guide directs enhancement and support requests to the [Snyk support portal](https://support.snyk.io). This was the appropriate contact because it did not require guessing an Artifact Hub account email or opening a no-change pull request. The approved request was submitted on 2026-07-31 using the user's work email, and Snyk returned an automated receipt without a ticket number or maintainer response.

- Destination: [Snyk support portal](https://support.snyk.io).
- Suggested category: Product/support request concerning Snyk Kubernetes Monitor ownership metadata.
- Proposed subject: `Artifact Hub ownership claim for Snyk Kubernetes Monitor Helm repository`
- Proposed message:

```text
Hello Snyk Support,

I am contacting you about the Snyk Kubernetes Monitor Helm repository currently listed on Artifact Hub:

https://artifacthub.io/repositories/helm/snyk

Artifact Hub repository ID: cd8322aa-ddcf-4c22-9848-281101dc5613

The validated source repository is:

https://github.com/snyk/kubernetes-monitor

The Helm repository is published at:

https://snyk.github.io/kubernetes-monitor/

Helm currently receives notifications for this Artifact Hub listing. Could you please route this request to the current Snyk maintainer or team for the Kubernetes Monitor project and confirm the correct Artifact Hub account to use for the ownership claim?

Artifact Hub requires the claimant to add an artifacthub-repo.yml file at the published repository path with the claimant's own Artifact Hub account identity and sign-in email, then complete the ownership claim from the Artifact Hub control panel.

If Snyk no longer maintains this project or listing, please redirect me to the current owner or advise whether the listing should be removed.

Thanks.
```

- Submission result: the exact message was submitted through the Snyk support portal on 2026-07-31. The automated receipt confirms that Snyk received the request but provides no ticket number, maintainer identity, ownership confirmation, or claim evidence.
- After a human response: record any durable support reference locally, validate the named claimant, prepare the exact `artifacthub-repo.yml` diff, and request separate approval before any GitHub PR or Artifact Hub action.

## Outreach Template Requirements

Every outreach message should include:

- the exact Artifact Hub repository URL and repository name;
- why Helm administrators currently receive its notifications;
- the validated source repository and why the recipient is believed to maintain it;
- Artifact Hub's ownership-claim instructions;
- a request to confirm in the thread after the claim succeeds;
- a request to redirect to a current owner if the contact is no longer responsible.

Before posting, check that no repository name, Artifact Hub query parameter, or maintainer mention was copied from another row.

### Recommended Issue Template

For repos without a mandatory issue template and without an existing response, prefer a Seldon-style issue body:

- `Hello,`
- one short paragraph about Helm being the historical default owner on Artifact Hub;
- the exact Artifact Hub repository URL;
- the validated source repository or repositories;
- the ownership-claim instruction URL;
- a concise request to confirm the claim or redirect to the current owner;
- a brief closing such as `Thanks.`

If the repo already has a response in the thread or enforces a mandatory issue template, keep that repository's required structure instead of this default.

## Completion Criteria

The work is complete when:

- all 136 rows have a validated source or a documented reason no source can be established;
- every source has a lifecycle classification and verification date;
- every active repository has an authoritative maintainer or project-owned contact channel;
- every contact, reply, and claim checkbox is backed by durable evidence;
- every unclaimed active repository has current outreach or a documented escalation;
- every abandoned, duplicate, or dead repository has an administrator-approved terminal disposition; and
- the issue inventory's summary counts are regenerated from the table and match the rows.

## Restart Handoff (Temporary)

This section preserves current working state for a model or session restart. It is not part of the issue inventory or activity overlay. Remove it after the findings have been consumed into permanent row dispositions and the first-pass review is complete.

### Current Position

- Verification date: `2026-07-30`.
- Seven Tier 1 outreach batches plus a four-repository eighth-batch partial are posted (39 repositories total): `newrelic`, `seldon`, `jenkins`, `keel`, `cloudposse`, `kedacore`, `descheduler`, `openfaas`, `sysdiglabs`, `vmware-tanzu`, `falcosecurity`, `prometheus-msteams`, `cryptlex`, `jitterbit`, `inlets`, `gresearch`, `litmuschaos`, `privatebin`, `kuberhealthy`, `ealenn`, `odavid`, `mogaal`, `dniel`, `gkarthiks`, `hmdmph`, `vulcanlink`, `zooz`, `pcktdmp`, `crowdfox`, `http-folder`, `gabibbo97`, `riskfocus`, `liwenhe`, `pndaproject`, `snl-charts`, `fluent`, `appuio`, `crossplane`, and `ory`.
- The outreach is recorded under `## 2026-07-25` in [activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580).
- GitHub did not apply the requested `feature request` label to the New Relic issue, and the posting account lacks permission to add it. The issue body follows New Relic's feature-request template, so no correction is pending.
- Slow-pacing Artifact Hub validation completed without new `HTTP 429` responses during the sixth-batch selection and posting preflight.

| Repository         | Outreach issue                                                                                                   |
| ------------------ | ---------------------------------------------------------------------------------------------------------------- |
| newrelic           | [newrelic/helm-charts#2360](https://github.com/newrelic/helm-charts/issues/2360)                                 |
| seldon             | [SeldonIO/seldon-core#7115](https://github.com/SeldonIO/seldon-core/issues/7115)                                 |
| jenkins            | [jenkinsci/kubernetes-operator#1185](https://github.com/jenkinsci/kubernetes-operator/issues/1185)               |
| keel               | [keel-hq/keel#864](https://github.com/keel-hq/keel/issues/864)                                                   |
| cloudposse         | [cloudposse/charts#282](https://github.com/cloudposse/charts/issues/282)                                         |
| kedacore           | [kedacore/charts#889](https://github.com/kedacore/charts/issues/889)                                             |
| descheduler        | [kubernetes-sigs/descheduler#1903](https://github.com/kubernetes-sigs/descheduler/issues/1903)                   |
| openfaas           | [openfaas/faas-netes#1254](https://github.com/openfaas/faas-netes/issues/1254)                                   |
| sysdiglabs         | [sysdiglabs/charts#2696](https://github.com/sysdiglabs/charts/issues/2696)                                       |
| vmware-tanzu       | [vmware-tanzu/helm-charts#745](https://github.com/vmware-tanzu/helm-charts/issues/745)                           |
| falcosecurity      | [falcosecurity/charts#1048](https://github.com/falcosecurity/charts/issues/1048)                                 |
| prometheus-msteams | [prometheus-msteams/prometheus-msteams#440](https://github.com/prometheus-msteams/prometheus-msteams/issues/440) |
| cryptlex           | [cryptlex/helm-charts#119](https://github.com/cryptlex/helm-charts/issues/119)                                   |
| jitterbit          | [jitterbit/charts#24](https://github.com/jitterbit/charts/issues/24)                                             |
| inlets             | [inlets/inlets-operator#174](https://github.com/inlets/inlets-operator/issues/174)                               |
| gresearch          | [G-Research/charts#140](https://github.com/G-Research/charts/issues/140)                                         |
| litmuschaos        | [litmuschaos/litmus-helm#494](https://github.com/litmuschaos/litmus-helm/issues/494)                             |
| privatebin         | [PrivateBin/helm-chart#136](https://github.com/PrivateBin/helm-chart/issues/136)                                 |
| kuberhealthy       | [kuberhealthy/kuberhealthy#1523](https://github.com/kuberhealthy/kuberhealthy/issues/1523)                       |
| ealenn             | [Ealenn/charts#54](https://github.com/Ealenn/charts/issues/54)                                                   |
| odavid             | [odavid/k8s-helm-charts#29](https://github.com/odavid/k8s-helm-charts/issues/29)                                 |
| mogaal             | [mogaal/helm-charts#25](https://github.com/mogaal/helm-charts/issues/25)                                         |
| dniel              | [dniel/charts#2](https://github.com/dniel/charts/issues/2)                                                       |
| gkarthiks          | [gkarthiks/helm-charts#13](https://github.com/gkarthiks/helm-charts/issues/13)                                   |
| hmdmph             | [hmdmph/helm-charts#18](https://github.com/hmdmph/helm-charts/issues/18)                                         |
| vulcanlink         | [vulcanlink/charts#36](https://github.com/vulcanlink/charts/issues/36)                                           |
| zooz               | [Zooz/helm#15](https://github.com/Zooz/helm/issues/15)                                                           |
| pcktdmp            | [pcktdmp/charts#42](https://github.com/pcktdmp/charts/issues/42)                                                 |
| crowdfox           | [CrowdfoxGmbH/cfcharts#2](https://github.com/CrowdfoxGmbH/cfcharts/issues/2)                                     |
| http-folder        | [AurelienGasser/charts#4](https://github.com/AurelienGasser/charts/issues/4)                                     |
| gabibbo97          | [gabibbo97/charts#54](https://github.com/gabibbo97/charts/issues/54)                                             |
| riskfocus          | [riskfocus/helm-charts-public#39](https://github.com/riskfocus/helm-charts-public/issues/39)                     |
| liwenhe            | [liwenhe1993/charts#14](https://github.com/liwenhe1993/charts/issues/14)                                         |
| pndaproject        | [pndaproject/pnda-helm-chart#10](https://github.com/pndaproject/pnda-helm-chart/issues/10)                       |
| snl-charts         | [snebel29/snl-charts#1](https://github.com/snebel29/snl-charts/issues/1)                                         |

### Validated Repositories

| Repository     | Canonical source                                                 | Confidence                | Lifecycle         | Recommended action                                                                                                                   |
| -------------- | ---------------------------------------------------------------- | ------------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| dacruz21       | <https://github.com/typokign/helm-charts>                          | `confirmed-by-index`      | `dead-endpoint`   | Correct source; retain for Tier 2 outreach about transfer or retirement.                                                             |
| equinor-charts | <https://github.com/equinor/helm-charts>                           | `confirmed-by-repository` | `unknown`         | Correct malformed source; later outreach about claiming or retiring the live but stale listing.                                      |
| eventstore     | <https://github.com/kurrent-io/EventStore.Charts>                  | `confirmed-by-index`      | `retired/renamed` | Correct source; request removal or disabled-listing disposition.                                                                     |
| gradiant       | <https://github.com/Gradiant/bigdata-charts>                       | `confirmed-by-repository` | `retired/renamed` | Correct source; confirm disposition of the stale Helm-owned duplicate of `gradiant-bigdata`.                                         |
| squidex        | <https://github.com/Squidex/squidex-hosting>                       | `confirmed-by-repository` | `dead-endpoint`   | Correct source; request repoint-or-remove disposition.                                                                               |
| talend         | <https://github.com/Talend/helm-charts-public>                     | `confirmed-by-index`      | `retired/renamed` | Correct malformed source; later outreach about ownership or removal of the historical listing.                                       |
| waldur         | <https://github.com/waldur/waldur-helm>                            | `confirmed-by-repository` | `retired/renamed` | Correct source; request disposition of the dead duplicate of the active `waldur-charts` listing.                                     |
| wombat         | <https://github.com/esl/helm-chart/tree/master/charts/wombatChart> | `confirmed-by-repository` | `active`          | Correct malformed source and reconcile as already owned outside Helm; no outreach.                                                   |
| cloudposse     | <https://github.com/cloudposse/charts>                             | `confirmed-by-repository` | `active`          | Reclassify as source-identified; Tier 1 outreach posted.                                                                             |
| newrelic       | <https://github.com/newrelic/helm-charts>                          | `confirmed-by-repository` | `active`          | Reclassify as source-identified; Tier 1 outreach posted.                                                                             |
| seldon         | <https://github.com/SeldonIO/seldon-core>                          | `confirmed-by-index`      | `active`          | Reclassify as source-identified; record `SeldonIO/helm-charts` as related current publishing infrastructure; Tier 1 outreach posted. |
| simplyzee      | <https://github.com/simplyzee/simplyzee-charts>                    | `confirmed-by-repository` | `unknown`         | Replace the incorrect source candidate; retain the dormant listing for Tier 2 outreach.                                              |
| ibm-charts     | <https://github.com/IBM/charts>                                    | `confirmed-by-index`      | `unknown`         | Reclassify as source-identified; retain for Tier 2 outreach about the legacy feed.                                                   |
| jenkins        | <https://github.com/jenkinsci/kubernetes-operator>                 | `confirmed-by-repository` | `active`          | Reclassify as source-identified; Tier 1 outreach posted.                                                                             |
| keel           | <https://github.com/keel-hq/keel>                                  | `confirmed-by-index`      | `active`          | Reclassify as source-identified; Tier 1 outreach posted.                                                                             |
| smueller18     | <https://gitlab.com/smueller18/helm-charts>                        | `confirmed-by-repository` | `retired/renamed` | Reclassify as archived and superseded by the verified `andibraeu` listing; request removal or disabled-listing disposition.          |

### Work Queues

- **Outreach posted, awaiting response/claim:** `newrelic`, `seldon`, `jenkins`, `keel`, `cloudposse`, `kedacore`, `descheduler`, `openfaas`, `vmware-tanzu`, `falcosecurity`, `prometheus-msteams`, `cryptlex`, `jitterbit`, `inlets`, `gresearch`, `litmuschaos`, `privatebin`, `kuberhealthy`, `ealenn`, `odavid`, `mogaal`, `dniel`, `gkarthiks`, `vulcanlink`, `zooz`, `pcktdmp`, `crowdfox`, `http-folder`, `gabibbo97`, `riskfocus`, `liwenhe`, `pndaproject`, `snl-charts`, `fluent`, `appuio`, `crossplane`, `ory`, `agones`, `influxdata`, `jfrog`, `kanister`, `rancher-stable`, `simplyzee`, `equinor-charts`, `dhiatn`, `lohmag`, and `mtls`. `hmdmph` and `sysdiglabs` moved to the claimed queue.
- **Eighth-batch partial posted:** `fluent`, `appuio`, `crossplane`, and `ory`; all passed the final preflight and received ownership requests. `snyk` was contacted through Snyk's support portal and is awaiting a human response; no claim or PR action is authorized.
- **Existing external outreach:** `runix` has an ownership-transfer request from `@SetagGnaw` at [rowanruseler/helm-charts#351](https://github.com/rowanruseler/helm-charts/issues/351). Treat it as durable contact evidence and do not open duplicate outreach, but keep `runix` in source research until provenance is independently verified.
- **Next Tier 1 batch prepared:** `agones`, `influxdata`, `jfrog`, `kanister`, and `rancher-stable`; all passed the replacement preflight and await exact-message approval.
- **Dormant candidates not selected for the next batch:** `gabibbo97`, `riskfocus`, `liwenhe`, `pndaproject`, and `snl-charts`; all were already contacted and their source repositories have not been updated since 2020 or 2021.
- **Tier 2 provisional queue:** `simplyzee`, `equinor-charts`, `dhiatn`, `lohmag`, `mtls`, `qamatic`, and `rasooll`; all seven candidates have now received ownership requests and Tier 2 is complete.
- **Tier 2 preflight exclusions:** `dacruz21` routes to `lifecycle-research`/`disposition`, `stardog` routes to disposition-first outreach because its source is archived, and `ibm-charts` routes to `contact-blocked` because IBM has disabled Issues and Discussions.
- **Disposition-oriented:** `eventstore`, `gradiant`, `squidex`, `talend`, `waldur`, and `smueller18`.
- **Later source-confirmed outreach:** `equinor-charts`, after accounting for its stale lifecycle.
- **No outreach needed:** `wombat`; reconcile its existing ownership and corrected source.
- **Deferred:** `crate`, as documented below; allow internal discussion until the first-pass review is complete.
- **Claimed and reconciled:** `couchbase`; ownership now belongs to the official `couchbase` organization.

### Completion and Disposition Tracking

- **Already claimed / ownership moved from Helm (evidence-backed):** `camel-k`, `ceph-csi`, `concourse`, `cowboysysop`, `couchbase`, `hmdmph`, and `sysdiglabs`.
- **No transfer action expected:** `wombat` (already owned outside Helm after source reconciliation).
- **Disposition queue after initial outreach completes:** `eventstore`, `gradiant`, `squidex`, `talend`, `waldur`, `smueller18`, and `crate`.

### Next Step

The population census, replacement Tier 1 selection, and all Tier 2 outreach are complete. Keep Tier 1, Tier 2, disposition, and contact-blocked batches separate. Continue to use one activity-comment heading per actual action date, and request separate approval for all activity and audit writes.

### Prepared Next Batch

Freshly validated candidates for the next outreach batch:

| Repository  | Preflight status            | Notes                                                                                                     |
| ----------- | --------------------------- | --------------------------------------------------------------------------------------------------------- |
| fluent      | posted | [fluent/helm-charts#742](https://github.com/fluent/helm-charts/issues/742) |
| snyk        | contacted/awaiting response | Support request submitted; automated receipt received, but no ticket number or maintainer response was provided. |
| appuio      | posted | [appuio/charts#559](https://github.com/appuio/charts/issues/559) |
| crossplane  | posted | [crossplane/crossplane#7659](https://github.com/crossplane/crossplane/issues/7659); unrelated Artifact Hub discussions were kept separate. |
| ory         | posted | [ory/k8s#892](https://github.com/ory/k8s/issues/892) |

Prepared outreach draft template for the next batch:

```md
Hello,

I am reaching out about the Artifact Hub repository for <repo-name>:
<artifact-hub-url>

Helm currently receives notifications for this listing. The validated source repository appears to be <canonical-source>, and I believe your team is the current maintainer/owner based on <evidence-summary>.

If you still own this project, please follow Artifact Hub's ownership-claim instructions and confirm back in this thread after the claim succeeds.
If you are no longer responsible for this repository, please redirect me to the current owner or team contact.
```

Prepared audit-log entry for the batch after approval and outreach:

```md
| 2026-07-30 | Eighth-batch outreach partial      | Revalidated the five selected candidates and opened ownership-transfer requests for four repositories. | Requests: [fluent](https://github.com/fluent/helm-charts/issues/742), [appuio](https://github.com/appuio/charts/issues/559), [crossplane](https://github.com/crossplane/crossplane/issues/7659), and [ory](https://github.com/ory/k8s/issues/892). `snyk` was deferred because GitHub Issues and Discussions are disabled. |
```

### API Rate-Limit Handling

- Start read-only Artifact Hub API calls at approximately one request per 3 seconds during bulk validation.
- If any `HTTP 429` appears, immediately slow to one request every four to five seconds for the rest of that run.
- Run validation in small batches of five to ten repositories, then pause 15 to 30 seconds before continuing.
- If `HTTP 429` persists after slowing down, back off for 60 to 120 seconds, then resume at the slower four-to-five-second pace.
- Keep a short run log of rate-limit events and the active pacing so follow-up sessions reuse the safer cadence.
- Immediately before any outreach write, recheck ownership and duplicate-request status for the exact repositories in that batch.

## Deferred Follow-ups

### Crate

- **Status as of 2026-07-24:** A current Crate organization member asked historical contributor `OJFord` whether they would take responsibility for the repository. `OJFord` declined because they no longer use CrateDB or Helm and could not provide meaningful support.
- **Current listing:** The `crate` Artifact Hub repository remains enabled and owned by `helm`.
- **Lifecycle:** The canonical repository remains unarchived, but its newest chart is `0.2.0` from 2022 and no current chart maintainer is identified.
- **Decision:** Allow time for internal Crate discussion. Do not post another response or infer that the historical contributor should claim ownership.
- **Evidence:** [Crate discussion](https://github.com/crate/helm-charts/issues/10#issuecomment-5067819593) and [contributor response](https://github.com/crate/helm-charts/issues/10#issuecomment-5068805504).
- [ ] Revisit after the first-pass review of all remaining repositories. Recheck the thread, Artifact Hub ownership, repository activity, and current maintainer evidence before deciding whether to request a transfer or terminal disposition.

## Ongoing Maintenance

Until the transfer project is complete, recheck contact threads monthly and source health quarterly. As part of each monthly review, prepare exact rows for the applicable dated activity section and request approval before appending them. Use one heading per date, one consolidated table for all same-day repository changes, and one optional addendum after the table for explanatory notes or blockers. Mention `@scottrigby` no more than once in that addendum. A lightweight audit should flag redirects, 404 responses, archived repositories, dead Helm indexes, removed maintainers, and new comments on contact threads. Issue maintainers can apply the activity entries to the original inventory; use scripts or working files only to generate and validate the data, subject to the same write-approval gate.

### Source-Research Census Reconciliation: 2026-07-31

The source-research queue was reconciled against the current 136-row public inventory using a read-only fetch of issue #428. The queue count was recorded as `40`, but the enumerated list contained `39` repositories. `vertigo` was present in the public inventory with the Helm URL `https://charts.vertigo.com.br/` but was absent from the local source-research list. It is now recorded as the 40th source-research row.

The source-research pass must remain read-only and proceed in batches of 5 to 10 repositories. For each row, capture the current Artifact Hub listing and Helm URL, inspect the live chart index and metadata, normalize redirects, verify that the candidate source publishes the tracked listing, classify lifecycle, identify authoritative project-owned contactability, and assign source confidence. Do not contact projects during this pass. Record evidence and a recommended queue locally, then request approval before changing the public inventory or posting outreach.

No GitHub, Artifact Hub, or other external writes were made during this reconciliation.

The subsequent discovery of [rowanruseler/helm-charts#351](https://github.com/rowanruseler/helm-charts/issues/351) provides durable contact evidence for `runix`, but does not complete the independent provenance check. Keep `runix` in this queue and avoid duplicate outreach while validating it.

### Source-Research Batch 1: 2026-07-31

This read-only batch covered `astarte`, `balle-petersen`, `banzaicloud-stable`, `brannon`, `camptocamp`, `choerodon`, `cleardata`, `cronce`, `datawire`, and `dgraph`. No GitHub, Artifact Hub, repository, or contact-channel writes were made.

| Repository | Feed evidence | Source and lifecycle evidence | Contactability | Provisional outcome |
| --- | --- | --- | --- | --- |
| `astarte` | [Live index](https://helm.astarte-platform.org/index.yaml); latest `astarte-operator` entry `26.7.0-rc.2` created 2026-07-31. | Index names [astarte-platform/astarte-kubernetes-operator](https://github.com/astarte-platform/astarte-kubernetes-operator), with release packages from [astarte-platform/helm](https://github.com/astarte-platform/helm). Both repositories are active and unarchived. | Organization-owned GitHub issues and pull requests are enabled; index lists current Secomind maintainers. | `confirmed-by-index`, `active`; source-confirmed candidate for later outreach. |
| `balle-petersen` | Root feed URL returns 404, but [index.yaml](https://charts.balle-petersen.org/index.yaml) is reachable; latest entries were created 2020-07-31. | Index identifies [tobiasbp/helm-charts](https://github.com/tobiasbp/helm-charts), unarchived but dormant since 2020-07-31. | Repository issues and pull requests are enabled; maintainer is Tobias Balle-Petersen. | `confirmed-by-index`, `dormant`; retain for lifecycle/disposition review before outreach. |
| `banzaicloud-stable` | Registered feed endpoint did not return a usable index during this pass. | [banzaicloud/banzai-charts](https://github.com/banzaicloud/banzai-charts) is an unarchived repository last pushed 2023-11-20 and contains many historical chart directories, but the registered feed-to-source relationship was not independently verified. | Banzai Cloud organization contact is public, but current chart ownership is not established. | `strong-candidate`, lifecycle/source unresolved; continue read-only reconciliation. |
| `brannon` | [Live index](https://helm.brannon.online/index.yaml); generated 2020-12-05 and latest chart entries were created 2020-12-05. | Index identifies [brannondorsey/helm-charts](https://github.com/brannondorsey/helm-charts), unarchived but dormant since 2020-12-05. | Repository issues and pull requests are enabled; feed identifies Brannon Dorsey as maintainer. | `confirmed-by-index`, `dormant`; retain for lifecycle review before outreach. |
| `camptocamp` | Registered feed endpoint did not return a usable index. | [camptocamp/charts](https://github.com/camptocamp/charts) is active and unarchived, but contains many unrelated chart directories; no exact relationship to the registered feed was verified. | Organization-owned GitHub contact exists, but the correct chart owner is unresolved. | `unverified`; continue provenance and feed-path research; no outreach. |
| `choerodon` | [Live index](https://openchart.choerodon.com.cn/choerodon/c7n/index.yaml); latest entries were created 2022-07-29. | No exact publishing repository was established. The Choerodon organization has many archived repositories and the visible service repositories are dormant or archived. | Organization exists, but no current chart-maintainer channel was established. | `unverified`, likely dormant/retired; continue lifecycle and source research. |
| `cleardata` | Registered feed endpoint did not return a usable index. | The [cleardata GitHub account](https://github.com/cleardata) has no public repositories; no canonical publishing source was established. | Inventory lists a support address, but no durable source-owned chart contact was verified. | `unverified`, possible dead endpoint; continue source and lifecycle research without outreach. |
| `cronce` | [Live index](https://charts.cronce.io/index.yaml) contains multiple charts; newest observed entries include 2025 and 2024 releases. | Index has mixed provenance: some charts identify public sources, while others use the private `gitlab.cronce.io` publishing path or omit `sources`. The tracked Artifact Hub chart identity was not isolated from the multi-chart feed. | Feed lists `mike@cronce.io`; this is a personal contact, not yet sufficient to establish the tracked listing's current ownership. | `strong-candidate` for feed existence only; tracked-chart provenance remains unresolved. |
| `datawire` | [Live index](https://getambassador.io/index.yaml); latest `ambassador` entry `6.9.5` created 2026-07-31. | Index names [datawire/ambassador](https://github.com/datawire/ambassador), which resolves to the active [emissary-ingress/emissary](https://github.com/emissary-ingress/emissary) successor. The feed is active, but the canonical source and Artifact Hub identity need exact reconciliation. | Successor repository has active issues, pull requests, and discussions; index also lists historical Datawire maintainers. | `confirmed-by-index`, active successor; correct canonical source before considering outreach. |
| `dgraph` | [Live index](https://charts.dgraph.io/index.yaml); latest Dgraph chart entry `25.0.0-preview6` created 2025-09-16. | Index identifies [dgraph-io/charts](https://github.com/dgraph-io/charts), active and unarchived, plus Dgraph/Hypermode sources. The chart repository was pushed 2026-07-21 and the Dgraph source repository 2026-07-31. | Organization-owned issues and pull requests are enabled; index lists `hello@hypermode.com` and `contact@dgraph.io` in different releases. | `confirmed-by-index`, `active`; source-confirmed candidate for later outreach after claimant/contact normalization. |

Batch 1 does not authorize outreach. The confirmed active candidates should be held until the batch is complete and the canonical source, Artifact Hub identity, and current project-owned contact are reconciled.

### Source-Research Batch 2: 2026-07-31

This read-only batch covered `dragonchain`, `fermosit`, `fold`, `forseti-security`, `franzinc`, `fyipe`, `gomods`, `gp42`, `hue`, and `inspur`. No GitHub, Artifact Hub, repository, or contact-channel writes were made.

| Repository | Feed evidence | Source and lifecycle evidence | Contactability | Provisional outcome |
| --- | --- | --- | --- | --- |
| `dragonchain` | Registered S3 endpoint returns 404 for `index.yaml`. | The Dragonchain organization has active-but-dormant repositories, including [dragonchain/dragonchain](https://github.com/dragonchain/dragonchain), last pushed 2023-05-22. No Helm publishing repository was found. | Organization GitHub contact exists, but no chart-owned channel was established. | `unverified`, likely dead historical feed; continue source/lifecycle research before disposition. |
| `fermosit` | [Live Harbor index](https://harbor.fermosit.es/chartrepo/library/index.yaml) is a multi-chart feed generated through 2023-11-16. | The feed contains unrelated charts from several personal and project sources and does not identify a canonical source for the tracked `fermosit` listing. | The inventory contact is personal; no source-owned contact for the tracked listing was established. | `unverified`; multi-tenant feed requires chart-identity reconciliation. |
| `fold` | [Live index](https://charts.foldapp.com/index.yaml); latest observed `lnd` entry created 2023-09-27. | Index points to [fold-team/helm-charts](https://github.com/fold-team/helm-charts), unarchived and last pushed 2025-09-02. The feed also contains historical `thesis` and Kubernetes chart references. | Organization-owned repository issues and pull requests are enabled. | `confirmed-by-index`, stale feed with active source; reconcile the exact Artifact Hub chart before outreach. |
| `forseti-security` | Registered Google Storage endpoint returns 403. | [forseti-security/helm-charts](https://github.com/forseti-security/helm-charts) is archived and was last pushed 2021-08-13; the wider Forseti organization is archived. | No current project-owned writable channel was established. | `confirmed-by-repository`, `archived`; route to disposition research, not ownership outreach. |
| `franzinc` | [Live index](https://franz.com/ftp/pub/helm/charts/index.yaml); latest entry created 2020-04-29. | Index identifies `franzinc/agraph-examples`, an unarchived repository updated 2026-04-30, with the Helm chart path under `clustering/kubernetes/mmr`. | Organization-owned issues and pull requests are enabled; index lists `support@franz.com`. | `confirmed-by-index`, active source with stale feed; source-confirmed candidate for later outreach. |
| `fyipe` | The registered domain now redirects to a HugeDomains sale page; the chart endpoint is not available. | No current chart source was established. | No current project-owned chart channel was found. | `dead-endpoint`; route to disposition research and do not contact. |
| `gomods` | Registered Azure Blob feed did not return a usable index. | [gomods/athens](https://github.com/gomods/athens) is active and unarchived, last pushed 2026-07-25, but the relationship between the registered chart feed and Athens was not independently verified. | Organization-owned issues, pull requests, and discussions are enabled. | `strong-candidate`; continue feed/source reconciliation before any outreach. |
| `gp42` | [Live index](https://ops42.org/helm-charts/index.yaml); only observed chart entry was created 2019-12-11. | The index contains an unofficial `calico-aws` chart and does not name a publishing source repository. The maintainer is the personal `gp42` account. | Personal GitHub account and listed email are available, but current ownership is unverified. | `unverified`, dormant; continue provenance research and avoid contact until source identity is established. |
| `hue` | [Live index](https://helm.gethue.com/index.yaml); latest chart `1.0.3` created 2023-01-19. | Index identifies [cloudera/hue](https://github.com/cloudera/hue), active and unarchived with pushes on 2026-07-31; the feed also names `gethue` Docker publishing. | Organization-owned issues, pull requests, and discussions are enabled. | `confirmed-by-index`, active source with stale chart feed; source-confirmed candidate for later outreach. |
| `inspur` | Registered GitHub Pages endpoint returns 404. | The listed [inspur-iop/charts](https://github.com/inspur-iop/charts) repository does not exist; the `inspur-iop` organization has no current charts repository and its visible repositories are dormant. | No current chart-owned contact channel was established. | `dead-endpoint`, source candidate invalid; route to disposition/source reconciliation, not outreach. |

Batch 2 does not authorize outreach. `franzinc` and `hue` remain read-only source-confirmed candidates; `forseti-security` and `fyipe` should receive disposition handling after the broader source-research pass unless new evidence changes their status.

### Source-Research Batch 3: 2026-07-31

This read-only batch covered `k8s-land`, `kiwigrid`, `kremers`, `larribas`, `microsoft`, `mirusresearch`, `opsdroid`, `pl-helm-charts`, `pomerium`, and `purestorage`. No GitHub, Artifact Hub, repository, or contact-channel writes were made.

| Repository | Feed evidence | Source and lifecycle evidence | Contactability | Provisional outcome |
| --- | --- | --- | --- | --- |
| `k8s-land` | Registered feed endpoint returns 404. | [k8s-land/charts](https://github.com/k8s-land/charts) exists and is unarchived but was last pushed 2020-05-15; its relationship to the registered feed was not verified. | No current source-owned channel was established. | `strong-candidate`, stale/dead feed; continue source and lifecycle reconciliation. |
| `kiwigrid` | No live feed was established from the registered source during this pass. | The listed source is not a repository, while [kiwigrid/charts](https://github.com/kiwigrid/charts) is archived and was last pushed 2020-08-27. | Kiwigrid has current public repositories, but no maintainer channel for this historical chart feed was verified. | `confirmed-by-repository` for the historical chart candidate, `archived`; route toward disposition after feed confirmation. |
| `kremers` | No live feed was established from the registered source during this pass. | The listed [kremers/kremers](https://github.com/kremers/kremers) source does not exist; [kremers/charts](https://github.com/kremers/charts) is an unarchived candidate last pushed 2021-05-18, but the Artifact Hub feed relationship is unverified. | Personal repository owner and email are listed, but current chart ownership is not established. | `strong-candidate`, dormant/uncertain; continue provenance research without outreach. |
| `larribas` | Registered feed endpoint did not return a usable index. | [larribas/helm-charts](https://github.com/larribas/helm-charts) exists and is unarchived but was last pushed 2022-01-05; no feed-to-chart mapping was verified. | Personal GitHub account exists; no current chart-maintainer evidence was established. | `strong-candidate`, stale feed; continue source and lifecycle research. |
| `microsoft` | The inventory points to the deleted `microsoft/chartsrepo` source; no live feed evidence was established. | [microsoft/charts](https://github.com/microsoft/charts) is an unarchived repository last pushed 2025-08-21, but it has not been established as the successor for the historical feed. | Microsoft has active organization channels, but the historical chart owner is unresolved. | `strong-candidate` successor only; require exact provenance before reclassification or outreach. |
| `mirusresearch` | No live feed was established from the registered source during this pass. | The listed [mirusresearch/charts](https://github.com/mirusresearch/charts) source does not exist. The organization has a separate [powerdns-helmchart](https://github.com/mirusresearch/powerdns-helmchart) repository last pushed 2022-12-20, but its relationship to the listing is unverified. | Organization-owned repositories exist, but no chart-specific current contact was established. | `unverified`, stale/dead source candidate; continue provenance research. |
| `opsdroid` | Registered feed endpoint did not return a usable index. | [opsdroid/opsdroid](https://github.com/opsdroid/opsdroid) is active and unarchived, last pushed 2026-05-05, but the chart publishing path was not independently verified. | Repository issues are enabled; current project contactability is plausible. | `strong-candidate`, active source candidate; verify chart path before outreach. |
| `pl-helm-charts` | No live feed or source repository was established. | The listed [pranay-lonkar/helm-charts](https://github.com/pranay-lonkar/helm-charts) repository and user account are unavailable. | No current project-owned channel was found. | `dead-endpoint`, source candidate invalid; route to disposition research. |
| `pomerium` | [Live index](https://helm.pomerium.io/index.yaml); latest entry `34.0.1` created 2023-05-30. | Index identifies [pomerium/pomerium](https://github.com/pomerium/pomerium), active and unarchived, with packages released through [pomerium/pomerium-helm](https://github.com/pomerium/pomerium-helm), last pushed 2023-10-05. | Organization-owned issues and pull requests are enabled; index lists `bdd@pomerium.io`. | `confirmed-by-index`, active source with stale chart feed; source-confirmed candidate for later outreach. |
| `purestorage` | No live feed was established from the registered source during this pass. | The listed [purestorage/helm-charts](https://github.com/purestorage/helm-charts) repository does not exist; no replacement chart repository was identified. | Pure Storage has an organization presence, but no chart-specific channel was verified. | `unverified`, likely dead historical source; continue source/lifecycle research before disposition. |

Batch 3 does not authorize outreach. `pomerium` remains the only source-confirmed active candidate in this batch; all other rows require further provenance or lifecycle reconciliation.

### Source-Research Batch 4: 2026-07-31

This read-only batch covered the final 10 source-research rows: `redsky`, `runix`, `softonic`, `soluto`, `sstarcher`, `t3n`, `trickster`, `uswitch`, `ververica`, and `vertigo`. No GitHub, Artifact Hub, repository, or contact-channel writes were made.

| Repository | Feed evidence | Source and lifecycle evidence | Contactability | Provisional outcome |
| --- | --- | --- | --- | --- |
| `redsky` | Registered `redskyops.dev/charts/` endpoint now redirects to StormForge documentation; no chart index was found. | No current `redskyops` chart repository was found. The historical provider identity appears to have been replaced or rebranded; this is not enough to map the listing to a current source. | No current chart-owned channel was established. | `dead-or-rebranded-source`; route to disposition/source reconciliation, not outreach. |
| `runix` | [Live index](https://helm.runix.net/index.yaml); latest `pgadmin4` entry `1.65.0` created 2026-06-23. | Index identifies [rowanruseler/helm-charts](https://github.com/rowanruseler/helm-charts), which is active and publishes the chart through GitHub releases. | Existing ownership-transfer request [rowanruseler/helm-charts#351](https://github.com/rowanruseler/helm-charts/issues/351) is durable contact evidence; no duplicate outreach. | `confirmed-by-index`, active source; retain the existing request and later verify claim outcome. |
| `softonic` | [Live index](https://charts.softonic.io/index.yaml) contains `crossplane-softonic-factory` `1.34.0`, created 2026-07-27. | The latest entry omits a source repository and maintainer, although other entries identify `softonic/*` source repositories and `@softonic.com` maintainers. Exact provenance for the tracked listing remains unresolved. | Organization-owned source/contact evidence exists for related charts, not yet for the tracked listing. | `strong-candidate`, active feed with chart-identity reconciliation required. |
| `soluto` | Registered `charts.soluto.io/index.yaml` endpoint failed; no current feed was available. | [Soluto/helm-charts](https://github.com/Soluto/helm-charts) is archived as of 2026-03-25; its README identifies the historical Kamus chart and the old feed. | Archived repository is read-only; no current writable chart channel was established. | `confirmed-by-repository`, archived; route to disposition, not ownership outreach. |
| `sstarcher` | [Live index](https://shanestarcher.com/helm-charts/index.yaml) generated 2025-11-27; latest `helm-exporter` `1.3.0`. | Index identifies [sstarcher/helm-exporter](https://github.com/sstarcher/helm-exporter) and related source repositories; maintainer metadata names Shane Starcher. | Maintainer email `shane.starcher@gmail.com` and project-owned source evidence are present. | `confirmed-by-index`, active source with stale feed; candidate for later outreach after final preflight. |
| `t3n` | [Live Google Storage index](https://storage.googleapis.com/t3n-helm-charts/index.yaml) generated 2025-02-24; latest notable chart entry is `web` `2.1.0` created 2024-07-09. | Index identifies [t3n/helm-charts](https://github.com/t3n/helm-charts) for some charts and lists Max Schmidt; no newer publishing evidence was found in this pass. | Maintainer email `max.schmidt@t3n.de` is listed, but chart activity is stale. | `confirmed-by-index`, dormant/stale source; review lifecycle before outreach. |
| `trickster` | Registered `helm.tricksterproxy.io/index.yaml` and `charts.tricksterproxy.io/index.yaml` endpoints return 404. | [trickstercache/helm-charts](https://github.com/trickstercache/helm-charts) is active and was updated 2025-06-02; README documents the migration to OCI charts at `ghcr.io/trickstercache/charts/trickster`. | Maintainers are listed in the active repository; the historical feed itself has no current contact channel. | `confirmed-by-repository`, active source with feed-to-OCI migration; reconcile the Artifact Hub source before outreach. |
| `uswitch` | Registered URL is malformed (`https://github.com/uswitch/kiam-helm-chartscharts/`) and returns 404; no live feed was found. | No current `uswitch` Kiam chart repository was found through repository search. | No current project-owned chart channel was established. | `dead-endpoint`, source candidate unresolved; route to disposition/source reconciliation. |
| `ververica` | [Live index](https://charts.ververica.com/index.yaml) generated 2026-07-29; latest `ververica-platform` `5.11.11`, app version `2.15.11`. | Feed is actively published at `charts.ververica.com`; project home is [ververica.com](https://www.ververica.com/). No public source repository is listed. | Maintainer metadata names Ververica Support at `platform@ververica.com`. | `confirmed-by-index`, active source; candidate for later outreach after Artifact Hub identity normalization. |
| `vertigo` | Registered `charts.vertigo.com.br/index.yaml` endpoint failed. | [vertigobr/charts](https://github.com/vertigobr/charts) is unarchived but last updated 2023-05-22; its `index.yaml` is empty and README describes only a historical Boundary chart. | No current chart-owned contact channel was established. | `confirmed-by-repository`, stale/empty source; review for disposition before outreach. |

Batch 4 does not authorize outreach. `runix`, `sstarcher`, and `ververica` are source-confirmed active candidates; `trickster` has an active source with an OCI migration; `softonic` requires exact chart-source reconciliation; and the remaining rows are stale, archived, dead, or rebranded candidates.

### Source-Research Consolidation: 2026-07-31

All 40 source-research rows now have read-only evidence records. The table below is a completed provisional consolidation; it does not itself change the public inventory or authorize outreach.

| Provisional outcome | Rows | Handling |
| --- | --- | --- |
| Source-confirmed active | `astarte`, `dgraph`, `franzinc`, `hue`, `pomerium`, `runix`, `sstarcher`, `trickster`, `ververica` | Normalize the exact Artifact Hub identity and duplicate-request state before any new outreach; retain the existing `runix` request. |
| Active source or successor candidate requiring reconciliation | `datawire`, `gomods`, `microsoft`, `opsdroid`, `softonic` | Verify exact chart path, feed identity, and canonical source before reclassification or outreach. |
| Source-confirmed dormant or stale | `balle-petersen`, `brannon`, `fold`, `t3n`, `vertigo` | Review lifecycle and disposition evidence before considering contact. |
| Archived, dead-endpoint, rebranded, or invalid-source candidate | `forseti-security`, `fyipe`, `inspur`, `kiwigrid`, `pl-helm-charts`, `redsky`, `soluto`, `uswitch` | Route toward disposition/source reconciliation; do not open normal ownership outreach. |
| Provenance or lifecycle unresolved | `banzaicloud-stable`, `camptocamp`, `choerodon`, `cleardata`, `cronce`, `dragonchain`, `fermosit`, `gp42`, `k8s-land`, `kremers`, `larribas`, `mirusresearch`, `purestorage` | Retain in research/disposition review until the exact source identity is established. |

### Source-Research Queue Reclassification: 2026-07-31

The 40 source-research rows are now assigned to the existing local reason queues using the completed read-only evidence. This is a local queue change only; it does not change the public inventory, activity overlay, or outreach state.

| Queue | Rows | Handling |
| --- | --- | --- |
| Contact-ready, pending final preflight | `astarte`, `dgraph`, `franzinc`, `hue`, `pomerium`, `sstarcher`, `trickster`, `ververica` | Source, lifecycle, and project-owned contact are sufficiently established for a final Artifact Hub identity and duplicate-request check. Do not contact until that check is complete and approval is obtained. |
| Contacted/awaiting outcome | `runix` | The source and feed are confirmed, and [rowanruseler/helm-charts#351](https://github.com/rowanruseler/helm-charts/issues/351) is an existing durable ownership request. Do not open duplicate outreach; monitor for a claim or response. |
| Source research | `banzaicloud-stable`, `camptocamp`, `choerodon`, `cleardata`, `cronce`, `datawire`, `dragonchain`, `fermosit`, `gomods`, `gp42`, `k8s-land`, `kremers`, `larribas`, `microsoft`, `mirusresearch`, `opsdroid`, `purestorage`, `softonic` | Keep unresolved or successor/multi-chart candidates in read-only research until the exact chart path, Artifact Hub identity, and canonical source are reconciled. |
| Disposition | `balle-petersen`, `brannon`, `fold`, `forseti-security`, `fyipe`, `inspur`, `kiwigrid`, `pl-helm-charts`, `redsky`, `soluto`, `t3n`, `uswitch`, `vertigo` | Route dormant, archived, dead, rebranded, invalid, or empty-feed listings to disposition review rather than normal ownership outreach. |

The contact-ready queue contains eight rows, and the source-research queue contains 18 rows. `softonic` remains in source research because the tracked chart's exact source is not established; `pomerium` is contact-ready because its feed-to-source relationship is confirmed and only the final preflight remains.

The resulting local partition before final preflight was `68` contacted/awaiting/claimed, `37` disposition, `18` source research, `8` contact-ready, `4` contact-blocked, and `1` no-outreach-needed, totaling `136`. The final preflight below supersedes that provisional partition.

### Contact-Ready Preflight: 2026-07-31

The final read-only preflight checked the current Artifact Hub package/repository identity, source or contact path, and duplicate ownership-request evidence for all eight candidates. No external writes were made.

| Repository | Artifact Hub evidence | Source/contact preflight | Duplicate-request check | Result |
| --- | --- | --- | --- | --- |
| `astarte` | `astarte-operator` `26.7.0-rc.2`; repository ID `35d6598b-7c7e-48a2-bb67-e83892385a43`; owner `helm`. | Feed and source remain active; project-owned GitHub issues are available on `astarte-platform/astarte-kubernetes-operator`. | No Artifact Hub ownership request found in the source repository. | Remain contact-ready. |
| `dgraph` | `dgraph` `25.0.0-preview6`; repository ID `3c686646-15cc-4585-8ada-d90ca644d3a3`; owner `helm`. | Feed identifies `dgraph-io/charts`; organization-owned issues are available. | Existing issue [#36](https://github.com/dgraph-io/charts/issues/36) is an unrelated historical release discussion, not an ownership request. | Remain contact-ready. |
| `franzinc` | `agraphmmr` `7.0.0`; repository ID `992a7a66-746f-4fc6-bb08-705be441aa3b`; owner `helm`. | Feed identifies `franzinc/agraph-examples`; organization-owned issues are available and the feed lists `support@franz.com`. | No Artifact Hub ownership request found in the source repository. | Remain contact-ready. |
| `hue` | `hue` `1.0.3`; repository ID `5b6ab329-73d6-44e4-8bda-0b45ef477ebd`; owner `helm`. | Feed identifies `cloudera/hue`; organization-owned issues are available. | Existing issue [#3583](https://github.com/cloudera/hue/issues/3583) is an unrelated application bug, not an ownership request. | Remain contact-ready. |
| `pomerium` | `pomerium` `34.0.1`; repository ID `ae611f10-efda-48d7-ad03-3ed960f591cd`; owner `helm`. | Feed identifies `pomerium/pomerium`; organization-owned issues are available and the feed lists `bdd@pomerium.io`. | No Artifact Hub ownership request found in the source repository. | Remain contact-ready. |
| `sstarcher` | `helm-exporter` `1.3.0+109c2ba`; repository ID `edde934e-2891-4d88-a6bf-9aa40025f866`; owner `helm`. | Feed identifies `sstarcher/helm-exporter`; repository is active and has an issue channel. | Search results containing `artifacthub.io` are unrelated product/configuration discussions; no ownership request found. | Remain contact-ready. |
| `trickster` | Helm-owned `trickster` `1.5.4`; repository ID `cffc2b94-ed2e-4f72-bc0d-99a0bfaa17ca`; owner `helm`. A separate `trickster` listing is AppsCode-owned and verified, with version `2026.1.15`. | The historical Trickster feed is dead; `trickstercache/helm-charts` documents migration to OCI. | No duplicate request found, but the separate verified AppsCode listing creates an ownership/source ambiguity. | Return to source research for Artifact Hub reconciliation; do not contact. |
| `ververica` | `ververica-platform` `5.11.11`; repository ID `1b372f65-8f35-4944-bfca-6921a1c31c64`; owner `helm`. | Feed is active and lists the project-owned support contact `platform@ververica.com`; no public source repository is listed. | No project-owned GitHub ownership request found. | Remain contact-ready for an approved support/email request. |

The preflight reduced the contact-ready queue to seven rows and returned `trickster` to source research. Subsequent approved outreach moved five rows to contacted/awaiting, and the two manual contacts below moved the final two rows as well. The current local partition is `75` contacted/awaiting/claimed, `37` disposition, `19` source research, `0` contact-ready, `4` contact-blocked, and `1` no-outreach-needed, totaling `136`.

### Contact-Ready Outreach: 2026-07-31

The approved ownership requests were posted for five of the seven preflighted candidates:

| Repository | Request |
| --- | --- |
| `astarte` | [astarte-platform/astarte-kubernetes-operator#596](https://github.com/astarte-platform/astarte-kubernetes-operator/issues/596) |
| `dgraph` | [dgraph-io/charts#155](https://github.com/dgraph-io/charts/issues/155) |
| `franzinc` | [franzinc/agraph-examples#51](https://github.com/franzinc/agraph-examples/issues/51) |
| `hue` | [cloudera/hue#4359](https://github.com/cloudera/hue/issues/4359) |
| `sstarcher` | [sstarcher/helm-exporter#209](https://github.com/sstarcher/helm-exporter/issues/209) |

Each issue was re-fetched after posting and matched the approved repository-specific message, Artifact Hub URL, source/feed, and repository ID. The public activity overlay was updated in the existing `2026-07-31` table.

The remaining two approved contacts were completed manually: Pomerium's Discuss topic is [here](https://discuss.pomerium.com/t/artifact-hub-ownership-claim-for-the-pomerium-helm-repository/513), and the Ververica email was sent to `platform@ververica.com`. Neither has replied or provided claim evidence; Ververica has not sent a receipt confirmation.

### Manual Contact Templates: 2026-07-31

#### Pomerium Discuss

- Destination: [Pomerium support category](https://discuss.pomerium.com/c/support/9)
- Title: `Artifact Hub ownership claim for the Pomerium Helm repository`
- Artifact Hub repository: `https://artifacthub.io/repositories/helm/pomerium`
- Repository ID: `ae611f10-efda-48d7-ad03-3ed960f591cd`
- Source/feed: `https://github.com/pomerium/pomerium` and `https://helm.pomerium.io/`
- Instructions: Open a new topic in the support category, use the title above, paste the message below, and retain the topic URL as durable contact evidence. Do not open a GitHub issue in `pomerium/pomerium` for this request.

```text
Hello,

I am reaching out about the Artifact Hub repository for Pomerium:

https://artifacthub.io/repositories/helm/pomerium

Helm currently receives notifications for this listing. The validated Helm source is https://helm.pomerium.io/, published by https://github.com/pomerium/pomerium.

Artifact Hub repository ID: ae611f10-efda-48d7-ad03-3ed960f591cd

If your team still maintains this repository, please follow Artifact Hub ownership-claim instructions:

https://artifacthub.io/docs/topics/repositories/#ownership-claim

The claimant should publish an artifacthub-repo.yml file at the published Helm repository path containing the repository ID and the email address used by the claimant account. Please confirm here after the claim succeeds.

If you are no longer responsible for this repository, please redirect us to the current owner or team contact.

Thanks.
```

#### Ververica Email

- Destination: `platform@ververica.com`
- Subject: `Artifact Hub ownership claim for the Ververica Platform Helm repository`
- Artifact Hub repository: `https://artifacthub.io/repositories/helm/ververica`
- Repository ID: `1b372f65-8f35-4944-bfca-6921a1c31c64`
- Source/feed: `https://charts.ververica.com/`
- Instructions: Send the message below to Ververica Support. Save the sent message and any response as local evidence. Do not mark the repository contacted, replied, or claimed until the message is sent or a durable response is received.

```text
Hello Ververica Support,

I am reaching out about the Artifact Hub repository for Ververica Platform:

https://artifacthub.io/repositories/helm/ververica

Helm currently receives notifications for this listing. The validated Helm repository is:

https://charts.ververica.com/

Artifact Hub repository ID: 1b372f65-8f35-4944-bfca-6921a1c31c64

If Ververica still maintains this repository, please follow Artifact Hub ownership-claim instructions:

https://artifacthub.io/docs/topics/repositories/#ownership-claim

The claimant should publish an artifacthub-repo.yml file at the published Helm repository path containing the repository ID and the email address used by the claimant account. Please reply with the appropriate claimant or team identity and confirm here after the claim succeeds.

If Ververica is no longer responsible for this repository, please redirect us to the current owner or team contact.

Thanks.
```

## Audit Log

This log records completed work for review convenience. It is not the source of truth. The issue inventory is maintained by issue maintainers, and [issue comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) provides our dated activity overlay.

| Date       | Scope                                    | Completed work                                                                                                                                                                                                                                                                                                   | Evidence and result                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ---------- | ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2026-07-23 | Initial review                           | Audited all 20 contacted entries and inventoried source and maintainer gaps across 136 repositories.                                                                                                                                                                                                             | Recorded baseline: 86 identified sources, 50 unidentified sources, 27 unknown maintainers, 20 contacted, 1 replied, and 1 claimed.                                                                                                                                                                                                                                                                                                                                                                                                           |
| 2026-07-23 | Tracker reconciliation                   | Corrected the `camel-k` source and reconciled statuses for `camel-k`, `carlosjgp`, `ceph-csi`, `couchbase`, and `concourse`; moved `concourse` into the identified-source section.                                                                                                                               | [Tracker comment](https://github.com/helm/community/issues/428#issuecomment-5061350580) now contains 87 identified sources, 49 unidentified sources, 20 contacted, 6 replied, and 4 claimed.                                                                                                                                                                                                                                                                                                                                                 |
| 2026-07-23 | Outreach correction                      | Corrected copied Artifact Hub details in the existing `crate` and `smallstep` outreach threads.                                                                                                                                                                                                                  | [crate correction](https://github.com/crate/helm-charts/issues/10#issuecomment-5061828052) and [smallstep correction](https://github.com/smallstep/helm-charts/issues/266#issuecomment-5061828210). No tracker-row change was required.                                                                                                                                                                                                                                                                                                      |
| 2026-07-23 | Stale-contact audit                      | Revalidated all 13 unresolved contacted repositories against their contact threads, canonical Git sources, current chart metadata, repository lifecycle, and Artifact Hub ownership.                                                                                                                             | Corrected seven tracker rows covering `adwerx`, `apicheck`, `appdynamics`, `chubaofs`, `cloudwatch-agent`, `couchbase`, and `couchdb`. The [tracker comment](https://github.com/helm/community/issues/428#issuecomment-5061350580) now records 87 identified sources, 49 unidentified sources, 20 contacted, 7 replied, and 4 claimed.                                                                                                                                                                                                       |
| 2026-07-23 | Disposition and follow-up                | Added a non-duplicative disposition queue for `appdynamics`, `buildkite`, `cgroschupp`, `chubaofs`, and `cloudwatch-agent`; posted 12 approved follow-ups across the unresolved contact threads.                                                                                                                 | The [tracker disposition section](https://github.com/helm/community/issues/428#issuecomment-5061350580) records the five pending decisions. Representative follow-ups: [AppDynamics](https://github.com/CiscoDevNet/appdynamics-charts/issues/47#issuecomment-5062355524), [CouchDB](https://github.com/apache/couchdb-helm/issues/278#issuecomment-5062481711), and [AWS](https://github.com/aws/eks-charts/issues/1290#issuecomment-5062481538). No follow-up was posted for `chubaofs` because its successor is already separately owned. |
| 2026-07-24 | Progress reporting format                | Replaced the duplicated 136-row tracker comment with a dated activity log containing only repositories contacted or otherwise changed. Future work will be appended under new date headings for issue maintainers to apply to the original inventory.                                                            | [Activity comment](https://github.com/helm/community/issues/428#issuecomment-5061350580) records the 2026-07-23 work and pending disposition requests without duplicating the issue inventory.                                                                                                                                                                                                                                                                                                                                               |
| 2026-07-24 | Reporting and outreach requirements      | Updated the workflow to use a dated activity overlay and reviewed outreach batches of five highest-confidence repositories. Confirmed-source and confirmed-contact entries are prioritized; less-authoritative contacts are saved until last, and unconfirmed source candidates are researched without outreach. | The issue inventory remains maintainer-owned, while [activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) records completed work for maintainers to apply.                                                                                                                                                                                                                                                                                                                                     |
| 2026-07-24 | Source validation and outreach selection | Performed read-only provenance, lifecycle, ownership, and contact validation for eight malformed-source rows and eight strong source-unknown candidates. Selected `newrelic`, `seldon`, `jenkins`, `keel`, and `cloudposse` as the first five highest-confidence outreach targets.                               | All five selected repositories have confirmed publishing provenance, active project-owned issue channels, and Artifact Hub listings still owned by `helm`. No outreach or activity-comment update was performed during validation.                                                                                                                                                                                                                                                                                                           |
| 2026-07-24 | Couchbase claim and support follow-up    | Verified that the current Couchbase maintainer claimed the `couchbase` Artifact Hub repository under their user account, then verified the posted guidance for recovering access to the existing official organization and transferring the repository into it.                                                  | Artifact Hub lists the repository under `ben.mottershead`, not `helm`. [The support response](https://github.com/couchbase-partners/helm-charts/issues/152#issuecomment-5075930517) is visible and matches the reviewed guidance; migration into the official `couchbase` organization remains pending.                                                                                                                                                                                                                                      |
| 2026-07-24 | Couchbase activity update                | Appended a dated activity entry recording the confirmed Couchbase reply and ownership claim without modifying the previous activity section.                                                                                                                                                                     | [Activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) records that ownership moved out of `helm`; transfer into the official `couchbase` organization remains pending.                                                                                                                                                                                                                                                                                                                         |
| 2026-07-24 | Crate follow-up deferral                 | Reviewed the Crate ownership discussion after a historical contributor declined responsibility. Deferred further outreach to allow the Crate organization time for internal discussion.                                                                                                                          | The listing remains enabled and owned by `helm`; [issue #10](https://github.com/crate/helm-charts/issues/10) will be revisited after the first-pass review of all remaining repositories.                                                                                                                                                                                                                                                                                                                                                    |
| 2026-07-25 | First Tier 1 outreach batch              | Revalidated Artifact Hub ownership and duplicate-request status, then opened five approved ownership-transfer requests for `newrelic`, `seldon`, `jenkins`, `keel`, and `cloudposse`.                                                                                                                            | Requests: [New Relic](https://github.com/newrelic/helm-charts/issues/2360), [Seldon](https://github.com/SeldonIO/seldon-core/issues/7115), [Jenkins Operator](https://github.com/jenkinsci/kubernetes-operator/issues/1185), [Keel](https://github.com/keel-hq/keel/issues/864), and [Cloud Posse](https://github.com/cloudposse/charts/issues/282). GitHub did not apply New Relic's requested `feature request` label, and the posting account lacks permission to add it.                                                                 |
| 2026-07-25 | Restart handoff                          | Added a temporary restart handoff preserving the detailed findings for 16 validated repositories, first-batch status and links, work queues, deferred follow-ups, and the next read-only validation step.                                                                                                        | A restarted session can continue from `Restart Handoff (Temporary)` without relying on prior conversation context or repeating completed source research.                                                                                                                                                                                                                                                                                                                                                                                    |
| 2026-07-25 | Second Tier 1 outreach batch             | Revalidated duplicate-request status and current Artifact Hub ownership, then opened five approved ownership-transfer requests for `kedacore`, `descheduler`, `openfaas`, `sysdiglabs`, and `vmware-tanzu`.                                                                                                      | Requests: [KEDA](https://github.com/kedacore/charts/issues/889), [Descheduler](https://github.com/kubernetes-sigs/descheduler/issues/1903), [OpenFaaS](https://github.com/openfaas/faas-netes/issues/1254), [Sysdig](https://github.com/sysdiglabs/charts/issues/2696), and [VMware Tanzu](https://github.com/vmware-tanzu/helm-charts/issues/745).                                                                                                                                                                                          |
| 2026-07-25 | Third Tier 1 outreach batch              | Revalidated duplicate-request status and current Artifact Hub ownership, then opened five approved ownership-transfer requests for `falcosecurity`, `prometheus-msteams`, `cryptlex`, `jitterbit`, and `inlets`.                                                                                                 | Requests: [Falco Security](https://github.com/falcosecurity/charts/issues/1048), [Prometheus MSTeams](https://github.com/prometheus-msteams/prometheus-msteams/issues/440), [Cryptlex](https://github.com/cryptlex/helm-charts/issues/119), [Jitterbit](https://github.com/jitterbit/charts/issues/24), and [inlets](https://github.com/inlets/inlets-operator/issues/174).                                                                                                                                                                  |
| 2026-07-25 | Next-batch candidate refresh             | Rebuilt the remaining uncontacted identified-source pool after three Tier 1 outreach batches and refreshed next-batch priorities while preserving Tier 2 and disposition queues for later phases.                                                                                                                | Prepared next Tier 1 candidates: `gresearch`, `litmuschaos`, `privatebin`, `kuberhealthy`, and `ealenn`; alternates: `crowdfox`, `odavid`, `gkarthiks`, `gabibbo97`, and `hmdmph`. Artifact Hub API returned temporary `HTTP 429` during deep validation, so ownership must be rechecked immediately before posting.                                                                                                                                                                                                                         |
| 2026-07-25 | Rate-limit-safe candidate revalidation   | Revalidated the prepared and alternate Tier 1 candidates using paced Artifact Hub API requests after temporary rate limiting was observed.                                                                                                                                                                       | Confirmed Helm ownership and no duplicate ownership-transfer issues for `gresearch`, `litmuschaos`, `privatebin`, `kuberhealthy`, `ealenn`, `crowdfox`, `odavid`, `gkarthiks`, `gabibbo97`, and `hmdmph`. Added reusable rate-limit handling guidance for future validation runs.                                                                                                                                                                                                                                                            |
| 2026-07-25 | Fourth Tier 1 outreach batch             | Revalidated duplicate-request status and current Artifact Hub ownership, then opened five approved ownership-transfer requests for `gresearch`, `litmuschaos`, `privatebin`, `kuberhealthy`, and `ealenn`.                                                                                                       | Requests: [G-Research](https://github.com/G-Research/charts/issues/140), [LitmusChaos](https://github.com/litmuschaos/litmus-helm/issues/494), [PrivateBin](https://github.com/PrivateBin/helm-chart/issues/136), [Kuberhealthy](https://github.com/kuberhealthy/kuberhealthy/issues/1523), and [Ealenn](https://github.com/Ealenn/charts/issues/54).                                                                                                                                                                                        |
| 2026-07-25 | Fifth-batch candidate selection          | Rebuilt and re-ranked the remaining active uncontacted identified-source pool after four posted outreach batches using rate-limit-safe Artifact Hub checks and repository-lifecycle screening.                                                                                                                   | Prepared next Tier 1 candidates: `odavid`, `mogaal`, `dniel`, `gkarthiks`, and `hmdmph`; alternates: `pcktdmp`, `crowdfox`, `http-folder`, `gabibbo97`, and `riskfocus`. Duplicate ownership-request searches were clear for the five prepared candidates. Temporary `HTTP 429` responses occurred later in the scan for `vulcanlink`, `wavefront`, and `zooz`; recheck before using them.                                                                                                                                                   |
| 2026-07-25 | Fifth-batch preflight revalidation       | Revalidated the five prepared Tier 1 candidates with slower Artifact Hub pacing to reduce rate-limit risk before drafting outreach.                                                                                                                                                                              | Confirmed Helm ownership and no duplicate ownership-transfer issues for `odavid`, `mogaal`, `dniel`, `gkarthiks`, and `hmdmph` at a slower two-plus-second cadence between calls. Updated the local rate-limit playbook with adaptive slowdown and backoff guidance.                                                                                                                                                                                                                                                                         |
| 2026-07-25 | Fifth Tier 1 outreach batch              | Revalidated duplicate-request status and current Artifact Hub ownership with slower pacing, then opened five approved ownership-transfer requests for `odavid`, `mogaal`, `dniel`, `gkarthiks`, and `hmdmph`.                                                                                                    | Requests: [odavid](https://github.com/odavid/k8s-helm-charts/issues/29), [mogaal](https://github.com/mogaal/helm-charts/issues/25), [dniel](https://github.com/dniel/charts/issues/2), [gkarthiks](https://github.com/gkarthiks/helm-charts/issues/13), and [hmdmph](https://github.com/hmdmph/helm-charts/issues/18).                                                                                                                                                                                                                       |
| 2026-07-25 | Sixth-batch candidate selection          | Rebuilt and re-ranked the remaining active uncontacted identified-source pool after five posted outreach batches using slow-pacing Artifact Hub checks and repository-lifecycle screening.                                                                                                                       | Prepared next Tier 1 candidates: `vulcanlink`, `zooz`, `pcktdmp`, `crowdfox`, and `http-folder`; alternates: `gabibbo97`, `riskfocus`, `liwenhe`, `pndaproject`, and `snl-charts`. Duplicate ownership-request searches were clear for the five prepared candidates.                                                                                                                                                                                                                                                                         |
| 2026-07-25 | Sixth Tier 1 outreach batch              | Revalidated duplicate-request status and current Artifact Hub ownership with slow pacing, then opened five approved ownership-transfer requests for `vulcanlink`, `zooz`, `pcktdmp`, `crowdfox`, and `http-folder`.                                                                                              | Requests: [vulcanlink](https://github.com/vulcanlink/charts/issues/36), [zooz](https://github.com/Zooz/helm/issues/15), [pcktdmp](https://github.com/pcktdmp/charts/issues/42), [crowdfox](https://github.com/CrowdfoxGmbH/cfcharts/issues/2), and [http-folder](https://github.com/AurelienGasser/charts/issues/4).                                                                                                                                                                                                                         |
| 2026-07-25 | Outreach template normalization          | Reworked the remaining unanswered 2026-07-25 issue bodies to match the Seldon-style template, except for the restrictive New Relic template and the already-responded Descheduler thread. | Updated `jenkins`, `keel`, `cloudposse`, `kedacore`, `openfaas`, `sysdiglabs`, `vmware-tanzu`, `falcosecurity`, `prometheus-msteams`, `cryptlex`, `jitterbit`, `inlets`, `gresearch`, `litmuschaos`, `privatebin`, `kuberhealthy`, `ealenn`, `odavid`, `mogaal`, `dniel`, `gkarthiks`, `hmdmph`, `vulcanlink`, `zooz`, `pcktdmp`, `crowdfox`, and `http-folder`; left `newrelic` on its mandatory template and `descheduler` unchanged after response. |
| 2026-07-30 | Follow-up status reconciliation          | Reviewed seven subsequent updates from contacted repositories and reconciled claims, replies, corrections, and disposition findings. | `couchbase` is now owned by the official organization; `hmdmph` confirmed a successful claim; `crate` requested removal after deprecation and archival; `smallstep` corrected its copied link; `prometheus-msteams` replied without claiming; `sysdiglabs` merged claim metadata but still requires publication and Artifact Hub verification; and `kuberhealthy` remains blocked by a stale Artifact Hub URL. |
| 2026-07-30 | Artifact Hub claim verification          | Rechecked the remaining blocker threads and current Artifact Hub repository metadata. | Artifact Hub now reports `sysdiglabs` owned by the `sysdig` organization with `verified_publisher: true`; `kuberhealthy` remains blocked by its stale registered URL; and `prometheus-msteams` still lacks `artifacthub-repo.yml`. |
| 2026-07-30 | Seventh Tier 1 outreach reconciliation  | Confirmed that the previously prepared seventh-batch candidates were already contacted on 2026-07-25 and have no replies or claims. | Existing requests: [gabibbo97](https://github.com/gabibbo97/charts/issues/54), [riskfocus](https://github.com/riskfocus/helm-charts-public/issues/39), [liwenhe](https://github.com/liwenhe1993/charts/issues/14), [pndaproject](https://github.com/pndaproject/pnda-helm-chart/issues/10), and [snl-charts](https://github.com/snebel29/snl-charts/issues/1). Their repositories are unarchived but dormant, with last pushes in 2020 or 2021. |
| 2026-07-30 | Eighth-batch candidate selection          | Performed a fresh read-only selection pass after excluding all 35 previously contacted repositories and screening source health, Artifact Hub ownership, and duplicate requests. | Prepared `fluent`, `snyk`, `appuio`, `crossplane`, and `ory`; all are currently Helm-owned with current package/source evidence and project-owned issue channels. `crossplane` has unrelated existing Artifact Hub discussions that require careful separation from ownership outreach. |
| 2026-07-30 | Tier 2 preflight                         | Reviewed the provisional Tier 2 queue and researched replacements without contacting repositories. | Eligible candidates: `simplyzee`, `equinor-charts`, and `dhiatn`. Routed `dacruz21` to lifecycle/disposition research, `stardog` to disposition-first handling because its source is archived, and `ibm-charts` to contact-blocked because IBM has disabled Issues and Discussions. The five-target Tier 2 batch remains open pending two more qualifying candidates. |
| 2026-07-30 | Population census                         | Assigned all 136 inventory rows to a disjoint provisional queue before continuing outreach planning. | Counts: 53 contacted/awaiting/claimed, 13 disposition, 8 lifecycle research, 45 source research, 11 Tier 1, 3 Tier 2, 2 contact-blocked, and 1 no-outreach-needed. The queue partition sums to 136; no public tracker changes were made. |
| 2026-07-30 | Tier 1 lifecycle preflight                 | Rechecked all 11 provisional Tier 1 candidates before preparing outreach. | Six archived candidates moved to disposition (`enapter`, `infobloxopen`, `lifen`, `owkin`, `pangeo`, `wavefront`); four dormant candidates moved to Tier 2 (`lohmag`, `mtls`, `qamatic`, `rasooll`); and `ruguodangshi` moved to contact-blocked because GitHub Issues and Discussions are disabled. No Tier 1 outreach was posted. |
| 2026-07-30 | Replacement Tier 1 selection               | Rebuilt the Tier 1 population from remaining source-research rows using current Artifact Hub ownership, source health, lifecycle, contactability, and duplicate-request checks. | Prepared `agones`, `influxdata`, `jfrog`, `kanister`, and `rancher-stable`; all are current, Helm-owned, source-confirmed, and contactable. |
| 2026-07-30 | Tier 1 replacement outreach               | Opened the approved ownership-transfer requests for the replacement Tier 1 batch. | Requests: [agones](https://github.com/agones-dev/agones/issues/4667), [influxdata](https://github.com/influxdata/helm-charts/issues/816), [jfrog](https://github.com/jfrog/charts/issues/2457), [kanister](https://github.com/kanisterio/kanister/issues/4149), and [rancher-stable](https://github.com/rancher/rancher/issues/56325). |
| 2026-07-30 | Tier 2 outreach batch                   | Completed read-only preflight and opened the first five Tier 2 ownership-transfer requests. | Requests: [simplyzee](https://github.com/simplyzee/simplyzee-charts/issues/1), [equinor-charts](https://github.com/equinor/helm-charts/issues/12), [dhiatn](https://github.com/DhiaTN/helm-kafka-topics-ui/issues/3), [lohmag](https://github.com/lohmag/helm-charts/issues/2), and [mtls](https://github.com/drGrove/charts/issues/1). |
| 2026-07-30 | Tier 2 completion batch               | Completed read-only preflight and opened the final two Tier 2 ownership-transfer requests. | Requests: [qamatic](https://github.com/qamatic/charts/issues/1) and [rasooll](https://github.com/rasooll/helm-charts/issues/1). Tier 2 is now complete. |
| 2026-07-30 | Disposition research                  | Completed a read-only review of `crate`, `eventstore`, `gradiant`, `squidex`, and `talend`. | `crate`, `eventstore`, `gradiant`, and `squidex` remain disposition-oriented; `talend` is an active source-confirmed repository and should return to ownership-outreach review. No external writes were made. |
| 2026-07-30 | Disposition next-step assignment       | Completed a read-only review of the remaining 14 disposition repositories and assigned a concrete next step to each. | Recorded removal, disablement, reconciliation, contact-blocked, follow-up, and reclassification actions locally. No external writes were made. |
| 2026-07-30 | Disposition tracker addendum           | Added the first five disposition recommendations to the existing activity-comment addendum. | Recorded administrator removal, disablement, or reconciliation recommendations for `crate`, `eventstore`, `gradiant`, `chubaofs`, and `cloudwatch-agent`; no project outreach was posted. |
| 2026-07-30 | Confirmation follow-up batch           | Posted follow-up questions to three existing project threads and attempted project-owned issue creation for two archived repositories. | Follow-ups posted for `appdynamics`, `buildkite`, and `cgroschupp`; GitHub rejected issue creation for `lifen` and `owkin`, which moved to contact-blocked. Tracker rows and an explanatory addendum were updated. |
| 2026-07-30 | Talend reclassification and outreach    | Revalidated the live source, chart index, Artifact Hub ownership, and duplicate-request status, then moved `talend` to the active outreach population and opened an ownership request. | Request: [Talend/helm-charts-public#57](https://github.com/Talend/helm-charts-public/issues/57). The tracker row was updated; no internal tier label was published. |
| 2026-07-30 | Disposition evidence addendum           | Added linked evidence and confidence levels for the next five disposition recommendations. | Recorded moderate evidence for `enapter` and strong deprecation/successor evidence for `infobloxopen`, `pangeo`, `smueller18`, and `stardog` in the public addendum and local record. |
| 2026-07-30 | Remaining disposition evidence         | Added linked evidence and confidence levels for all six remaining disposition repositories. | Recorded follow-up, administrator decision, duplicate reconciliation, and contact-channel next steps for `appdynamics`, `buildkite`, `cgroschupp`, `squidex`, `waldur`, and `wavefront` in the public addendum and local record. |
| 2026-07-30 | Disposition addenda consolidation       | Consolidated the three same-day disposition subsections into one `Disposition Review` addendum without changing the prior-day disposition section. | All 16 same-day disposition entries now use the linked evidence-strength format; the prior `2026-07-23` section remains unchanged. |
| 2026-07-30 | Disposition addenda formatting repair  | Removed a duplicated six-entry tail created during consolidation and revalidated the live comment boundaries. | The prior-day section, one current `Disposition Review` section, and the archived confirmation blockers are preserved; all 16 current entries are unique. |
| 2026-07-30 | Handoff refresh                        | Rewrote the restart handoff to reflect the completed outreach phases, current queue partition, no-write boundary, and revised read-only-first execution order. | The next session should process lifecycle, contact-blocked, and source research before executing disposition writes; no external write is currently pending approval. |
| 2026-07-31 | Lifecycle research                     | Completed a read-only lifecycle review of `dacruz21`, `flink-operator`, `k8s-dashboard`, `kubedex`, `monocular`, `pfisterer-knox`, `quarks`, and `volcano`. | Recorded source, Artifact Hub, archive/retirement, endpoint, and successor evidence in the local `Lifecycle Research: 2026-07-31` section. All eight route to disposition-oriented handling; no external writes were made. |
| 2026-07-31 | Contact-blocked research               | Searched official project sites, support portals, repository capabilities, and successor/fork relationships for `ibm-charts`, `lifen`, `owkin`, `ruguodangshi`, and `snyk`. | `ibm-charts` and `snyk` have public pull-request channels and moved to local `contact-ready`; `lifen`, `owkin`, and `ruguodangshi` remain `contact-blocked`. No external writes were made. |
| 2026-07-31 | Pull-request draft preparation          | Resolved Artifact Hub repository IDs, target branches, metadata paths, contribution guidance, and exact draft bodies for `ibm-charts` and `snyk`. | Drafts are recorded locally; both require a real metadata diff and the current claimant's Artifact Hub identity before any PR can be posted. No external writes were made. |
| 2026-07-31 | Pull-request path correction             | Reviewed repository contribution rules and corrected the initial contact-ready classification for `ibm-charts`. | IBM's contribution guidance excludes `stable` from GitHub contributions, so `ibm-charts` returned to `contact-blocked`; `snyk` remains contact-ready, but its claimant email and metadata diff are not publicly established. No external writes were made. |
| 2026-07-31 | Snyk support contact draft               | Prepared an exact private support request using Snyk's documented support channel to identify the current Artifact Hub claimant. | Draft is local and pending explicit approval before submission; no support request or other external write was made. |
| 2026-07-31 | Snyk support outreach                    | Submitted the approved Artifact Hub ownership request through Snyk's support channel using the user's work email. | Snyk sent an automated receipt confirming the request was received; no ticket number, maintainer identity, ownership confirmation, or claim evidence was provided. Snyk is contacted/awaiting response; `Replied` and `Claimed` remain unrecorded. |
| 2026-07-31 | Source-research census reconciliation    | Reconciled the recorded source-research count and list against all 136 public inventory rows using a read-only issue fetch. | Found `39` enumerated names under a recorded count of `40`; added `vertigo` (`https://charts.vertigo.com.br/`) as the missing 40th source-research row. No external writes were made. |
| 2026-07-31 | Runix external outreach reconciliation   | Reviewed the independently opened ownership-transfer request for `runix` and recorded it without duplicating outreach. | [rowanruseler/helm-charts#351](https://github.com/rowanruseler/helm-charts/issues/351) was opened by `@SetagGnaw` and contains the Artifact Hub listing, Helm feed, source repository, and repository ID. No reply or claim is present; `runix` remains in source research pending independent provenance validation. |
| 2026-07-31 | Source-research batch 1                 | Completed the first read-only batch for 10 source-research rows, inspecting live feeds, indexes, source candidates, lifecycle, and contactability. | Recorded evidence and provisional outcomes for `astarte`, `balle-petersen`, `banzaicloud-stable`, `brannon`, `camptocamp`, `choerodon`, `cleardata`, `cronce`, `datawire`, and `dgraph`; no external writes or outreach were made. |
| 2026-07-31 | Source-research batch 2                 | Completed the second read-only batch for 10 source-research rows, inspecting live feeds, indexes, source candidates, lifecycle, and contactability. | Recorded evidence and provisional outcomes for `dragonchain`, `fermosit`, `fold`, `forseti-security`, `franzinc`, `fyipe`, `gomods`, `gp42`, `hue`, and `inspur`; no external writes or outreach were made. |
| 2026-07-31 | Source-research batch 3                 | Completed the third read-only batch for 10 source-research rows, inspecting live feeds, indexes, source candidates, lifecycle, and contactability. | Recorded evidence and provisional outcomes for `k8s-land`, `kiwigrid`, `kremers`, `larribas`, `microsoft`, `mirusresearch`, `opsdroid`, `pl-helm-charts`, `pomerium`, and `purestorage`; no external writes or outreach were made. |
| 2026-07-31 | Source-research interim consolidation   | Consolidated the evidence from the first three 10-row read-only batches without changing queue assignments or contacting projects. | Summarized 30 of 40 rows into active, successor/reconciliation, dormant, disposition-oriented, and unresolved groups. The final ten rows remain pending; no external writes were made. |
| 2026-07-31 | Source-research batch 4                 | Completed the final read-only batch for 10 source-research rows, inspecting live feeds, indexes, source candidates, lifecycle, migrations, and contactability. | Recorded evidence and provisional outcomes for `redsky`, `runix`, `softonic`, `soluto`, `sstarcher`, `t3n`, `trickster`, `uswitch`, `ververica`, and `vertigo`; no external writes or outreach were made. |
| 2026-07-31 | Source-research complete consolidation  | Consolidated all four read-only batches into a complete 40-row provisional outcome table. | Identified 9 source-confirmed active rows, 5 active source/successor reconciliation candidates, 5 stale candidates, 8 archived/dead/rebranded candidates, and 13 unresolved provenance/lifecycle rows. No public inventory or queue assignment was changed. |
| 2026-07-31 | Source-research queue reclassification  | Assigned all 40 researched rows to the existing local reason queues using the completed provenance, lifecycle, and contactability evidence. | Moved eight rows to contact-ready pending final preflight, `runix` to contacted/awaiting because an existing ownership request is present, 13 rows to disposition, and retained 18 rows in source research. No public inventory, tracker, or outreach write was made. |
| 2026-07-31 | Contact-ready preflight                 | Checked current Artifact Hub package identities, repository IDs, source/contact paths, and duplicate ownership-request evidence for all eight contact-ready candidates. | Seven rows remain contact-ready. `trickster` returned to source research because its Helm-owned historical listing is distinct from a separate verified AppsCode listing and its source has migrated to OCI. No external writes were made. |
| 2026-07-31 | Contact-ready outreach                  | Posted the approved ownership-transfer requests for five preflighted repositories and updated the existing public activity table. | Requests: [astarte](https://github.com/astarte-platform/astarte-kubernetes-operator/issues/596), [dgraph](https://github.com/dgraph-io/charts/issues/155), [franzinc](https://github.com/franzinc/agraph-examples/issues/51), [hue](https://github.com/cloudera/hue/issues/4359), and [sstarcher](https://github.com/sstarcher/helm-exporter/issues/209). All five rendered bodies were re-fetched and verified. |
| 2026-07-31 | Manual contact completion              | Recorded the user-reported Pomerium Discuss topic and Ververica email submission. | [Pomerium topic](https://discuss.pomerium.com/t/artifact-hub-ownership-claim-for-the-pomerium-helm-repository/513) is durable contact evidence; the Ververica email was sent but produced no receipt or response. Neither repository has reply or claim evidence. |
| 2026-07-31 | Talend follow-up response              | Posted an approved `needs-response` follow-up answering Talend's ownership, account-access, no-claim, and removal questions. | [Follow-up response](https://github.com/Talend/helm-charts-public/issues/57#issuecomment-5147323956) was authored by Helm, not Talend. `Replied` and `Claimed` remain unrecorded; await Talend's decision to claim or request disablement/removal. |
| 2026-07-31 | Crossplane reply reconciliation        | Reviewed the Crossplane maintainer's response to the ownership request. | [Crossplane reply](https://github.com/crossplane/crossplane/issues/7659#issuecomment-5134272016) acknowledges the request and says the maintainer will attempt the claim for the Crossplane organization. Record `Replied`; leave `Claimed` unset. No response from Helm is needed. |
| 2026-07-31 | T3n ownership outreach                | Posted the approved Artifact Hub ownership request to the active t3n Helm chart repository and appended the corresponding activity row. | [t3n/helm-charts#214](https://github.com/t3n/helm-charts/issues/214); the issue body and updated activity table were re-fetched and verified. `Replied` and `Claimed` remain unrecorded. |
| 2026-07-31 | Disposition tracker completion         | Appended the remaining 10 disposition recommendations to the existing dated activity section. | The public activity overlay now records all 35 local disposition recommendations; no Artifact Hub administrator request was made. |
| 2026-07-31 | Wombat tracker reconciliation          | Added a no-outreach activity row identifying the reconciled source and existing outside-Helm ownership. | The activity row was verified. Updating the original issue-body source field failed with GitHub `403` because the posting account lacks repository-admin rights; maintainer action remains required. |

### Disposition Reclassification: 2026-07-31

The remaining four source-research disposition candidates were rechecked read-only. No public inventory, GitHub, Artifact Hub, or project-contact writes were made.

| Repository | Current evidence | Local routing | Next step |
| --- | --- | --- | --- |
| `fold` | The source repository is active and was updated in 2025; the feed is stale and contains multiple chart identities, with the tracked relationship requiring exact reconciliation. | `contact-ready` | Perform final Artifact Hub identity and duplicate-request preflight before considering outreach. |
| `t3n` | The source repository remains active, and the feed was generated in 2025 with later chart entries; the listing is stale but not demonstrably terminal. | `contact-ready` | Perform final Artifact Hub identity and duplicate-request preflight before considering outreach. |
| `balle-petersen` | The source and feed remain reachable but are dormant; the latest feed entries date to 2020. | `disposition` | Seek a maintainer decision before any administrator request; do not infer removal solely from dormancy. |
| `brannon` | The source and feed remain reachable but are dormant; the latest feed entries date to 2020. | `disposition` | Seek a maintainer decision before any administrator request; do not infer removal solely from dormancy. |

The resulting local partition is `75` contacted/awaiting/claimed, `35` disposition, `2` contact-ready, `19` source research, `4` contact-blocked, and `1` no-outreach-needed, totaling `136`. This reclassification does not authorize outreach or administrator action.

### Contact-Ready Preflight Recheck: 2026-07-31

The final preflight rechecked the exact Artifact Hub repository records, package identities, source mapping, and duplicate ownership requests for `fold` and `t3n`. No GitHub, Artifact Hub, or project-contact writes were made.

| Repository | Artifact Hub evidence | Source/contact preflight | Duplicate-request check | Result |
| --- | --- | --- | --- | --- |
| `fold` | Repository `fold`, ID `52cfb567-b05e-43ac-9513-bc19916314a4`, remains Helm-owned. The repository contains `lnd`, `bitcoind`, `pgbouncer`, and historical `jupyter-notebook` packages. | `fold-team/helm-charts` is active and publishes the feed, but GitHub reports that issue creation is restricted. The Fold website exposes private support channels but no durable public maintainer thread. | No Artifact Hub ownership request was found in the repository's searchable issues. | Return to `contact-blocked`; do not use the restricted issue path or private support without separate approval. |
| `t3n` | Repository `t3n`, ID `d1a688e1-1880-47a0-b6f0-921c8c95620c`, remains Helm-owned. The tracked `web` package has ID `f405f0dd-3666-483f-9f15-c11fecd61d24`, version `2.1.0`. | `t3n/helm-charts` is active, has writable issues, and publishes the feed at `https://storage.googleapis.com/t3n-helm-charts`. The repository identifies itself as actively developed and lists `max.schmidt@t3n.de` in chart metadata. | The only search result containing `artifacthub` was an unrelated closed SnipeIT issue; no ownership request was found before posting. | Ownership request posted at [issue #214](https://github.com/t3n/helm-charts/issues/214); await reply or claim evidence. |

The corrected local partition after posting is `76` contacted/awaiting/claimed, `35` disposition, `0` contact-ready, `19` source research, `5` contact-blocked, and `1` no-outreach-needed, totaling `136`.

### Queue Priority: 2026-07-31

The next execution order is:

1. Resolve the remaining 10 disposition recommendations and prepare exact public tracker row diffs for maintainer review.
2. Continue the 19-row source-research pass read-only; do not contact projects until provenance and chart identity are established.
3. Recheck the 5 contact-blocked rows for durable project-owned channels, retaining blockers where no valid channel exists.
4. Have an issue maintainer apply the `wombat` source correction; its no-outreach evidence is already recorded publicly.
5. Passively monitor existing outreach for replies and claims.

`contact-ready` requires no tracker update because the queue is empty. `wombat` does require a future public inventory reconciliation, but no ownership outreach.

### Proposed Tracker Updates: 2026-07-31

The proposal has now been posted to the existing `2026-07-31` `Disposition Review` section and activity table. No internal queue labels were published.

#### Disposition Review Addendum

```md
- `dacruz21`: **Strong evidence for terminal review.** The registered feed endpoint returns 404. The validated historical source is [typokign/helm-charts](https://github.com/typokign/helm-charts), but it has been dormant since 2020. Recommend correcting the source if the listing is retained, then requesting disablement or removal unless a current owner confirms responsibility; do not transfer by inference.
- `flink-operator`: **Strong evidence.** The source repository is archived, explicitly deprecated, and directs users to the Apache Flink Kubernetes Operator or Google Cloud Dataproc. Recommend removal or disablement of the historical listing; do not transfer it to the successor by inference.
- `k8s-dashboard`: **Strong evidence.** The registered feed endpoint returns 404 and the source resolves to the archived `kubernetes-retired/dashboard` repository. Recommend removal or disablement; do not infer a successor claim.
- `kubedex`: **Moderate evidence.** The feed remains live, but the source and generated index have been dormant since 2019. Seek a project or administrator decision on retaining or removing the dormant listing; do not assert automatic removal from dormancy alone.
- `monocular`: **Strong evidence.** The Helm source is archived and explicitly described as obsolete, while the historical feed remains present. Recommend removal or disablement; no ownership transfer is appropriate.
- `pfisterer-knox`: **Strong evidence.** The source repository is archived and no current project-owned successor or maintainer was validated. Recommend removal or disablement unless a current Apache Knox owner explicitly confirms responsibility.
- `quarks`: **Strong evidence.** The Helm repository and its operator source are archived, while the historical feed remains live. Recommend removal or disablement; do not infer that a current Cloud Foundry successor owns the listing.
- `volcano`: **Strong evidence for stale retired-source reconciliation.** The registered feed returns 404 and the old source belongs to the retired `volcano-retired` organization. The active project publishes through `volcano-sh/helm-charts`; request administrator reconciliation or removal of the old listing, not an inferred transfer.
- `balle-petersen`: **Moderate evidence.** The feed and source remain reachable but have been dormant since 2020. Ask the project to confirm whether it wants to retain and claim the listing or have it disabled or removed; do not infer removal solely from dormancy.
- `brannon`: **Moderate evidence.** The feed and source remain reachable but have been dormant since 2020. Ask the project to confirm whether it wants to retain and claim the listing or have it disabled or removed; do not infer removal solely from dormancy.

These recommendations are presented for maintainer review. No Artifact Hub administrator request has been made.
```

Evidence links for the addendum are already recorded in the local lifecycle and source-research sections above. Before posting, append the relevant source and Artifact Hub links to each row and re-fetch the rendered comment for Markdown verification.

#### `wombat` Inventory Diff

Public issue: [helm/community#428](https://github.com/helm/community/issues/428)

| Field | Current | Proposed |
| --- | --- | --- |
| `Repo` | `wombat` | `wombat` |
| `Source` | `https://github.com/esl/helm-chartcharts/wombatChart` | `https://github.com/esl/helm-chart/tree/master/charts/wombatChart` |
| `Maintainers` | Existing values unchanged | Existing values unchanged |
| `Contacted` | Unchecked | Unchecked |
| `Replied` | Unchecked | Unchecked |
| `Claimed` | Unchecked | Unchecked |

No summary-count change is expected: `wombat` remains in the identified-source section and no contact or claim checkbox changes. The activity-table row should be:

```md
| wombat | No outreach needed | Not recorded | Not recorded | Corrected source to `esl/helm-chart/tree/master/charts/wombatChart`; ownership is already established outside Helm after source reconciliation. |
```

The activity row was posted, but updating the original issue-body source field returned GitHub `403: Must have admin rights to Repository`. The source correction remains a maintainer-applied change. This is a tracker reconciliation only; it does not request an ownership transfer or Artifact Hub administrator action.

### Tracker Update Outcome: 2026-07-31

- The public activity overlay now contains all 35 disposition recommendations, including the final 10 added in this pass.
- The public activity overlay records `wombat` as no outreach needed and identifies the reconciled canonical source.
- The original issue-body `wombat` source field remains unchanged because the posting account lacks repository-admin rights.
- No public summary-count change was made or is expected from the `wombat` correction.
- No Artifact Hub administrator request was made.

#### `t3n` Outreach Draft

- Destination: [t3n/helm-charts issues](https://github.com/t3n/helm-charts/issues), pending approval.
- Proposed title: `[Artifact Hub] Claim ownership of the t3n Helm repository`
- Proposed body:

```md
Hello,

I am reaching out about the Artifact Hub repository for the t3n Helm charts:

https://artifacthub.io/repositories/helm/t3n

Helm currently receives notifications for this listing. The validated Helm repository is:

https://storage.googleapis.com/t3n-helm-charts

The publishing source is:

https://github.com/t3n/helm-charts

Artifact Hub repository ID: `d1a688e1-1880-47a0-b6f0-921c8c95620c`

If the t3n team still maintains this repository, please follow Artifact Hub's ownership-claim instructions:

https://artifacthub.io/docs/topics/repositories/#ownership-claim

The claimant should publish an `artifacthub-repo.yml` file at the published Helm repository path containing this repository ID and the email address used by the claimant's Artifact Hub account. Please confirm here after the claim succeeds.

If t3n is no longer responsible for this repository, please redirect us to the current owner or team contact.

Thanks.
```

The approved request was posted at [t3n/helm-charts#214](https://github.com/t3n/helm-charts/issues/214). The issue body and corresponding activity-table row were re-fetched and verified after posting.

### Incoming Updates: 2026-08-03

The following durable thread updates were reviewed. No GitHub, Artifact Hub, tracker, or project-contact writes were made.

#### `astarte`

Maintainer [@lucamarchiori](https://github.com/lucamarchiori) replied at [astarte-platform/astarte-kubernetes-operator#596](https://github.com/astarte-platform/astarte-kubernetes-operator/issues/596#issuecomment-5165460249) that [astarte-platform/helm](https://github.com/astarte-platform/helm) hosts the Helm source, while [astarte-platform/astarte-kubernetes-operator](https://github.com/astarte-platform/astarte-kubernetes-operator) builds and pushes the Helm package there through CI. The maintainer asked which repository should be linked to Artifact Hub.

This is a `needs-response` case. Read-only verification found that `https://helm.astarte-platform.org/index.yaml` is served from the `gh-pages` branch of `astarte-platform/helm`, while the chart metadata identifies `astarte-platform/astarte-kubernetes-operator` as the chart source. The feed repository currently has no published `artifacthub-repo.yml` at `https://helm.astarte-platform.org/artifacthub-repo.yml`. The clean distinction is: keep the operator repository as the chart source, and use the Helm repository as the published-feed and ownership-metadata location. The durable maintainer response supports setting `Replied`; `Claimed` remains unset.

**Posted response:**

```md
Thanks for clarifying. The two repositories have different roles here: `astarte-platform/astarte-kubernetes-operator` is the chart's source repository, while `astarte-platform/helm` hosts the published Helm feed at `https://helm.astarte-platform.org/`.

Please keep the operator repository as the chart source, and add the Artifact Hub ownership metadata to the published feed in `astarte-platform/helm` (the `gh-pages` branch), alongside `index.yaml`. The listing is:

https://artifacthub.io/repositories/helm/astarte

Artifact Hub repository ID: `35d6598b-7c7e-48a2-bb67-e83892385a43`

Once the Astarte team has added the metadata and completed the claim, please confirm here. If Artifact Hub requires the metadata in a different location, please let us know.
```

The response was manually posted by Helm at [issue comment 5169060318](https://github.com/astarte-platform/astarte-kubernetes-operator/issues/596#issuecomment-5169060318) on 2026-08-03. Await the Astarte team's confirmation or claim evidence; do not mark `Claimed` yet.

**Posted public tracker update:**

Apply a new dated section only. Do not modify the original inventory row, prior activity sections, or summary counts in this write. The `astarte` inventory reclassification and checkbox changes remain a separate future maintainer-applied reconciliation.

**Proposed new activity section for `## 2026-08-03`:**

```md
## 2026-08-03

| Repository | Contact | Replied | Claimed | Notes |
| --- | --- | --- | --- | --- |
| astarte | [astarte-platform/astarte-kubernetes-operator#596](https://github.com/astarte-platform/astarte-kubernetes-operator/issues/596) | Yes | Not recorded | Maintainer identified `astarte-platform/helm` as the published Helm feed and `astarte-platform/astarte-kubernetes-operator` as the build/source repository. Helm clarified the distinction and requested that the team add Artifact Hub ownership metadata to the published feed; awaiting confirmation or claim evidence. |
```

Optional addendum for the same new date:

```md
### Astarte

The published Helm feed is hosted by [`astarte-platform/helm`](https://github.com/astarte-platform/helm), while the chart source remains [`astarte-platform/astarte-kubernetes-operator`](https://github.com/astarte-platform/astarte-kubernetes-operator). Helm asked the Astarte team to add the Artifact Hub ownership metadata to the published feed and confirm the claim. The original inventory row and summary counts were not modified in this update.
```

The new section was appended to [activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) on 2026-08-03 and re-fetched successfully. No Artifact Hub administrator request was made, and no existing inventory row, prior activity section, or summary count was changed.

#### `runix`

The existing [rowanruseler/helm-charts#351](https://github.com/rowanruseler/helm-charts/issues/351) remains open and has no comments or claim evidence. Its issue body confirms the Artifact Hub repository ID, feed, source repository, and `pgadmin4` chart path. Combined with the local source-research result that the feed is live and identifies `rowanruseler/helm-charts`, this is durable contact and independently confirmed provenance.

Keep `runix` in contacted/awaiting monitoring. Do not open duplicate outreach or post a reminder: there is no maintainer response requiring Helm action, and the stale-response follow-up threshold has not been met.

#### `crossplane`

Maintainer [@jbw976](https://github.com/jbw976) replied at [crossplane/crossplane#7659](https://github.com/crossplane/crossplane/issues/7659#issuecomment-5134272016) that they will attempt to claim the repository for the Crossplane organization. This supports `Replied`; `Claimed` remains unset until Artifact Hub verifies the ownership change. No Helm response is needed, and no follow-up should be posted now.

### Audit Log Additions: 2026-08-03

| Date | Scope | Completed work | Evidence and result |
| --- | --- | --- | --- |
| 2026-08-03 | Incoming thread updates | Reviewed the Astarte maintainer response, the existing Runix ownership request, and the Crossplane maintainer acknowledgment. | Astarte requires a pending `needs-response` clarification about `astarte-platform/helm` versus `astarte-kubernetes-operator`; Runix remains contacted with no reply or claim; Crossplane remains `Replied` with `Claimed` unset. No external writes were made. |
| 2026-08-03 | Astarte clarification response | Manually posted the reviewed clarification on the Astarte ownership issue. | [Issue comment 5169060318](https://github.com/astarte-platform/astarte-kubernetes-operator/issues/596#issuecomment-5169060318) distinguishes the chart source from the published feed and asks Astarte to add ownership metadata to `astarte-platform/helm`. Await confirmation or claim evidence. |
| 2026-08-03 | Astarte activity tracker update | Appended the approved new-day activity row without modifying prior tracker content or the original inventory. | [Activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) now records `astarte` as replied and awaiting claim evidence; the rendered section was re-fetched and verified. |

### Source-Research Reconciliation: 2026-08-03

This was a fresh read-only pass over all 19 rows in the source-research queue. No GitHub, Artifact Hub, tracker, repository, or project-contact writes were made.

| Repository | Fresh evidence and outcome | Confidence / lifecycle | Local routing |
| --- | --- | --- | --- |
| `banzaicloud-stable` | Artifact Hub packages map to `banzaicloud/banzai-charts`; the registered feed is unreachable and the source is dormant. [Package](https://artifacthub.io/api/v1/packages/helm/banzaicloud-stable/pipeline) · [source](https://github.com/banzaicloud/banzai-charts) | `confirmed-by-repository`; dead endpoint/dormant | disposition |
| `camptocamp` | The tracked `bivac` chart maps to [camptocamp/bivac](https://github.com/camptocamp/bivac), which is active; the old feed is unavailable. [Package](https://artifacthub.io/api/v1/packages/helm/camptocamp/bivac) | `confirmed-by-repository`; active source/stale feed | contact-ready, final preflight required |
| `choerodon` | The live feed and package identity are confirmed, but no current canonical Git publishing source was found; the organization is predominantly archived/dormant. [Package](https://artifacthub.io/api/v1/packages/helm/choerodon/agile-service) · [feed](https://openchart.choerodon.com.cn/choerodon/c7n/index.yaml) | `confirmed-by-index` for feed; `unverified` Git source; retired/dormant | disposition |
| `cleardata` | The tracked `locate` package and ClearDATA contact are confirmed, but the registered feed is dead and no public source repository was found. [Package](https://artifacthub.io/api/v1/packages/helm/cleardata/locate) | `confirmed-by-package`; dead endpoint | disposition |
| `cronce` | The feed is live but multi-chart; `billet` is confirmed, while the inventory row cannot be reduced to one source or chart identity. [Package](https://artifacthub.io/api/v1/packages/helm/cronce/billet) · [feed](https://charts.cronce.io/index.yaml) | `unverified` tracked-row provenance | source research |
| `datawire` | The tracked `ambassador` listing points to the renamed Emissary successor, which publishes a different current chart; treat the historical listing as successor-ambiguous. [Package](https://artifacthub.io/packages/helm/datawire/ambassador) · [successor](https://github.com/emissary-ingress/emissary) | `confirmed-by-index`; retired/renamed listing | disposition |
| `dragonchain` | The exact `dragonchain-k8s` chart source is [dragonchain/dragonchain](https://github.com/dragonchain/dragonchain), but the feed is 404 and the source is dormant. [Package](https://artifacthub.io/packages/helm/dragonchain/dragonchain-k8s) | `confirmed-by-repository`; dormant/dead feed | disposition |
| `fermosit` | The Harbor feed is multi-tenant and contains unrelated charts; the tracked chart identity remains unresolved. [Feed](https://harbor.fermosit.es/chartrepo/library/index.yaml) | `unverified`; stale multi-tenant feed | source research |
| `gomods` | The historical `athens-proxy` listing maps to the active successor publishing repository [gomods/athens-charts](https://github.com/gomods/athens-charts), not `gomods/athens`. [Package](https://artifacthub.io/packages/helm/gomods/athens-proxy) | `confirmed-by-repository`; active successor | contact-ready, final preflight required |
| `gp42` | The exact `calico-aws` package is dormant and has no publishing source repository; only a personal account is associated. [Package](https://artifacthub.io/packages/helm/gp42/calico-aws) | `unverified`; dormant | disposition |
| `k8s-land` | The `gitea` chart maps to [k8s-land/charts](https://github.com/k8s-land/charts), but the registered feed is 404 and the source is dormant. [Package](https://artifacthub.io/packages/helm/k8s-land/gitea) | `confirmed-by-repository`; dead endpoint/dormant | disposition |
| `kremers` | `vmware-exporter` maps to [kremers/charts-vmware-exporter](https://github.com/kremers/charts-vmware-exporter), while `postgresql-ha` has mixed Bitnami provenance; the feed is stale. [Feed](https://kremers.github.io/index.yaml) | `confirmed-by-repository` with mixed provenance; dormant | disposition/source clarification |
| `larribas` | `airflow` and `mlflow` map to [larribas/helm-charts](https://github.com/larribas/helm-charts), but the registered feed is 404 and the source is dormant. [Source index](https://raw.githubusercontent.com/larribas/helm-charts/master/index.yaml) | `confirmed-by-repository`; stale/dead feed | disposition |
| `microsoft` | The feed is live at [microsoft.github.io/charts/repo](https://microsoft.github.io/charts/repo/index.yaml), but the four tracked charts have mixed project sources and ownership. [Repository](https://github.com/microsoft/charts) | `confirmed-by-repository` for feed; mixed chart provenance | source research |
| `mirusresearch` | No current Artifact Hub packages or valid `mirusresearch/charts` source were found; `powerdns-helmchart` is only an unverified candidate. [Search](https://artifacthub.io/api/v1/packages/search?repo=mirusresearch&limit=20) | `unverified`; stale/dead historical row | disposition |
| `opsdroid` | The package and active `opsdroid/opsdroid` project are confirmed, but the project contains no visible Helm chart path and the feed DNS is unavailable. [Package](https://artifacthub.io/packages/helm/opsdroid/opsdroid) | high package/lifecycle confidence; medium source confidence | source research |
| `purestorage` | No current package, feed, or valid `purestorage/helm-charts` source was found; the organization remains active. [Historical source](https://github.com/purestorage/helm-charts) | high dead-source confidence; historical disposition unresolved | disposition |
| `softonic` | The tracked `crossplane-softonic-factory` package is confirmed within a large multi-chart feed, but it has no source or maintainer metadata. [Package](https://artifacthub.io/packages/helm/softonic/crossplane-softonic-factory) | high package/feed confidence; low-medium source confidence | source research |
| `trickster` | The historical Helm-owned package is distinct from the verified AppsCode package; the original source migrated to OCI through `trickstercache/helm-charts`. [Helm package](https://artifacthub.io/packages/helm/trickster/trickster) · [AppsCode package](https://artifacthub.io/packages/helm/appscode/trickster) | high package distinction; medium transfer eligibility | source research |

The resulting local partition is `76` contacted/awaiting/claimed, `46` disposition, `6` source research, `5` contact-blocked, `2` contact-ready, and `1` no-outreach-needed, totaling `136`. The two contact-ready rows require a separate final preflight and explicit approval before any outreach. The research pass itself authorizes no external write.

### Source-Research Final Routing: 2026-08-03

The final read-only pass rechecked the remaining six source-research rows. No external writes were made.

| Repository | Final evidence | Routing |
| --- | --- | --- |
| `cronce` | The `billet` package and live feed are confirmed, but package/feed metadata has no source, home, or canonical chart repository. `mike@cronce.io` is personal rather than project-owned. [Package](https://artifacthub.io/api/v1/packages/helm/cronce/billet) · [feed](https://charts.cronce.io/index.yaml) | Remain source research; canonical source and project-owned contact are unresolved. |
| `fermosit` | The live Harbor feed is multi-tenant and contains unrelated packages with no unique tracked chart/source mapping. Only personal contact evidence is available. [Search](https://artifacthub.io/api/v1/packages/search?repo=fermosit&limit=60) · [feed](https://harbor.fermosit.es/chartrepo/library/index.yaml) | Remain source research; tracked chart identity and owner are unresolved. |
| `microsoft` | Four packages are confirmed, but provenance is mixed across Microsoft/Azure repositories; the cognitive-services chart lacks source mapping. The central chart repository's issue path is restricted. [Feed](https://microsoft.github.io/charts/repo/index.yaml) · [repository](https://github.com/microsoft/charts) | Remain source research; chart-specific provenance and writable contact are unresolved. |
| `opsdroid` | The package feed identifies the active project and its project-owned publishing repository [opsdroid/helm-chart](https://github.com/opsdroid/helm-chart), which has Issues enabled. [Package](https://github.com/opsdroid/helm-chart) · [feed](https://raw.githubusercontent.com/opsdroid/helm-chart/gh-pages/index.yaml) | Move to contact-ready; final Artifact Hub identity and duplicate-request preflight required. |
| `softonic` | The tracked `crossplane-softonic-factory` package is confirmed in an active multi-chart feed, but no source, maintainer, or chart-specific project contact is identified. [Package](https://artifacthub.io/packages/helm/softonic/crossplane-softonic-factory) · [feed](https://charts.softonic.io/index.yaml) | Remain source research; chart source and owner are unresolved. |
| `trickster` | The historical Helm-owned listing is distinct from the verified AppsCode listing. Its original source moved to [trickstercache/helm-charts](https://github.com/trickstercache/helm-charts) and then OCI; the project has a writable issue channel. [Historical package](https://artifacthub.io/packages/helm/trickster/trickster) · [AppsCode package](https://artifacthub.io/packages/helm/appscode/trickster) | Move to contact-ready; final preflight must identify the historical Helm-owned listing explicitly. |

The current local partition is `76` contacted/awaiting/claimed, `46` disposition, `4` source research, `5` contact-blocked, `4` contact-ready, and `1` no-outreach-needed, totaling `136`. The four remaining source-research rows have explicit evidence blockers and should not be forced into disposition or outreach without new evidence.

### Contact-Ready Final Preflight: 2026-08-03

The four contact-ready candidates were rechecked read-only for current Artifact Hub identity, source/feed mapping, lifecycle, writable project-owned contact, and duplicate ownership requests. No external writes were made.

| Repository | Artifact Hub identity | Contact destination | Preflight result |
| --- | --- | --- | --- |
| `camptocamp` | Package `bivac`, ID `85775314-ab09-4364-9801-d72a77a52091`; repository `camptocamp`, ID `10d7b0bd-b670-4928-8020-e882d07fd029`; owner `helm`; current version `1.0.0`. [Package](https://artifacthub.io/api/v1/packages/helm/camptocamp/bivac) | [camptocamp/bivac Issues](https://github.com/camptocamp/bivac/issues) | Was contact-ready at preflight. The historical feed is unavailable, so the posted message states that Artifact Hub maps the listing to `camptocamp/bivac` and asks the project to claim or clarify disposition. No duplicate request found. |
| `gomods` | Package `athens-proxy`, ID `b52a88f2-199a-4a43-81a4-5d74c336abff`; repository `gomods`, ID `499993e8-5c7d-4909-b95f-0090fcae774d`; owner `helm`; current version `0.5.2`. [Package](https://artifacthub.io/api/v1/packages/helm/gomods/athens-proxy) | [gomods/athens-charts Issues](https://github.com/gomods/athens-charts/issues) | Was contact-ready at preflight and is now contacted/awaiting. The historical Azure feed and current `gomods/athens-charts` publishing path are reconciled. PR [#14](https://github.com/gomods/athens-charts/pull/14) is unrelated to ownership transfer. |
| `opsdroid` | Package `opsdroid`, ID `8b369cbc-0f0e-40ab-b477-486d3e1af0ff`; repository `opsdroid`, ID `e5b8386e-c41a-44e9-ac6c-c6fbbcf98e42`; owner `helm`; current version `0.1.11`. [Package](https://artifacthub.io/api/v1/packages/helm/opsdroid/opsdroid) | [opsdroid/helm-chart Issues](https://github.com/opsdroid/helm-chart/issues) | Was contact-ready at preflight and is now contacted/awaiting. The live publishing feed, chart path, source project, and writable project-owned issue channel were confirmed. No duplicate request found. |
| `trickster` | Historical Helm-owned package ID `4bd97bc5-13ff-4baa-8f7e-4576122726b3`; repository ID `cffc2b94-ed2e-4f72-bc0d-99a0bfaa17ca`; owner `helm`; version `1.5.4`. The separate AppsCode package is independently owned and is not the target. [Historical package](https://artifacthub.io/packages/helm/trickster/trickster) · [AppsCode package](https://artifacthub.io/packages/helm/appscode/trickster) | [trickstercache/helm-charts Issues](https://github.com/trickstercache/helm-charts/issues) | Was contact-ready at preflight and is now contacted/awaiting. The historical source migrated to this project and OCI publication; the posted message explicitly excludes the separate AppsCode listing and asks whether Trickster wants to claim or disposition the historical listing. No duplicate request found. |

#### Approval-Ready Outreach Destinations

No outreach is approved by this preflight. Each request requires separate approval with the exact body below or a revised body.

- `camptocamp`: new issue in [camptocamp/bivac](https://github.com/camptocamp/bivac/issues), title `Artifact Hub ownership transfer for the camptocamp/bivac Helm listing`.
- `gomods`: new issue in [gomods/athens-charts](https://github.com/gomods/athens-charts/issues), title `Artifact Hub ownership transfer for the gomods/athens-proxy Helm listing`.
- `opsdroid`: new issue in [opsdroid/helm-chart](https://github.com/opsdroid/helm-chart/issues), title `Artifact Hub ownership transfer for the opsdroid Helm listing`.
- `trickster`: new issue in [trickstercache/helm-charts](https://github.com/trickstercache/helm-charts/issues), title `Artifact Hub ownership transfer for the historical Helm-owned Trickster listing`.

The final preflight left the partition at `76` contacted/awaiting/claimed, `46` disposition, `4` source research, `5` contact-blocked, `4` contact-ready, and `1` no-outreach-needed. The subsequent approved `camptocamp`, `gomods`, `opsdroid`, and `trickster` outreach moved the current partition to `80` contacted/awaiting/claimed and `0` contact-ready.

#### Exact Outreach Drafts: 2026-08-03

These drafts were approval-only; all four drafts have now been posted and verified.

##### `camptocamp`

Destination: [camptocamp/bivac Issues](https://github.com/camptocamp/bivac/issues)

Title: `Artifact Hub ownership transfer for the camptocamp/bivac Helm listing`

```md
Hello,

I am reaching out about the Artifact Hub repository for the camptocamp Helm charts:

https://artifacthub.io/repositories/helm/camptocamp

Artifact Hub currently lists this repository as owned by `helm`. The tracked package is `bivac`, and Artifact Hub identifies this repository as its source:

https://github.com/camptocamp/bivac

Artifact Hub repository ID: `10d7b0bd-b670-4928-8020-e882d07fd029`
Artifact Hub package ID: `85775314-ab09-4364-9801-d72a77a52091`

The historical Helm feed registered for this listing is no longer available. If the Camptocamp team still maintains the `bivac` chart, please follow Artifact Hub's ownership-claim instructions:

https://artifacthub.io/docs/topics/repositories/#ownership-claim

The claimant should publish an `artifacthub-repo.yml` at the published Helm repository path containing the repository ID and the email address used by the claimant's Artifact Hub account, then complete the ownership claim. Please confirm here after the claim succeeds.

If this listing is no longer maintained or should be removed or disabled instead, please let us know.

Thanks.
```

##### `gomods`

Destination: [gomods/athens-charts Issues](https://github.com/gomods/athens-charts/issues)

Title: `Artifact Hub ownership transfer for the gomods/athens-proxy Helm listing`

```md
Hello,

I am reaching out about the Artifact Hub repository for the gomods Helm charts:

https://artifacthub.io/repositories/helm/gomods

Artifact Hub currently lists this repository as owned by `helm`. The tracked package is `athens-proxy`, and the current publishing repository is:

https://github.com/gomods/athens-charts

The chart is published from `charts/athens-proxy` through:

https://gomods.github.io/athens-charts/

Artifact Hub repository ID: `499993e8-5c7d-4909-b95f-0090fcae774d`
Artifact Hub package ID: `b52a88f2-199a-4a43-81a4-5d74c336abff`

The historical Helm feed was:

https://athens.blob.core.windows.net/charts

If the Athens team still maintains this chart, please follow Artifact Hub's ownership-claim instructions:

https://artifacthub.io/docs/topics/repositories/#ownership-claim

The claimant should publish an `artifacthub-repo.yml` at the published Helm repository path containing the repository ID and the email address used by the claimant's Artifact Hub account, then complete the ownership claim. Please confirm here after the claim succeeds.

If this listing is no longer maintained or should be removed or disabled instead, please let us know.

Thanks.
```

##### `opsdroid`

Destination: [opsdroid/helm-chart Issues](https://github.com/opsdroid/helm-chart/issues)

Title: `Artifact Hub ownership transfer for the opsdroid Helm listing`

```md
Hello,

I am reaching out about the Artifact Hub repository for the opsdroid Helm chart:

https://artifacthub.io/repositories/helm/opsdroid

Artifact Hub currently lists this repository as owned by `helm`. The chart source is:

https://github.com/opsdroid/opsdroid

The Helm chart is published from this repository at `charts/opsdroid`:

https://github.com/opsdroid/helm-chart

The published feed is:

https://raw.githubusercontent.com/opsdroid/helm-chart/gh-pages/index.yaml

Artifact Hub repository ID: `e5b8386e-c41a-44e9-ac6c-c6fbbcf98e42`
Artifact Hub package ID: `8b369cbc-0f0e-40ab-b477-486d3e1af0ff`

If the opsdroid team still maintains this chart, please follow Artifact Hub's ownership-claim instructions:

https://artifacthub.io/docs/topics/repositories/#ownership-claim

The claimant should publish an `artifacthub-repo.yml` at the published Helm repository path containing the repository ID and the email address used by the claimant's Artifact Hub account, then complete the ownership claim. Please confirm here after the claim succeeds.

If this listing is no longer maintained or should be removed or disabled instead, please let us know.

Thanks.
```

##### `trickster`

Destination: [trickstercache/helm-charts Issues](https://github.com/trickstercache/helm-charts/issues)

Title: `Artifact Hub ownership transfer for the historical Helm-owned Trickster listing`

```md
Hello,

I am reaching out about a historical Artifact Hub repository for the Trickster Helm chart:

https://artifacthub.io/packages/helm/trickster/trickster

This specific listing is currently owned by `helm`:

Artifact Hub repository ID: `cffc2b94-ed2e-4f72-bc0d-99a0bfaa17ca`
Artifact Hub package ID: `4bd97bc5-13ff-4baa-8f7e-4576122726b3`

The original Helm source and feed are no longer active. The chart source has since moved to:

https://github.com/trickstercache/helm-charts

The current chart is published through OCI at:

oci://ghcr.io/trickstercache/charts/trickster

This request concerns only the historical `trickster` listing owned by `helm`. It does not concern the separate AppsCode listing:

https://artifacthub.io/packages/helm/appscode/trickster

If the Trickster team still maintains this chart and wants to retain the historical listing, please follow Artifact Hub's ownership-claim instructions:

https://artifacthub.io/docs/topics/repositories/#ownership-claim

The claimant should publish an `artifacthub-repo.yml` containing the historical repository ID and the email address used by the claimant's Artifact Hub account, then complete the ownership claim. Please confirm here after the claim succeeds.

If the historical listing should instead be removed or disabled because the chart moved to OCI, please let us know.

Thanks.
```

All four drafts were separately approved, posted, and verified. Their corresponding public activity-overlay rows and local audit entries are complete.

| 2026-08-03 | Contact-ready final preflight | Rechecked `camptocamp`, `gomods`, `opsdroid`, and `trickster` for Artifact Hub identity, source mapping, lifecycle, contactability, and duplicate requests. | All four were contact-ready and have since been posted and moved to contacted/awaiting. Exact destinations and repository-specific cautions are recorded above. |
| 2026-08-03 | `camptocamp` outreach | Posted the approved ownership-transfer request and appended its same-day activity row. | [camptocamp/bivac#409](https://github.com/camptocamp/bivac/issues/409) was re-fetched and matched the approved body. [Activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) was re-fetched and the rendered row verified. |
| 2026-08-03 | `gomods` outreach | Posted the approved ownership-transfer request and appended its same-day activity row. | [gomods/athens-charts#141](https://github.com/gomods/athens-charts/issues/141) was re-fetched and matched the approved body. [Activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) was re-fetched and the rendered row verified. |
| 2026-08-03 | `opsdroid` outreach | Posted the approved ownership-transfer request and appended its same-day activity row. | [opsdroid/helm-chart#35](https://github.com/opsdroid/helm-chart/issues/35) was re-fetched and matched the approved body. [Activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) was re-fetched and the rendered row verified. |
| 2026-08-03 | `trickster` outreach | Posted the approved ownership-transfer request and appended its same-day activity row. | [trickstercache/helm-charts#34](https://github.com/trickstercache/helm-charts/issues/34) was re-fetched and matched the approved body. [Activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) was re-fetched and the rendered row verified. |

### Posted Public Addenda: 2026-08-03

The following text was appended after the existing `2026-08-03` activity table. It did not modify the original inventory, prior activity sections, or the existing Snyk and Wombat entries.

```md
### Disposition Review

- `banzaicloud-stable`: **Strong evidence for administrator disposition review.** The historical `banzaicloud/banzai-charts` source is dormant and the registered feed is unavailable. No current ownership transfer is proposed; recommend administrator review for disablement or removal of the historical listing. [Artifact Hub package](https://artifacthub.io/api/v1/packages/helm/banzaicloud-stable/pipeline) · [source repository](https://github.com/banzaicloud/banzai-charts)
- `choerodon`: **Strong evidence for dormant/retired-source review.** The registered feed remains reachable but its packages are historical, the latest observed entries date to 2022, and no current canonical Git publishing source was identified. Recommend administrator review for retaining, disabling, or removing the listing; do not transfer by inference. [Artifact Hub package](https://artifacthub.io/api/v1/packages/helm/choerodon/agile-service) · [feed](https://openchart.choerodon.com.cn/choerodon/c7n/index.yaml)
- `cleardata`: **Strong evidence for dead-endpoint review.** The tracked `locate` package is identified, but the registered feed is unavailable and no public chart source repository was found. Recommend administrator review for disablement or removal; no ownership outreach is proposed. [Artifact Hub package](https://artifacthub.io/api/v1/packages/helm/cleardata/locate) · [registered feed](https://helm.cleardata.com/index.yaml)
- `datawire`: **Strong evidence for successor reconciliation.** The historical `ambassador` listing points to the renamed Emissary successor, which publishes a different current chart. Recommend administrator reconciliation or removal of the historical listing; do not transfer it to the successor by inference. [Artifact Hub package](https://artifacthub.io/packages/helm/datawire/ambassador) · [successor](https://github.com/emissary-ingress/emissary)
- `dragonchain`: **Strong evidence for stale-listing review.** The exact `dragonchain-k8s` source is [dragonchain/dragonchain](https://github.com/dragonchain/dragonchain), but the registered feed is unavailable and the source is dormant. Recommend administrator review for disablement or removal; no normal ownership outreach is proposed. [Artifact Hub package](https://artifacthub.io/packages/helm/dragonchain/dragonchain-k8s)
- `gp42`: **Moderate evidence for dormant-source review.** The `calico-aws` package is historical and no publishing source repository or project-owned maintainer channel was identified. Recommend administrator review rather than ownership outreach. [Artifact Hub package](https://artifacthub.io/packages/helm/gp42/calico-aws) · [feed](https://ops42.org/helm-charts/index.yaml)
- `k8s-land`: **Strong evidence for dead-endpoint review.** The `gitea` chart maps to [k8s-land/charts](https://github.com/k8s-land/charts), but the registered feed is unavailable and the source is dormant. Recommend administrator review for disablement or removal; do not pursue normal outreach. [Artifact Hub package](https://artifacthub.io/packages/helm/k8s-land/gitea) · [registered feed](https://charts.k8s.land/index.yaml)
- `kremers`: **Moderate evidence for source-identity reconciliation.** The feed contains `vmware-exporter` from [kremers/charts-vmware-exporter](https://github.com/kremers/charts-vmware-exporter), while `postgresql-ha` has mixed Bitnami provenance and the feed is dormant. Require chart-by-chart reconciliation before any transfer; do not contact based on the mixed feed alone. [feed](https://kremers.github.io/index.yaml)
- `larribas`: **Strong evidence for stale-feed review.** The `airflow` and `mlflow` charts map to [larribas/helm-charts](https://github.com/larribas/helm-charts), but the registered feed is unavailable and the source is dormant. Recommend administrator review for disablement or removal before any transfer request. [source index](https://raw.githubusercontent.com/larribas/helm-charts/master/index.yaml)
- `mirusresearch`: **Strong evidence for historical-listing review.** No current Artifact Hub packages or valid `mirusresearch/charts` source were found. A separate `powerdns-helmchart` repository is only an unverified candidate. Recommend administrator review; do not contact the candidate repository by inference. [Artifact Hub search](https://artifacthub.io/api/v1/packages/search?repo=mirusresearch&limit=20) · [missing source](https://github.com/mirusresearch/charts) · [candidate](https://github.com/mirusresearch/powerdns-helmchart)
- `purestorage`: **Strong evidence for historical-source review.** No current Artifact Hub package, feed, or valid `purestorage/helm-charts` source was found. Recommend administrator review for disablement or removal if the historical listing remains present; no ownership outreach is proposed. [historical source](https://github.com/purestorage/helm-charts) · [Pure Storage organization](https://github.com/purestorage)

These are recommendations for maintainer review only. No Artifact Hub administrator request has been made.

### Research Findings and Contact Status

The following rows remain unresolved after read-only research. No outreach is proposed until the stated evidence gaps are resolved.

| Repository | Current finding | Next step |
| --- | --- | --- |
| `cronce` | The `billet` package and feed are live, but package/feed metadata provides no canonical source or project-owned maintainer contact. | Identify the chart source and an authoritative owner before outreach. [Package](https://artifacthub.io/api/v1/packages/helm/cronce/billet) · [feed](https://charts.cronce.io/index.yaml) |
| `fermosit` | The Harbor feed is multi-tenant and contains unrelated packages; the tracked inventory row cannot be mapped to one chart or owner. | Reconcile the tracked chart identity before any contact. [Search](https://artifacthub.io/api/v1/packages/search?repo=fermosit&limit=60) · [feed](https://harbor.fermosit.es/chartrepo/library/index.yaml) |
| `microsoft` | Four packages share the listing but map to different Microsoft/Azure projects; one chart lacks source mapping and the central issue path is restricted. | Resolve chart-by-chart provenance and a writable owner channel. [feed](https://microsoft.github.io/charts/repo/index.yaml) · [repository](https://github.com/microsoft/charts) |
| `softonic` | The active `crossplane-softonic-factory` package has no source, maintainer, or chart-specific owner metadata; related Softonic repositories are not sufficient evidence. | Identify the publishing source and owning team before outreach. [Package](https://artifacthub.io/packages/helm/softonic/crossplane-softonic-factory) · [feed](https://charts.softonic.io/index.yaml) |

The following current contact blockers have no valid public project-owned outreach path established:

| Repository | Blocker |
| --- | --- |
| `fold` | The source is active, but issue creation is restricted and only private support channels were found. |
| `ibm-charts` | IBM's contribution guidance excludes the published `stable` directory from GitHub contributions; no valid public metadata path was established. |
| `lifen` | The source repository is archived and GitHub rejected issue creation; no durable public project-maintainer channel was found. |
| `owkin` | The source repository is archived and GitHub rejected issue creation; no durable public project-maintainer channel was found. |
| `ruguodangshi` | The source is an inactive fork with Issues and Discussions disabled; no authoritative project-owned channel was established. |

These blocker notes describe current evidence and do not request private or restricted outreach. The `snyk` support request and `wombat` no-outreach reconciliation are already recorded in the dated activity history and are unchanged here.
```

### Historical Tracker Formatting Proposal: 2026-08-03

The original `2026-07-23` activity section contains a separate `Disposition Decisions Requested` table. The proposal is to replace only that table with the addendum-style bullets used by the later tracker sections. No repository decisions, links, prior dated sections, inventory rows, or summary counts would change.

**Destination:** [activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580)

**Current block to replace:**

```md
### Disposition Decisions Requested

| Repository | Contact | Decision needed |
| --- | --- | --- |
| appdynamics | [CiscoDevNet/appdynamics-charts#47](https://github.com/CiscoDevNet/appdynamics-charts/issues/47) | Repoint and transfer the disabled listing, or remove it. |
| buildkite | [buildkite/charts#110](https://github.com/buildkite/charts/issues/110) | Transfer the deprecated legacy listing, or disable or remove it. |
| cgroschupp | [cgroschupp/helm-charts#1](https://github.com/cgroschupp/helm-charts/issues/1) | Transfer the inactive listing, or disable or remove it. |
| chubaofs | [cubefs/cubefs-helm#60](https://github.com/cubefs/cubefs-helm/issues/60) | Retain the disabled historical listing, or remove it. |
| cloudwatch-agent | [s2504s/charts#1](https://github.com/s2504s/charts/pull/1) | Transfer the stale listing, or disable or remove it. |
```

**Proposed replacement:**

```md
### Disposition Decisions Requested

- `appdynamics`: **Decision needed.** Repoint and transfer the disabled listing, or remove it. [Contact](https://github.com/CiscoDevNet/appdynamics-charts/issues/47)
- `buildkite`: **Decision needed.** Transfer the deprecated legacy listing, or disable or remove it. [Contact](https://github.com/buildkite/charts/issues/110)
- `cgroschupp`: **Decision needed.** Transfer the inactive listing, or disable or remove it. [Contact](https://github.com/cgroschupp/helm-charts/issues/1)
- `chubaofs`: **Decision needed.** Retain the disabled historical listing, or remove it. [Contact](https://github.com/cubefs/cubefs-helm/issues/60)
- `cloudwatch-agent`: **Decision needed.** Transfer the stale listing, or disable or remove it. [Contact](https://github.com/s2504s/charts/pull/1)
```

The approved replacement was posted to [activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) on 2026-08-03. The old table is gone, the five addendum bullets are present, the `2026-08-03` section remains present, and no other tracker content was changed. No inventory rows or summary counts changed.

### Audit Log Addition: 2026-08-03

| Date | Scope | Completed work | Evidence and result |
| --- | --- | --- | --- |
| 2026-08-03 | Historical disposition formatting repair | Replaced only the old `2026-07-23` disposition table with equivalent addendum-style bullets. | [Activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) was re-fetched and verified: the old table is absent, all five bullets are present, and the later `2026-08-03` section remains intact. |
| 2026-08-03 | Research and blocker addenda | Appended the 11 new disposition recommendations plus the four unresolved research blockers and five contact blockers to the current dated activity section. | [Activity comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580) was re-fetched and verified. The erroneous duplicate five-item disposition block from the initial append attempt was removed during repair; the final comment contains one such block and the approved research/contact addendum. |
| 2026-08-03 | Tracker comment recovery | Restored the activity comment from GitHub's content-edit history after a faulty append replaced the body, then reapplied the approved addendum. | The exact pre-truncation version from `2026-08-03T17:44:35Z` was recovered. The final comment preserves the historical sections, all same-day outreach rows, and the approved disposition/research/contact addendum; rendered section boundaries were re-fetched and verified. |

### Tracker Markdown Write Incident: 2026-08-10

The 2026-08-10 activity append temporarily broke the public activity comment formatting. The update used `gh api --input` with process substitution; GitHub received the serialized JSON document as the comment body instead of receiving an object whose `body` field contained the Markdown. The raw comment therefore began with a literal quote and escaped `\\n` sequences, and GitHub rendered the complete Markdown payload as text rather than headings and tables.

The comment was repaired by decoding the extra JSON layer and sending a correctly formed request body through standard input. Verification confirmed that the rendered comment contains an `h1`, dated `h2` headings, and rendered tables, including the `2026-08-10` section.

Prevention rules:

- Never use process substitution with `gh api --input` for Markdown comment updates.
- Build the request as `jq -n --arg body "$body" '{body: $body}'` and pipe it to `gh api --input -`.
- Before treating a write as complete, inspect both the raw API body for a leading Markdown heading and the rendered `body_html` for expected headings and table elements.
- Preserve the pre-write body and restore it from the saved exact content if verification detects JSON quoting, escaped newlines, missing headings, missing tables, or truncation.

### Recent Incoming Updates: 2026-08-04 through 2026-08-23

These updates were recorded in the public activity overlay; no issue-body changes were made.

| Date | Repository | Evidence and current state |
| --- | --- | --- |
| 2026-08-04 | `kuberhealthy` | The maintainer updated the registered Artifact Hub URL to `https://kuberhealthy.github.io/kuberhealthy/helm-repos` and confirmed that the ownership metadata is present. Artifact Hub verification remains pending. [Issue comment](https://github.com/kuberhealthy/kuberhealthy/issues/1523#issuecomment-5172837450) |
| 2026-08-04 | `astarte` | The team confirmed completion of the ownership claim. Artifact Hub reports the repository under `astarte-platform` with `verified_publisher: true`. [Issue comment](https://github.com/astarte-platform/astarte-kubernetes-operator/issues/596#issuecomment-5179605506) |
| 2026-08-04 | `sstarcher` | The maintainer added the ownership metadata and is waiting for Artifact Hub to update. [Issue comment](https://github.com/sstarcher/helm-exporter/issues/209#issuecomment-5171604278) |
| 2026-08-05 | `keel` | Maintainer `@rusenask` merged [PR #878](https://github.com/keel-hq/keel/pull/878), adding and publishing the ownership metadata. Artifact Hub still reports Helm ownership. [Issue event](https://github.com/keel-hq/keel/issues/864#event-29008555546) |
| 2026-08-06 | `smallstep` | [PR #270](https://github.com/smallstep/helm-charts/pull/270) merged and the metadata is accessible at `https://smallstep.github.io/helm-charts/artifacthub-repo.yml`. Artifact Hub now reports repository `227e7c9c-4ae2-4ba4-ae05-68fa006d87c0` under the `smallstep` organization. [Latest issue comment](https://github.com/smallstep/helm-charts/issues/266#issuecomment-5222236009) |
| 2026-08-11 | `smallstep` | Helm confirmed that the ownership-transfer issue is fully fixed. | [Issue comment](https://github.com/smallstep/helm-charts/issues/266#issuecomment-5255558355); Artifact Hub continues to report repository `227e7c9c-4ae2-4ba4-ae05-68fa006d87c0` under the `smallstep` organization. |
| 2026-08-23 | `kuberhealthy` | The project automation confirmed that the ownership metadata remains live at `https://kuberhealthy.github.io/kuberhealthy/helm-repos/artifacthub-repo.yml` and returns HTTP 200. No repository-side changes remain; the Artifact Hub claim still needs to be completed or confirmed. `Claimed` remains unset. [Issue comment](https://github.com/kuberhealthy/kuberhealthy/issues/1523#issuecomment-5386950696) |

### Incoming Update: 2026-08-10

The Prometheus MSTeams maintainer asked whether the historical Artifact Hub listing can be removed because the chart is published through GitHub Container Registry. Another Helm response is already present in the thread, so no additional response was posted. The repository remains `Replied`; `Claimed` is unset; await an explicit retain-or-remove decision before any disposition request.

Artifact Hub currently reports the Prometheus MSTeams repository as Helm-owned:

- Repository ID: `04862194-6d5a-4896-97f3-8cd88b1d685b`
- Package: `prometheus-msteams` `1.3.6`

Artifact Hub now reports Smallstep repository `227e7c9c-4ae2-4ba4-ae05-68fa006d87c0` under the `smallstep` organization. This supports `Replied` and `Claimed`; no further outreach is needed. The issue-body inventory update remains blocked by GitHub repository-admin permissions.

| Date | Scope | Completed work | Evidence and result |
| --- | --- | --- | --- |
| 2026-08-10 | Incoming ownership and disposition updates | Reviewed the latest Prometheus MSTeams and Smallstep responses and appended the approved activity-overlay update. | [Prometheus MSTeams](https://github.com/prometheus-msteams/prometheus-msteams/issues/440#issuecomment-5237276490) remains replied and awaits a terminal decision; [Smallstep](https://github.com/smallstep/helm-charts/issues/266#issuecomment-5222236009) is claimed according to live Artifact Hub data. The Smallstep inventory edit returned GitHub `403: Must have admin rights to Repository`. |

### Inventory Reconciliation: 2026-08-10

A fresh read-only fetch of issue #428 found exactly `136` inventory rows: `86` in the identified-source section and `50` in the source-unknown section. The live `smallstep` row still has `Replied` and `Resolved` unchecked because the issue-body update returned GitHub `403: Must have admin rights to Repository`. No other inventory rows were changed during this pass.

### Audit Log Addition: 2026-08-18

| Date | Scope | Completed work | Evidence and result |
| --- | --- | --- | --- |
| 2026-08-18 | AWS ownership metadata update | Reviewed the merged AWS EKS charts pull request adding Artifact Hub ownership metadata to the published `gh-pages` feed. | [aws/eks-charts#1360](https://github.com/aws/eks-charts/pull/1360) merged on 2026-08-17 and publishes `https://aws.github.io/eks-charts/artifacthub-repo.yaml` with AWS owner emails. Artifact Hub still reports repository `0ea9a8e1-751f-4ed6-a333-7052cf004900` under `helm`; `Replied` is supportable, but `Claimed` remains unrecorded. No public tracker or external follow-up was made. |

### Audit Log Addition: 2026-08-19

| Date | Scope | Completed work | Evidence and result |
| --- | --- | --- | --- |
| 2026-08-19 | AWS ownership claim confirmation | Recorded the AWS maintainer’s confirmation that the Artifact Hub ownership claim succeeded. | [aws/eks-charts#1290 comment 5336824735](https://github.com/aws/eks-charts/issues/1290#issuecomment-5336824735) confirms “looks like it worked!” Ownership metadata is published at `https://aws.github.io/eks-charts/artifacthub-repo.yaml`. The live Artifact Hub API still returns repository `0ea9a8e1-751f-4ed6-a333-7052cf004900` under `helm`, with `verified_publisher: false`; no replacement repository ID currently exists. `Claimed` is supportable from maintainer confirmation, while Artifact Hub propagation remains pending. |

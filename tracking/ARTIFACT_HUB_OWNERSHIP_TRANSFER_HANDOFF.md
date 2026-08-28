# Artifact Hub Ownership Transfer Handoff

Last updated: `2026-08-24`

This handoff is the restart point for the Artifact Hub ownership-transfer work tracked in [helm/community#428](https://github.com/helm/community/issues/428).

## Source Of Truth

- Public inventory: [helm/community#428](https://github.com/helm/community/issues/428)
- Public activity overlay: [issue comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580)
- Detailed local plan: `ARTIFACT_HUB_OWNERSHIP_TRANSFER_PLAN.md`
- The issue body remains maintainer-owned. The activity overlay records only repositories contacted or materially changed; it does not replace the 136-row inventory.

## Current Position

- Inventory size: `136` repositories.
- Current queue partition: `80` contacted/awaiting/claimed, `46` disposition, `0` lifecycle research, `0` contact-ready, `4` source research, `0` uncontacted Tier 1, `0` Tier 2, `5` contact-blocked, and `1` no outreach needed.
- Queue counts are a local provisional partition and sum to all `136` rows.
- Public issue-body sections currently parse as 86 identified-source and 50 source-unknown rows. The local plan records intended reclassification separately; do not alter the public inventory without explicit approval and exact row diffs.
- Tier 1 and Tier 2 outreach execution is complete. Current outreach outcomes remain open or awaiting evidence; no new outreach batch is prepared.
- Local disposition research and recommendation text are complete for all 46 disposition entries, and all 46 recommendations are recorded in the public activity overlay. No Artifact Hub administrator request has been made. The `wombat` inventory source correction remains pending because the issue body is maintainer-owned.
- The local plan records all current evidence, confidence levels, next steps, and audit entries. The approved Snyk support request was submitted on 2026-07-31 and is awaiting a human response; no GitHub PR or Artifact Hub action is pending approval.
- All 46 local disposition recommendations and the `wombat` evidence row are now posted in the public activity overlay. The original issue-body source correction for `wombat` was blocked by GitHub `403` permissions and remains maintainer-applied work.
- The public activity overlay now records the 2026-08-10 Prometheus MSTeams question and the Smallstep claim. The Smallstep inventory checkbox update was attempted but remains maintainer-applied work because GitHub returned `403: Must have admin rights to Repository`.

## Outreach Status

- `64` ownership-transfer contacts are recorded: seven complete five-repository batches, one four-repository partial batch, the latest five-repository replacement Tier 1 batch, the first five-repository Tier 2 batch, the two-repository Tier 2 completion batch, the single Talend reclassification request, five source-research ownership requests, one Pomerium Discuss topic, one Ververica email, the t3n ownership request, and the `camptocamp`, `gomods`, `opsdroid`, and `trickster` requests.
- All current outreach requests are awaiting replies or claims unless listed as claimed below.
- The latest five Tier 1 requests are:
  - `agones`: [agones-dev/agones#4667](https://github.com/agones-dev/agones/issues/4667)
  - `influxdata`: [influxdata/helm-charts#816](https://github.com/influxdata/helm-charts/issues/816)
  - `jfrog`: [jfrog/charts#2457](https://github.com/jfrog/charts/issues/2457)
  - `kanister`: [kanisterio/kanister#4149](https://github.com/kanisterio/kanister/issues/4149)
  - `rancher-stable`: [rancher/rancher#56325](https://github.com/rancher/rancher/issues/56325)

## Confirmed Claims

The following ownership transfers are evidence-backed:

- `camel-k`
- `ceph-csi`
- `concourse`
- `cowboysysop`
- `couchbase`, now owned by the official `couchbase` organization
- `hmdmph`
- `smallstep`, verified by Artifact Hub as owned by the `smallstep` organization
- `sysdiglabs`, verified by Artifact Hub as owned by the `sysdig` organization
- `astarte`, verified by Artifact Hub as owned by the `astarte-platform` organization
- `aws`, supported by maintainer confirmation; Artifact Hub propagation remains pending

`wombat` needs no outreach because ownership is already established outside Helm after source reconciliation.

## Tier 2 Queue

Tier 2 is local prioritization only. Do not add tier labels to the public tracker.

The Tier 2 queue is complete. The first five-candidate batch and the two-repository completion batch were posted after read-only preflight.

## Reason Queues

- `contact-ready`: none. `t3n` was contacted through [issue #214](https://github.com/t3n/helm-charts/issues/214) and awaits a response or claim. `pomerium` was contacted through its Discuss support forum, and `ververica` was contacted by email; both await a response or claim evidence. `snyk` was contacted through the support portal and is awaiting a human response.
- `contact-blocked`: `fold`, `ibm-charts`, `lifen`, `owkin`, and `ruguodangshi`.
- `lifecycle-research`: none; the 2026-07-31 read-only pass completed this queue.
- `disposition`: `appdynamics`, `balle-petersen`, `banzaicloud-stable`, `brannon`, `buildkite`, `cgroschupp`, `choerodon`, `chubaofs`, `cleardata`, `cloudwatch-agent`, `crate`, `dacruz21`, `datawire`, `dragonchain`, `enapter`, `eventstore`, `flink-operator`, `forseti-security`, `fyipe`, `gp42`, `gradiant`, `infobloxopen`, `inspur`, `k8s-dashboard`, `kiwigrid`, `kremers`, `kubedex`, `larribas`, `mirusresearch`, `monocular`, `pangeo`, `pfisterer-knox`, `pl-helm-charts`, `purestorage`, `quarks`, `redsky`, `smueller18`, `soluto`, `squidex`, `stardog`, `uswitch`, `volcano`, `vertigo`, `waldur`, and `wavefront`.
- `no-outreach-needed`: `wombat`.
- `source-research`: `cronce`, `fermosit`, `microsoft`, and `softonic`. These 4 rows still lack sufficient chart-source or owner reconciliation; do not contact or force them into disposition without new evidence.
- `deferred`: none currently; `crate` is now disposition-oriented because the project requested Artifact Hub removal.

## Special Cases

- `kuberhealthy`: the maintainer updated the registered URL to `https://kuberhealthy.github.io/kuberhealthy/helm-repos`; the published ownership metadata is live at `https://kuberhealthy.github.io/kuberhealthy/helm-repos/artifacthub-repo.yml` and returns HTTP 200. No repository-side changes remain; the maintainer still needs to complete or confirm the Artifact Hub ownership claim. Do not mark `Claimed` yet. [Latest update](https://github.com/kuberhealthy/kuberhealthy/issues/1523#issuecomment-5386950696)
- `prometheus-msteams`: the maintainer asked whether the historical Artifact Hub listing should be removed because charts are now published through GitHub Container Registry. No Helm response has been posted because another Helm response is already present; await an explicit retain-or-remove decision.
- `ibm-charts`: IBM's contribution guidance excludes the `stable` directory from GitHub contributions; do not use a PR for the Artifact Hub metadata.
- `snyk`: the approved support request was submitted through Snyk's support channel and received an automated receipt. No ticket number, maintainer identity, claimant email, or ownership evidence was provided; do not prepare or post a PR until a human response identifies the claimant.
- `runix`: [rowanruseler/helm-charts#351](https://github.com/rowanruseler/helm-charts/issues/351) is an open ownership-transfer request with no reply or claim evidence. The feed and source are independently verified; do not open duplicate outreach or post a reminder.
- `astarte`: the team added ownership metadata to the published feed and confirmed the claim at [issue comment 5179605506](https://github.com/astarte-platform/astarte-kubernetes-operator/issues/596#issuecomment-5179605506). Artifact Hub now reports the repository under the `astarte-platform` organization with `verified_publisher: true`; `Claimed` is supported.
- `lifen` and `owkin`: GitHub issue creation was rejected because their source repositories are archived; no project-owned writable channel was identified. Do not treat attempted issue creation as outreach.
- `sysdiglabs`: fully claimed; no maintainer follow-up is needed.
- `pomerium`: [Discuss topic](https://discuss.pomerium.com/t/artifact-hub-ownership-claim-for-the-pomerium-helm-repository/513) was posted; no reply or claim evidence yet.
- `ververica`: the approved email was sent to `platform@ververica.com`; no receipt, reply, or claim evidence yet.
- `talend`: Talend replied in [Talend/helm-charts-public#57](https://github.com/Talend/helm-charts-public/issues/57#issuecomment-5140935144), so `Replied` is supported. The claim-versus-removal decision remains pending; Helm's later `needs-response` follow-up does not replace Talend's reply.
- `crossplane`: Maintainer [@jbw976](https://github.com/jbw976) acknowledged the request and said they will attempt to claim the repository for the Crossplane organization. `Replied` is supported; `Claimed` remains unrecorded. No Helm response is needed.
- `sstarcher`: the maintainer added the ownership metadata and is waiting for Artifact Hub to update. `Replied` is supported; `Claimed` remains unrecorded.
- `keel`: maintainer [@rusenask](https://github.com/rusenask) merged [PR #878](https://github.com/keel-hq/keel/pull/878), which adds and publishes the ownership metadata. Artifact Hub still reports Helm ownership; `Claimed` remains unrecorded.
- `smallstep`: [PR #270](https://github.com/smallstep/helm-charts/pull/270) merged and the metadata is accessible at `https://smallstep.github.io/helm-charts/artifacthub-repo.yml`. Artifact Hub now reports repository `227e7c9c-4ae2-4ba4-ae05-68fa006d87c0` under the `smallstep` organization; `Replied` and `Claimed` are supported. Scott confirmed on 2026-08-11 that the issue is fully fixed. The issue-body checkbox update remains maintainer-applied work.
- `aws`: [aws/eks-charts#1290 comment 5336824735](https://github.com/aws/eks-charts/issues/1290#issuecomment-5336824735) confirms the maintainer successfully claimed the Artifact Hub repository. Ownership metadata is published at `https://aws.github.io/eks-charts/artifacthub-repo.yaml`. Artifact Hub still reports repository `0ea9a8e1-751f-4ed6-a333-7052cf004900` under `helm`, with `verified_publisher: false`; retain the existing ID until Artifact Hub propagates the ownership change.

## Tracker Rules

- Keep all same-day repository changes in one dated table in the existing activity overlay section.
- Use one optional addendum after that table for explanatory notes or blockers.
- Mention `@scottrigby` at most once in the dated addendum, never once per batch or repository.
- Do not create public Tier 1/Tier 2 columns or separate public batch sections.
- Do not duplicate the full inventory in the activity overlay.
- Update `Contacted`, `Replied`, and `Claimed` only from durable evidence.
- Request approval before any new external write, showing exact destinations and content.
- Every outreach posting must include the corresponding public activity-tracker update and local audit-log entry.
- Keep local prioritization labels, including `Tier 1` and `Tier 2`, out of all public GitHub content; use them only in local tracking.
- After every GitHub write, re-fetch and verify the rendered Markdown formatting, table structure, line breaks, links, and content; repair any formatting failure before treating the write as complete.
- Follow-up responses are allowed only when another party responded and appears to need information or action from Helm (`needs-response`), or when Helm is the latest responder and that response is more than one month old (`stale-latest-response`).
- Ask for approval before posting every follow-up response. Include its category, a review link to the exact thread, the proposed destination, and the exact response text. Do not post routine reminders automatically.

## Next Actions

Existing outreach monitoring is passive background work: the current contacted queue should be processed only when durable replies, claims, redirects, or terminal outcomes arrive.

Proceed in this order:

1. Monitor current outreach for durable responses, claims, redirects, or terminal outcomes.
2. Prepare exact Artifact Hub administrator requests for disposition items only after maintainer review and approval.
3. Recheck the 5 contact-blocked rows and 4 source-research rows only when new evidence or a durable project-owned channel appears.
4. Have an issue maintainer apply the `wombat` source correction in the public inventory; its no-outreach evidence is already recorded.
5. Update the public inventory only with exact row diffs, then reconcile all 136 rows and summary counts.

Do not open a new Tier 1 or Tier 2 population unless new evidence creates a distinct candidate set. Tier labels remain local-only.

Do not assume that a repository is an outreach candidate merely because it is Helm-owned. Revalidate source, lifecycle, contactability, and duplicate requests immediately before any new outreach.

## Restart Checkpoint

Use this section as the current restart point. Historical queue counts and intermediate plans remain below in the detailed plan; the current partition above takes precedence.

- Current local partition: `80` contacted/awaiting/claimed, `46` disposition, `4` source research, `5` contact-blocked, `0` contact-ready, and `1` no-outreach-needed, totaling `136`.
- Confirmed claims: `astarte`, `aws`, `camel-k`, `ceph-csi`, `concourse`, `cowboysysop`, `couchbase`, `hmdmph`, `smallstep`, and `sysdiglabs`.
- Public activity overlay: [issue comment 5061350580](https://github.com/helm/community/issues/428#issuecomment-5061350580). It includes the t3n request, all 46 disposition recommendations, the current research/contact-blocker addendum, and the `wombat` no-outreach evidence row.
- Public inventory: [issue #428](https://github.com/helm/community/issues/428). A fresh read-only parse found `86` identified-source and `50` source-unknown rows across all `136` rows. The `wombat` source remains malformed, and the `smallstep` Replied/Resolved fields remain stale in the main table because updating the issue body returned GitHub `403: Must have admin rights to Repository`.
- Local source of truth: `ARTIFACT_HUB_OWNERSHIP_TRANSFER_PLAN.md` contains the evidence, proposed diffs, queue rationale, and audit entries. Both local documents are currently untracked and have not been committed.
- Next priority: monitor the four newly posted ownership requests and the existing contacted queue. The remaining 4 source-research rows have explicit blockers; no outreach is authorized for them.
- After source research: recheck the `5` contact-blocked rows for durable project-owned channels. Do not use private forms or restricted channels without separate approval.
- Passive monitoring: await responses or claims from current outreach, especially t3n, Snyk, Pomerium, Ververica, and the existing contacted queue.
- No Artifact Hub administrator request is approved or pending. Any new tracker, project, Artifact Hub, or support write requires an exact destination and content review first.

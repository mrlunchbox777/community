# Approval packets — 2026-08-28

These drafts are review-only. Nothing in this file authorizes sending or submitting an Artifact Hub administrator request.

## Contact drafts

All five charts are published through the Softonic Artifact Hub repository:

- Repository URL: https://artifacthub.io/repositories/helm/softonic
- Artifact Hub repository ID: `47e3cc7f-4fe5-4457-b8d4-aa9701b2eeae`
- Feed: https://charts.softonic.io/

### `go-ratelimit`

- Destination: https://github.com/softonic/go-ratelimit-chart/issues
- Proposed title: `[Artifact Hub] Claim ownership of the go-ratelimit Helm repository`

```md
Hello,

I am reaching out about the Artifact Hub repository for the Softonic go-ratelimit Helm chart:

https://artifacthub.io/packages/helm/softonic/go-ratelimit

Artifact Hub repository ID: `47e3cc7f-4fe5-4457-b8d4-aa9701b2eeae`

Helm currently receives notifications for this listing. The validated Helm repository is:

https://charts.softonic.io/

The publishing source is:

https://github.com/softonic/go-ratelimit-chart

The chart packages the Envoy Rate Limit service; this request concerns ownership of the Softonic Helm chart and its Artifact Hub listing, not ownership of the upstream Envoy project.

If the Softonic team still maintains this repository, please follow Artifact Hub's ownership-claim instructions:

https://artifacthub.io/docs/topics/repositories/#ownership-claim

The claimant should publish an `artifacthub-repo.yml` file at the published Helm repository path containing this repository ID and the email address used by the claimant's Artifact Hub account. Please confirm here after the claim succeeds.

If Softonic is no longer responsible for this chart, please redirect us to the current owner or team contact.

Thanks.
```

### `ip-blocker`

- Destination: https://github.com/softonic/ip-blocker/issues
- Proposed title: `[Artifact Hub] Claim ownership of the ip-blocker Helm repository`

Use the standard body above, with:

- Artifact Hub package: https://artifacthub.io/packages/helm/softonic/ip-blocker
- Publishing source: https://github.com/softonic/ip-blocker
- Chart-specific note: this is a Softonic project chart; no upstream chart owner was identified.

### `kubewatch`

- Destination: https://github.com/softonic/kubewatch-chart/issues
- Proposed title: `[Artifact Hub] Claim ownership of the kubewatch Helm repository`

Use the standard body above, with:

- Artifact Hub package: https://artifacthub.io/packages/helm/softonic/kubewatch
- Publishing source: https://github.com/softonic/kubewatch-chart
- Application source: https://github.com/softonic/kubewatch
- Chart-specific note: this concerns the Softonic chart and packaged Softonic application, not unrelated upstream Kubewatch projects.

### `redis-sharded`

- Destination: https://github.com/softonic/redis-sharded-chart/issues
- Proposed title: `[Artifact Hub] Claim ownership of the redis-sharded Helm repository`

Use the standard body above, with:

- Artifact Hub package: https://artifacthub.io/packages/helm/softonic/redis-sharded
- Publishing source: https://github.com/softonic/redis-sharded-chart
- Chart-specific note: the chart is Softonic-owned and is loosely based on Bitnami Redis patterns; this is not a transfer request to Bitnami, Redis, or Twitter.

### `varnish`

- Destination: https://github.com/softonic/varnish-chart/issues
- Proposed title: `[Artifact Hub] Claim ownership of the varnish Helm repository`

Use the standard body above, with:

- Artifact Hub package: https://artifacthub.io/packages/helm/softonic/varnish
- Publishing source: https://github.com/softonic/varnish-chart
- Chart-specific note: the chart packages the upstream Varnish image but is maintained as a Softonic chart. Confirm the Artifact Hub version skew (`0.18.9` published versus `0.18.10` in source) before posting.

## Disposition and clarification drafts

### `hierarchical-namespace-controller` — administrator disposition review

- Artifact Hub package: https://artifacthub.io/packages/helm/softonic/hierarchical-namespace-controller
- Artifact Hub repository ID: `47e3cc7f-4fe5-4457-b8d4-aa9701b2eeae`
- Source: https://github.com/softonic/hierarchical-namespace-controller
- Upstream provenance: https://github.com/kubernetes-retired/multi-tenancy
- Proposed action: review for disablement/removal or historical retention. Do not transfer to the retired upstream project by inference.
- Proposed administrator request:

```md
Subject: Administrator review requested for the historical hierarchical-namespace-controller listing

Please review the Artifact Hub package `softonic/hierarchical-namespace-controller`:

https://artifacthub.io/packages/helm/softonic/hierarchical-namespace-controller

Artifact Hub repository ID: `47e3cc7f-4fe5-4457-b8d4-aa9701b2eeae`

The published chart source is https://github.com/softonic/hierarchical-namespace-controller and packages HNC v0.8.0. The upstream Kubernetes multi-tenancy project is retired/read-only, and the Softonic chart is historical. Please determine whether the listing should be retained as historical, disabled, or removed. No ownership transfer to the retired upstream project is requested.
```

### `kube-gcp-disks-roomba` — administrator disposition review

- Artifact Hub package: https://artifacthub.io/packages/helm/softonic/kube-gcp-disks-roomba
- Artifact Hub repository ID: `47e3cc7f-4fe5-4457-b8d4-aa9701b2eeae`
- Source: https://github.com/softonic/kube-gcp-disks-roomba-chart
- Proposed action: review stale historical listing; do not infer current ownership from the archived activity.
- Proposed administrator request:

```md
Subject: Administrator review requested for the historical kube-gcp-disks-roomba listing

Please review the Artifact Hub package `softonic/kube-gcp-disks-roomba`:

https://artifacthub.io/packages/helm/softonic/kube-gcp-disks-roomba

Artifact Hub repository ID: `47e3cc7f-4fe5-4457-b8d4-aa9701b2eeae`

The published chart source is https://github.com/softonic/kube-gcp-disks-roomba-chart. The latest indexed release is historical and the package shows no recent operational activity. Please determine whether the listing should be retained, disabled, or removed. No ownership transfer is requested without confirmation of a current owner.
```

### Microsoft `spark` — administrator/owner clarification

- Artifact Hub package: https://artifacthub.io/packages/helm/microsoft/spark
- Proposed destination: Microsoft Charts project-owned channel, destination to be approved before posting: https://github.com/microsoft/charts
- Proposed action: ask Microsoft to confirm retain, archive, retire, or successor handling. Do not transfer to Apache Spark or Kubeflow by inference.

```md
Subject: Clarify ownership and lifecycle of the Microsoft Spark Helm listing

Hello,

The Helm project is reviewing the Artifact Hub package:

https://artifacthub.io/packages/helm/microsoft/spark

The package is a legacy Microsoft-hosted chart with its last indexed release from 2020 and Apache Spark 2.4.4 application content. The Microsoft chart index remains available, but the chart source points to historical material rather than a current Microsoft product repository.

Could the Microsoft Charts team confirm whether this listing should be retained, archived, retired, or associated with a maintained successor? Please do not redirect ownership to Apache Spark, Kubeflow, or Bitnami without confirming the ownership and lifecycle of this specific chart artifact.

Thanks.
```

### Microsoft Speech — owner/support clarification

- Artifact Hub package: https://artifacthub.io/packages/helm/microsoft/cognitive-services-speech-onpremise
- Package ID: `75320d89-f85d-43c7-8db5-bffb71e26c6f`
- Proposed destination: Microsoft Charts project-owned channel, destination to be approved before posting: https://github.com/microsoft/charts
- Proposed action: clarify chart support/ownership and whether a maintained chart successor exists. Do not mark the package formally retired solely because the chart is stale; current Microsoft documentation still references the Speech product.

```md
Subject: Clarify ownership and support status of the Microsoft Speech Helm chart

Hello,

The Helm project is reviewing the Artifact Hub package:

https://artifacthub.io/packages/helm/microsoft/cognitive-services-speech-onpremise

Artifact Hub package ID: `75320d89-f85d-43c7-8db5-bffb71e26c6f`

The latest indexed Helm chart release is 0.3.3 from 2021, while current Microsoft documentation continues to reference Azure Speech in Foundry Tools On-Premises and the Microsoft Helm chart name. Please confirm whether this chart remains supported, should be archived or retired, or has a maintained successor chart/source.

This request concerns the lifecycle and ownership of the Helm chart artifact. It does not infer that current Speech container images imply current Helm chart support.

Thanks.
```

## Preflight before any send

1. Re-fetch each package and repository record.
2. Confirm the current Softonic feed and source URL.
3. Check for duplicate/open requests in each destination repository.
4. Confirm the exact destination for the two Microsoft clarification requests and the Artifact Hub administrator route for disposition requests.
5. Obtain approval for each exact destination and message.
6. After sending, read back each public issue or email and append only terse status rows to the existing Helm tracker activity comment.

# Approval-Ready Outreach Drafts

These drafts follow the established Seldon-style ownership-transfer template. They are pending approval and have not been sent.

Every draft includes the exact Artifact Hub repository URL and ID, why Helm currently receives notifications, the validated source/feed, claim instructions, confirmation request, and redirect request.

## `fold`

- Destination: [fold-team/helm-charts issues](https://github.com/fold-team/helm-charts/issues), pending approval.
- Proposed title: `[Artifact Hub] Claim ownership of the fold Helm repository`
- Proposed body:

```md
Hello,

I am reaching out about the Artifact Hub repository for the Fold Helm charts:

https://artifacthub.io/repositories/helm/fold

Artifact Hub repository ID: `52cfb567-b05e-43ac-9513-bc19916314a4`

Helm currently receives notifications for this listing. The validated Helm repository is:

https://charts.foldapp.com

The publishing source is:

https://github.com/fold-team/helm-charts

If the Fold team still maintains this repository, please follow Artifact Hub's ownership-claim instructions:

https://artifacthub.io/docs/topics/repositories/#ownership-claim

The claimant should publish an `artifacthub-repo.yml` file at the published Helm repository path containing this repository ID and the email address used by the claimant's Artifact Hub account. Please confirm here after the claim succeeds.

If Fold is no longer responsible for this repository, please redirect us to the current owner or team contact.

Thanks.
```

## `ibm-charts`

- Destination: [IBM/charts pull requests](https://github.com/IBM/charts/pulls), pending approval and confirmation that a pull-request-channel inquiry is acceptable under IBM's contribution guidance.
- Proposed title: `[Artifact Hub] Claim ownership of the ibm-charts Helm repository`
- Proposed body:

```md
Hello,

I am reaching out about the Artifact Hub repository for the IBM Helm charts:

https://artifacthub.io/repositories/helm/ibm-charts

Artifact Hub repository ID: `5d25cfa5-d7fc-401f-a7d3-2c7645bd2731`

Helm currently receives notifications for this listing. The validated Helm repository is:

https://raw.githubusercontent.com/IBM/charts/master/repo/stable/

The publishing source is:

https://github.com/IBM/charts

If the IBM charts team still maintains this repository, please follow Artifact Hub's ownership-claim instructions:

https://artifacthub.io/docs/topics/repositories/#ownership-claim

The claimant should publish an `artifacthub-repo.yml` file at the published Helm repository path containing this repository ID and the email address used by the claimant's Artifact Hub account. Please confirm here after the claim succeeds.

If IBM is no longer responsible for this repository, please redirect us to the current owner or team contact.

Thanks.
```

## `ruguodangshi`

- Destination: [ruguodangshi/ruguodangshi.github.io issues](https://github.com/ruguodangshi/ruguodangshi.github.io/issues), pending approval.
- Proposed title: `[Artifact Hub] Claim ownership of the ruguodangshi Helm repository`
- Proposed body:

```md
Hello,

I am reaching out about the Artifact Hub repository for the ruguodangshi Helm charts:

https://artifacthub.io/repositories/helm/ruguodangshi

Artifact Hub repository ID: `42b801c1-e15a-420d-808b-72029d2b340d`

Helm currently receives notifications for this listing. The validated Helm repository is:

https://ruguodangshi.github.io

The publishing source is:

https://github.com/ruguodangshi/ruguodangshi.github.io

If you still maintain this repository, please follow Artifact Hub's ownership-claim instructions:

https://artifacthub.io/docs/topics/repositories/#ownership-claim

The claimant should publish an `artifacthub-repo.yml` file at the published Helm repository path containing this repository ID and the email address used by the claimant's Artifact Hub account. Please confirm here after the claim succeeds.

If you are no longer responsible for this repository, please redirect us to the current owner or team contact.

Thanks.
```

## `cronce`

- Destination: `helm@cronce.io`, pending approval.
- Proposed subject: `Artifact Hub ownership claim for the cronce Helm repository`
- Proposed message:

```md
Hello,

I am reaching out about the Artifact Hub repository for the Cronce Helm charts:

https://artifacthub.io/repositories/helm/cronce

Artifact Hub repository ID: `d114f871-b924-4c9f-8252-01152107cc1d`

Helm currently receives notifications for this listing. The validated Helm repository is:

https://charts.cronce.io/

The publishing source is:

https://github.com/mcronce/charts

If the Cronce team still maintains this repository, please follow Artifact Hub's ownership-claim instructions:

https://artifacthub.io/docs/topics/repositories/#ownership-claim

The claimant should publish an `artifacthub-repo.yml` file at the published Helm repository path containing this repository ID and the email address used by the claimant's Artifact Hub account. Please confirm here after the claim succeeds.

The feed contains multiple charts, including charts that appear to repackage upstream software. Please also identify any charts that should be redirected to an upstream owner or retired rather than treated as Cronce-owned.

If Cronce is no longer responsible for this repository, please redirect us to the current owner or team contact.

Thanks.
```

## Final preflight requirements

Before any posting or sending:

1. Re-fetch each Artifact Hub repository record and check for an existing claim or duplicate request.
2. Confirm the exact destination and whether the repository's own contribution rules permit the proposed channel.
3. Re-check the feed/source URLs and repository IDs.
4. Obtain approval for the exact destination and exact message.
5. After posting, read back the public thread and record the durable URL in the Gitea activity log.

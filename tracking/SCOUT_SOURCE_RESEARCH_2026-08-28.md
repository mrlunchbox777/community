## Fresh read-only research pass

- Retrieved and parsed `https://charts.softonic.io/index.yaml`; verified **61 distinct chart entries**.[1]
- Downloaded each latest chart archive and inspected `Chart.yaml` metadata where the index omitted source fields.
- Queried Artifact Hub’s public package API for both Microsoft packages.[2][3]
- Checked Microsoft’s chart repository, `sources.yaml`, repository state, commit history, and current Speech documentation.[4][5][6][7]
- No external records, comments, issues, messages, or repositories were modified. No contacts were contacted.

## Softonic: 61-chart reconciliation

Classification is based on chart metadata, source URLs, chart archive contents, public repository evidence, and naming. “Upstream-repackaged” means the chart metadata directly identifies an external project/repository; “unresolved” means the available public metadata does not establish ownership strongly enough.

| Group | Count | Charts | Evidence / durable contact |
|---|---:|---|---|
| **Clearly Softonic-owned** | **7** | `gar-exporter`, `gcp-quota-exporter`, `homing-pigeon`, `laravel`, `mysql-backup`, `pagespeed-exporter`, `sft-new-digitaltrends` | `gar-exporter`, `gcp-quota-exporter`, `mysql-backup`, and `pagespeed-exporter` point to `github.com/softonic/...`; `laravel` and `sft-new-digitaltrends` point to Softonic Bitbucket projects; Homing Pigeon is linked to `softonic/homing-pigeon` and its chart repository.[1][8][9][10][11][12][13] Durable contacts: the corresponding repository issue pages and the Softonic GitHub/Bitbucket project, rather than individual maintainer email addresses. |
| **Internal / factory** | **4** | `crossplane-softonic-factory`, `csi-gcs-softonic-factory`, `tools-softonic-factory`, `workflows-softonic-factory` | The chart names and descriptions explicitly identify Softonic factory/template packages; `workflows-softonic-factory` also carries the Softonic Bitbucket source.[1] Durable contact: the owning Softonic source project/team; no public project-owned contact was exposed for the three charts without source URLs. |
| **Upstream-repackaged / externally attributable** | **31** | `artifact-hub`, `cost-analyzer`, `crossplane`, `docker-registry`, `dragonfly`, `eck-elasticsearch`, `eck-kibana`, `eck-operator`, `external-dns`, `external-secrets`, `harbor`, `hello-world-app`, `ingress-nginx`, `keda`, `keycloak`, `kibana`, `kube-prometheus-stack`, `kyverno`, `kyverno-policies`, `logstash`, `oauth2-proxy`, `policy-reporter`, `preemptible-killer`, `prometheus-thanos`, `redis-operator`, `sealed-secrets`, `sealed-secrets-web`, `service-level-operator`, `sorry-cypress`, `trivy-operator`, `webhook-receiver` | The index or packaged `Chart.yaml` identifies the upstream project, such as Kubecost, Crossplane, Elastic, Bitnami/Broadcom, Harbor, Kubernetes, KEDA, Prometheus Community, Kyverno, Elastic, or the respective upstream repositories.[1] Durable contacts should be the upstream project repository/team, not Softonic. |
| **Unresolved / ownership not established** | **19** | `cilium-mesh`, `go-ratelimit`, `hierarchical-namespace-controller`, `infinispan`, `ip-blocker`, `istio-gateway`, `istio-sidecar`, `keda-operator`, `knative-serving`, `kube-gcp-disks-roomba`, `kubewatch`, `node-policy-webhook`, `pod-defaulter`, `rate-limit-operator`, `rclone`, `redis`, `redis-sharded`, `sloth-service-levels`, `varnish` | Current chart metadata has no sufficiently identifying `sources`/`home` field. Some have strong Softonic-repository candidates—for example `go-ratelimit-chart`, `kubewatch-chart`, `hierarchical-namespace-controller`, `knative-serving-chart`, `redis-sharded-chart`, and `varnish-chart`—but this pass did not establish a one-to-one chart-to-repository mapping for every item.[14][15][16][17][18] |

**Count check:** 7 + 4 + 31 + 19 = **61**.

### Softonic ownership observations

- The strongest durable ownership evidence is repository-level, not the personal maintainer emails embedded in older chart metadata.
- Confirmed public Softonic project contacts include:
  - `https://github.com/softonic/gar-exporter`
  - `https://github.com/softonic/gcp-quota-exporter-helm-chart`
  - `https://github.com/softonic/mysql-backup-chart`
  - `https://github.com/softonic/pagespeed-exporter-chart`
  - `https://github.com/softonic/homing-pigeon-chart`
  - `https://github.com/softonic/homing-pigeon`
  - `https://github.com/softonic/go-ratelimit-chart`
  - `https://github.com/softonic/varnish-chart`
  - `https://github.com/softonic/redis-sharded-chart`
  - `https://github.com/softonic/kubewatch-chart`
  - `https://github.com/softonic/hierarchical-namespace-controller`
  - `https://github.com/softonic/knative-serving-chart`
- These candidate repositories should be used for the next verification pass, but the unresolved group should not be promoted solely from name similarity.

## Microsoft `spark`

| Field | Finding | Confidence |
|---|---|---|
| Artifact Hub package | `https://artifacthub.io/packages/helm/microsoft/spark` | High |
| Repository/feed | Artifact Hub repository `microsoft`, feed `https://microsoft.github.io/charts/repo/` | High |
| Current Artifact Hub version | **1.0.4**, application version **2.4.4**, released **3 July 2020**; only versions 1.0.4 and 1.0.0 are indexed.[2] | High |
| Source links | Kubernetes Spark example, Apache Spark, and Azure ML Spark Docker images: `https://github.com/kubernetes/kubernetes/tree/master/examples/spark`, `https://github.com/apache/spark`, `https://github.com/Azure/mmlspark/tree/master/tools/helm/docker_images`.[2] | High |
| Ownership/lifecycle | This is a Microsoft-hosted feed entry for a chart based on Helm Classic and Azure/MMLSpark images, not a current Apache Spark project chart. Microsoft’s `sources.yaml` maps `spark` to `dbanda/charts`, not to a current Microsoft product repository.[5] | High |
| Current successor evidence | Current alternatives include upstream Apache Spark deployment documentation and maintained third-party charts such as Bitnami Spark; no Microsoft successor chart was found. | Medium |
| Durable contact | `https://github.com/microsoft/charts` repository/issues; the repository remains public and unarchived, but its chart content is substantially stale.[4][6] | High |

**Recommended disposition:** `upstream-repackaged / retired-feed candidate`; queue for **Microsoft chart-feed retirement verification**, not direct ownership transfer to Apache Spark without confirming whether the chart is still intentionally supported.

## Microsoft `cognitive-services-speech-onpremise`

| Field | Finding | Confidence |
|---|---|---|
| Artifact Hub package | `https://artifacthub.io/packages/helm/microsoft/cognitive-services-speech-onpremise` | High |
| Exact Artifact Hub package ID | `75320d89-f85d-43c7-8db5-bffb71e26c6f`.[3] | High |
| Repository/feed | Artifact Hub repository `microsoft`, feed `https://microsoft.github.io/charts/repo/` | High |
| Current Artifact Hub version | **0.3.3**, released **22 June 2021**; indexed versions are 0.3.3, 0.2.0, and 0.1.1.[3] | High |
| Chart content | Umbrella chart for Speech-to-Text and Text-to-Speech, with local dependencies `speechToText` and `textToSpeech` at 0.2.0.[3] | High |
| Source/lifecycle signal | Microsoft’s old feed index contains only the original 0.1.0 entry, while Artifact Hub retains later packages. No corresponding chart archive commit was found in the Microsoft repository history for 0.3.3.[5][6] | High |
| Current documentation | Microsoft’s current documentation still references the same chart/feed and install name, but describes it as the **Azure Speech in Foundry Tools On-Premises Chart** and was updated **30 January 2026**.[7] | High |
| Successor / retirement evidence | No separate successor chart repository or new Artifact Hub package was found. Current docs still point at the old `microsoft/cognitive-services-speech-onpremise` name, creating a lifecycle/documentation mismatch. | High |
| Durable contact | Microsoft chart repository/issues and Microsoft Speech documentation feedback/edit path; do not rely on the historical `antsu@microsoft.com` maintainer address. | High |

**Recommended disposition:** `Microsoft-owned legacy chart; successor unclear`. Queue for **Microsoft Speech product-owner verification**. Do not mark fully retired based solely on the 2021 package age because current Microsoft documentation still actively references the chart/feed.

## Recommended queue assignments

1. **Softonic-confirmed ownership queue**
   - 7 clearly Softonic-owned charts.
   - Use repository-level contacts and ownership evidence.
2. **Softonic factory/internal queue**
   - 4 explicitly factory-named charts.
   - Resolve through the internal Softonic source projects; public ownership evidence is insufficient for three of four.
3. **Upstream transfer / repackaged queue**
   - 31 charts with identifiable upstream projects.
   - Route to the upstream project repository/team, preserving the distinction between Softonic’s feed and upstream ownership.
4. **Softonic source-resolution queue**
   - 19 unresolved charts.
   - Prioritize one-to-one verification for `go-ratelimit`, `hierarchical-namespace-controller`, `knative-serving`, `kubewatch`, `redis-sharded`, and `varnish`, where public Softonic repository candidates exist.
5. **Microsoft Spark queue**
   - Treat as stale Microsoft-hosted feed content with no current Microsoft successor found.
   - Verify retirement/transfer policy before assigning to Apache Spark or Bitnami.
6. **Microsoft Speech queue**
   - Escalate as a lifecycle mismatch: Artifact Hub’s latest package is from 2021, but Microsoft’s current documentation still references the chart.
   - Seek confirmation of current support or an undocumented replacement before closing as retired.

## Unresolved cases

- Ownership remains unproven for the 19 source-less Softonic charts listed above.
- `spark` has no confirmed Microsoft successor and no explicit retirement notice located.
- `cognitive-services-speech-onpremise` has current documentation references but no clearly published successor feed/package; the chart may be legacy-but-supported, documentation-stale, or distributed through an undocumented internal process.

### Sources

[1] https://charts.softonic.io/index.yaml  
[2] https://artifacthub.io/api/v1/packages/helm/microsoft/spark  
[3] https://artifacthub.io/api/v1/packages/helm/microsoft/cognitive-services-speech-onpremise  
[4] https://github.com/microsoft/charts  
[5] https://raw.githubusercontent.com/microsoft/charts/gh-pages/sources.yaml  
[6] https://api.github.com/repos/microsoft/charts  
[7] https://learn.microsoft.com/en-us/azure/ai-services/speech-service/speech-container-howto-on-premises  
[8] https://github.com/softonic/homing-pigeon-chart  
[9] https://github.com/softonic/homing-pigeon  
[10] https://github.com/softonic/gar-exporter  
[11] https://github.com/softonic/gcp-quota-exporter-helm-chart  
[12] https://github.com/softonic/mysql-backup-chart  
[13] https://github.com/softonic/pagespeed-exporter-chart  
[14] https://github.com/softonic/charts-bitnami  
[15] https://github.com/softonic/go-ratelimit-chart  
[16] https://github.com/softonic/varnish-chart  
[17] https://github.com/softonic/redis-sharded-chart  
[18] https://github.com/softonic/kubewatch-chart  
[19] https://github.com/softonic/hierarchical-namespace-controller  
[20] https://github.com/softonic/knative-serving-chart  
[21] https://github.com/softonic/helm-webhook-receiver
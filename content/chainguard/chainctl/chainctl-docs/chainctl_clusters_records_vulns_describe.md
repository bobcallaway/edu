---
date: 2023-07-18T12:25:34Z
title: "chainctl clusters records vulns describe"
slug: chainctl_clusters_records_vulns_describe
url: /chainguard/chainctl/chainctl-docs/chainctl_clusters_records_vulns_describe/
draft: false
tags: ["chainctl", "Reference", "Product"]
images: []
type: "article"
toc: true
---
## chainctl clusters records vulns describe

Describe the CVEs from the cluster vulnerability report.

```
chainctl clusters records vulns describe CLUSTER_NAME|CLUSTER_ID --image=IMAGE [--cve=CVE,CVE,...] [--min-severity=LOW|MEDIUM|HIGH|CRITICAL] [--fix-states=STATE,STATE,... (STATE=UNKNOWN|FIXED|NOT_FIXED|WONT_FIX)] [--active-within=DURATION] [--output table|json|wide]
```

### Options

```
      --active-within duration   How recently a vuln must have been active to be listed. Zero will return all vulns. (default 24h0m0s)
      --cve strings              A comma separated list of CVEs to filter the results.
      --fix-states strings       A comman separated list of vulnerability fix states to return (UNKNOWN, FIXED, NOT_FIXED, WONT_FIX).
  -h, --help                     help for describe
      --image string             The name of an image or regular expression to filter the results.
      --min-severity string      The lowest level of severity vulnerability return (one of LOW, MEDIUM, HIGH, CRITICAL).
```

### Options inherited from parent commands

```
      --api string                   The url of the Chainguard platform API. (default "https://console-api.enforce.dev")
      --audience string              The Chainguard token audience to request. (default "https://console-api.enforce.dev")
      --config string                A specific chainctl config file.
      --console string               The url of the Chainguard platform Console. (default "https://console.enforce.dev")
      --issuer string                The url of the Chainguard STS endpoint. (default "https://issuer.enforce.dev")
  -o, --output string                Output format. One of: ["", "table", "tree", "json", "id", "wide"]
      --timestamp-authority string   The url of the Chainguard Timestamp Authority endpoint. (default "https://tsa.enforce.dev")
  -v, --v int                        Set the log verbosity level.
```

### SEE ALSO

* [chainctl clusters records vulns](/chainguard/chainctl/chainctl-docs/chainctl_clusters_records_vulns/)	 - Interact with cluster records vulnerabilities.


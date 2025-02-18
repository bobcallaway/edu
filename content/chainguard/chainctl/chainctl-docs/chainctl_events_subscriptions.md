---
date: 2023-07-18T12:25:34Z
title: "chainctl events subscriptions"
slug: chainctl_events_subscriptions
url: /chainguard/chainctl/chainctl-docs/chainctl_events_subscriptions/
draft: false
tags: ["chainctl", "Reference", "Product"]
images: []
type: "article"
toc: true
---
## chainctl events subscriptions

Subscription interactions.

### Options

```
  -h, --help   help for subscriptions
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

* [chainctl events](/chainguard/chainctl/chainctl-docs/chainctl_events/)	 - Events related commands for the Chainguard platform.
* [chainctl events subscriptions create](/chainguard/chainctl/chainctl-docs/chainctl_events_subscriptions_create/)	 - Subscribe to events under a group.
* [chainctl events subscriptions delete](/chainguard/chainctl/chainctl-docs/chainctl_events_subscriptions_delete/)	 - Delete a subscription.
* [chainctl events subscriptions list](/chainguard/chainctl/chainctl-docs/chainctl_events_subscriptions_list/)	 - List subscriptions.


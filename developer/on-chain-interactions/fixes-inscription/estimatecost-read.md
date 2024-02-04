---
description: Estimate current inscribing cost
---

# EstimateCost - read

#### Script parameters

<table><thead><tr><th width="130" align="center">Key</th><th width="108" data-type="checkbox">Required</th><th width="100" align="center">FType</th><th>Description</th></tr></thead><tbody><tr><td align="center">mimeType</td><td>true</td><td align="center">t.String</td><td>for  𝔉rc20 use "text/plain"</td></tr><tr><td align="center">data</td><td>true</td><td align="center">t.String</td><td>the data string of each inscription</td></tr><tr><td align="center">protocol</td><td>true</td><td align="center">t.String</td><td>for 𝔉rc20 use "frc20"</td></tr></tbody></table>

#### Code example

```typescript
import scEstimateCost from "@fixes/contracts/scripts/estimate-cost.cdc?raw";

async function estimateInscriptionCost(data: string) {
  return await flowSrv.executeScript(
      scEstimateCost,
      (arg, t) => [
        arg("text/plain", t.String),
        arg(data, t.String),
        arg("frc20", t.String),
      ],
      "0.001"
    );
}
```

#### Script source code

{% @github-files/github-code-block url="https://github.com/fixes-world/fixes/blob/main/cadence/scripts/estimate-cost.cdc" %}

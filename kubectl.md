
1. Get versions of `images` for set of `deployments`
```bash
k get deployment -o=jsonpath="{range .items[*]}{'\n'}{.metadata.name}{': '}{range .spec.template.spec.containers[*]}{.image},{end}{end}" | grep rebate | sort | awk -F':' '{print $1 " - "  $3}'      <aws:main>

## OUTPUT:
rebate-accrual-calculator-worker - release-2021.4-timeout-extend.6,
rebate-api - release-2021.4-timeout-extend.6,
rebate-calculator-worker - release-2021.4-timeout-extend.6,
rebate-dataaggregator-worker - release-2021.4-timeout-extend.6,
rebate-message-publisher - release-2021.4-timeout-extend.6,
rebate-orchestrator-worker - release-2021.4-timeout-extend.6,
rebate-payment-worker - release-2021.4-timeout-extend.6,
rebate-product-calculator-worker - release-2021.4-timeout-extend.6,

```
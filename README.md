<!-- Warning: Do not manually edit this file. See notes on gluon + helm-docs at the end of this file for more information. -->
# gateway

![Version: 1.25.1-bb.3](https://img.shields.io/badge/Version-1.25.1--bb.3-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.25.1](https://img.shields.io/badge/AppVersion-1.25.1-informational?style=flat-square) ![Maintenance Track: bb_integrated](https://img.shields.io/badge/Maintenance_Track-bb_integrated-green?style=flat-square)

Helm chart for deploying Istio gateways

## Upstream References

- <https://github.com/istio/istio>

## Upstream Release Notes

- [Find our upstream chart's CHANGELOG here](https://istio.io/latest/news/releases/)

## Learn More

- [Application Overview](docs/overview.md)
- [Other Documentation](docs/)

## Pre-Requisites

- Kubernetes Cluster deployed
- Kubernetes config installed in `~/.kube/config`
- Helm installed

Install Helm

https://helm.sh/docs/intro/install/

## Deployment

- Clone down the repository
- cd into directory

```bash
helm install gateway chart/
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| mtls.mode | string | `"STRICT"` | STRICT = Allow only mutual TLS traffic, PERMISSIVE = Allow both plain text and mutual TLS traffic |
| networkPolicies.enabled | bool | `true` |  |
| networkPolicies.additionalPolicies | list | `[]` |  |
| gateway.servers[0].hosts[0] | string | `"*.dev.bigbang.mil"` |  |
| gateway.servers[0].port.name | string | `"http"` |  |
| gateway.servers[0].port.number | int | `8080` |  |
| gateway.servers[0].port.protocol | string | `"HTTP"` |  |
| gateway.servers[0].tls.httpsRedirect | bool | `true` |  |
| gateway.servers[1].hosts[0] | string | `"*.dev.bigbang.mil"` |  |
| gateway.servers[1].port.name | string | `"https"` |  |
| gateway.servers[1].port.number | int | `8443` |  |
| gateway.servers[1].port.protocol | string | `"HTTPS"` |  |
| gateway.servers[1].tls.credentialName | string | `"public-cert"` |  |
| gateway.servers[1].tls.mode | string | `"SIMPLE"` |  |
| upstream.name | string | `""` |  |
| upstream.revision | string | `""` |  |
| upstream.replicaCount | string | `nil` |  |
| upstream.kind | string | `"Deployment"` |  |
| upstream.rbac.enabled | bool | `true` |  |
| upstream.serviceAccount.create | bool | `true` |  |
| upstream.serviceAccount.annotations | object | `{}` |  |
| upstream.serviceAccount.name | string | `""` |  |
| upstream.podAnnotations."prometheus.io/port" | string | `"15020"` |  |
| upstream.podAnnotations."prometheus.io/scrape" | string | `"true"` |  |
| upstream.podAnnotations."prometheus.io/path" | string | `"/stats/prometheus"` |  |
| upstream.podAnnotations."inject.istio.io/templates" | string | `"gateway"` |  |
| upstream.podAnnotations."sidecar.istio.io/inject" | string | `"true"` |  |
| upstream.securityContext | object | `{}` |  |
| upstream.containerSecurityContext | object | `{}` |  |
| upstream.service.type | string | `"LoadBalancer"` |  |
| upstream.service.ports[0].name | string | `"tcp-status-port"` |  |
| upstream.service.ports[0].port | int | `15021` |  |
| upstream.service.ports[0].protocol | string | `"TCP"` |  |
| upstream.service.ports[0].targetPort | int | `15021` |  |
| upstream.service.ports[1].name | string | `"http2"` |  |
| upstream.service.ports[1].port | int | `80` |  |
| upstream.service.ports[1].protocol | string | `"TCP"` |  |
| upstream.service.ports[1].targetPort | int | `8080` |  |
| upstream.service.ports[2].name | string | `"https"` |  |
| upstream.service.ports[2].port | int | `443` |  |
| upstream.service.ports[2].protocol | string | `"TCP"` |  |
| upstream.service.ports[2].targetPort | int | `8443` |  |
| upstream.service.annotations | object | `{}` |  |
| upstream.service.loadBalancerIP | string | `""` |  |
| upstream.service.loadBalancerSourceRanges | list | `[]` |  |
| upstream.service.externalTrafficPolicy | string | `""` |  |
| upstream.service.externalIPs | list | `[]` |  |
| upstream.service.ipFamilyPolicy | string | `""` |  |
| upstream.service.ipFamilies | list | `[]` |  |
| upstream.resources.requests.cpu | string | `"100m"` |  |
| upstream.resources.requests.memory | string | `"128Mi"` |  |
| upstream.resources.limits.cpu | string | `"2000m"` |  |
| upstream.resources.limits.memory | string | `"1024Mi"` |  |
| upstream.autoscaling.enabled | bool | `true` |  |
| upstream.autoscaling.minReplicas | int | `1` |  |
| upstream.autoscaling.maxReplicas | int | `5` |  |
| upstream.autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| upstream.autoscaling.targetMemoryUtilizationPercentage | object | `{}` |  |
| upstream.autoscaling.autoscaleBehavior | object | `{}` |  |
| upstream.env | object | `{}` |  |
| upstream.strategy | object | `{}` |  |
| upstream.minReadySeconds | string | `nil` |  |
| upstream.readinessProbe | object | `{}` |  |
| upstream.labels."istio.io/dataplane-mode" | string | `"none"` |  |
| upstream.labels.istio | string | `"ingressgateway"` |  |
| upstream.annotations | object | `{}` |  |
| upstream.nodeSelector | object | `{}` |  |
| upstream.tolerations | list | `[]` |  |
| upstream.topologySpreadConstraints | list | `[]` |  |
| upstream.affinity | object | `{}` |  |
| upstream.networkGateway | string | `""` |  |
| upstream.imagePullPolicy | string | `""` |  |
| upstream.imagePullSecrets | list | `[]` |  |
| upstream.podDisruptionBudget | object | `{}` |  |
| upstream.terminationGracePeriodSeconds | int | `30` |  |
| upstream.volumes | list | `[]` |  |
| upstream.volumeMounts | list | `[]` |  |
| upstream.priorityClassName | string | `""` |  |

## Contributing

Please see the [contributing guide](./CONTRIBUTING.md) if you are interested in contributing.

---

_This file is programatically generated using `helm-docs` and some BigBang-specific templates. The `gluon` repository has [instructions for regenerating package READMEs](https://repo1.dso.mil/big-bang/product/packages/gluon/-/blob/master/docs/bb-package-readme.md)._


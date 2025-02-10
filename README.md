<!-- Warning: Do not manually edit this file. See notes on gluon + helm-docs at the end of this file for more information. -->
# gateway

![Version: 1.23.3-bb.2](https://img.shields.io/badge/Version-1.23.3--bb.2-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.23.3](https://img.shields.io/badge/AppVersion-1.23.3-informational?style=flat-square) ![Maintenance Track: bb_integrated](https://img.shields.io/badge/Maintenance_Track-bb_integrated-green?style=flat-square)

Helm chart for deploying Istio gateways

## Upstream References

- <https://github.com/istio/istio>

## Upstream Release Notes

- [Find our upstream chart's CHANGELOG here](https://istio.io/latest/news/releases/1.23.2/announcing-1.23.2)

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
| defaults.name | string | `""` |  |
| defaults.revision | string | `""` |  |
| defaults.replicaCount | string | `nil` |  |
| defaults.kind | string | `"Deployment"` |  |
| defaults.rbac.enabled | bool | `true` |  |
| defaults.serviceAccount.create | bool | `true` |  |
| defaults.serviceAccount.annotations | object | `{}` |  |
| defaults.serviceAccount.name | string | `""` |  |
| defaults.podAnnotations."prometheus.io/port" | string | `"15020"` |  |
| defaults.podAnnotations."prometheus.io/scrape" | string | `"true"` |  |
| defaults.podAnnotations."prometheus.io/path" | string | `"/stats/prometheus"` |  |
| defaults.podAnnotations."inject.istio.io/templates" | string | `"gateway"` |  |
| defaults.podAnnotations."sidecar.istio.io/inject" | string | `"true"` |  |
| defaults.securityContext | object | `{}` |  |
| defaults.containerSecurityContext | object | `{}` |  |
| defaults.service.type | string | `"LoadBalancer"` |  |
| defaults.service.ports[0].name | string | `"tcp-status-port"` |  |
| defaults.service.ports[0].port | int | `15021` |  |
| defaults.service.ports[0].protocol | string | `"TCP"` |  |
| defaults.service.ports[0].targetPort | int | `15021` |  |
| defaults.service.ports[1].name | string | `"http2"` |  |
| defaults.service.ports[1].port | int | `80` |  |
| defaults.service.ports[1].protocol | string | `"TCP"` |  |
| defaults.service.ports[1].targetPort | int | `8080` |  |
| defaults.service.ports[2].name | string | `"https"` |  |
| defaults.service.ports[2].port | int | `443` |  |
| defaults.service.ports[2].protocol | string | `"TCP"` |  |
| defaults.service.ports[2].targetPort | int | `8443` |  |
| defaults.service.annotations | object | `{}` |  |
| defaults.service.loadBalancerIP | string | `""` |  |
| defaults.service.loadBalancerSourceRanges | list | `[]` |  |
| defaults.service.externalTrafficPolicy | string | `""` |  |
| defaults.service.externalIPs | list | `[]` |  |
| defaults.service.ipFamilyPolicy | string | `""` |  |
| defaults.service.ipFamilies | list | `[]` |  |
| defaults.resources.requests.cpu | string | `"100m"` |  |
| defaults.resources.requests.memory | string | `"128Mi"` |  |
| defaults.resources.limits.cpu | string | `"2000m"` |  |
| defaults.resources.limits.memory | string | `"1024Mi"` |  |
| defaults.autoscaling.enabled | bool | `true` |  |
| defaults.autoscaling.minReplicas | int | `1` |  |
| defaults.autoscaling.maxReplicas | int | `5` |  |
| defaults.autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| defaults.autoscaling.targetMemoryUtilizationPercentage | object | `{}` |  |
| defaults.autoscaling.autoscaleBehavior | object | `{}` |  |
| defaults.env | object | `{}` |  |
| defaults.labels | object | `{}` |  |
| defaults.annotations | object | `{}` |  |
| defaults.nodeSelector | object | `{}` |  |
| defaults.tolerations | list | `[]` |  |
| defaults.topologySpreadConstraints | list | `[]` |  |
| defaults.affinity | object | `{}` |  |
| defaults.networkGateway | string | `""` |  |
| defaults.image.repo | string | `"registry1.dso.mil/ironbank/opensource/istio/proxyv2"` |  |
| defaults.image.tag | string | `"1.23.3"` |  |
| defaults.imagePullPolicy | string | `""` |  |
| defaults.imagePullSecrets[0].name | string | `"private-registry"` |  |
| defaults.podDisruptionBudget | object | `{}` |  |
| defaults.terminationGracePeriodSeconds | int | `30` |  |
| defaults.volumes | list | `[]` |  |
| defaults.volumeMounts | list | `[]` |  |
| defaults.priorityClassName | string | `""` |  |
| defaults.enterprise | bool | `false` |  |
| defaults.tidHub | string | `"registry1.dso.mil/ironbank/tetrate/istio"` |  |
| defaults.tidTag | string | `"1.23.3-tetratefips-v0"` |  |
| mtls.mode | string | `"STRICT"` | STRICT = Allow only mutual TLS traffic, PERMISSIVE = Allow both plain text and mutual TLS traffic |
| networkPolicies.enabled | bool | `true` |  |
| networkPolicies.additionalPolicies | list | `[]` |  |
| monitoring.enabled | bool | `false` |  |
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

## Contributing

Please see the [contributing guide](./CONTRIBUTING.md) if you are interested in contributing.

---

_This file is programatically generated using `helm-docs` and some BigBang-specific templates. The `gluon` repository has [instructions for regenerating package READMEs](https://repo1.dso.mil/big-bang/product/packages/gluon/-/blob/master/docs/bb-package-readme.md)._


<!-- Warning: Do not manually edit this file. See notes on gluon + helm-docs at the end of this file for more information. -->
# gateway

![Version: 1.25.1-bb.1](https://img.shields.io/badge/Version-1.25.1--bb.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.25.1](https://img.shields.io/badge/AppVersion-1.25.1-informational?style=flat-square) ![Maintenance Track: bb_integrated](https://img.shields.io/badge/Maintenance_Track-bb_integrated-green?style=flat-square)

Helm chart for deploying Istio gateways

## Upstream References

- <https://github.com/istio/istio>

## Upstream Release Notes

- [Find our upstream chart's CHANGELOG here](https://istio.io/latest/news/releases/1.25.x/announcing-1.25)

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
| _internal_defaults_do_not_set.name | string | `""` |  |
| _internal_defaults_do_not_set.revision | string | `""` |  |
| _internal_defaults_do_not_set.replicaCount | string | `nil` |  |
| _internal_defaults_do_not_set.kind | string | `"Deployment"` |  |
| _internal_defaults_do_not_set.rbac.enabled | bool | `true` |  |
| _internal_defaults_do_not_set.serviceAccount.create | bool | `true` |  |
| _internal_defaults_do_not_set.serviceAccount.annotations | object | `{}` |  |
| _internal_defaults_do_not_set.serviceAccount.name | string | `""` |  |
| _internal_defaults_do_not_set.podAnnotations."prometheus.io/port" | string | `"15020"` |  |
| _internal_defaults_do_not_set.podAnnotations."prometheus.io/scrape" | string | `"true"` |  |
| _internal_defaults_do_not_set.podAnnotations."prometheus.io/path" | string | `"/stats/prometheus"` |  |
| _internal_defaults_do_not_set.podAnnotations."inject.istio.io/templates" | string | `"gateway"` |  |
| _internal_defaults_do_not_set.podAnnotations."sidecar.istio.io/inject" | string | `"true"` |  |
| _internal_defaults_do_not_set.securityContext | object | `{}` |  |
| _internal_defaults_do_not_set.containerSecurityContext | object | `{}` |  |
| _internal_defaults_do_not_set.resources.requests.cpu | string | `"100m"` |  |
| _internal_defaults_do_not_set.resources.requests.memory | string | `"128Mi"` |  |
| _internal_defaults_do_not_set.resources.limits.cpu | string | `"2000m"` |  |
| _internal_defaults_do_not_set.resources.limits.memory | string | `"1024Mi"` |  |
| _internal_defaults_do_not_set.autoscaling.enabled | bool | `true` |  |
| _internal_defaults_do_not_set.autoscaling.minReplicas | int | `1` |  |
| _internal_defaults_do_not_set.autoscaling.maxReplicas | int | `5` |  |
| _internal_defaults_do_not_set.autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| _internal_defaults_do_not_set.autoscaling.targetMemoryUtilizationPercentage | object | `{}` |  |
| _internal_defaults_do_not_set.autoscaling.autoscaleBehavior | object | `{}` |  |
| _internal_defaults_do_not_set.env | object | `{}` |  |
| _internal_defaults_do_not_set.strategy | object | `{}` |  |
| _internal_defaults_do_not_set.minReadySeconds | string | `nil` |  |
| _internal_defaults_do_not_set.readinessProbe | object | `{}` |  |
| _internal_defaults_do_not_set.labels."istio.io/dataplane-mode" | string | `"none"` |  |
| _internal_defaults_do_not_set.annotations | object | `{}` |  |
| _internal_defaults_do_not_set.nodeSelector | object | `{}` |  |
| _internal_defaults_do_not_set.tolerations | list | `[]` |  |
| _internal_defaults_do_not_set.topologySpreadConstraints | list | `[]` |  |
| _internal_defaults_do_not_set.affinity | object | `{}` |  |
| _internal_defaults_do_not_set.networkGateway | string | `""` |  |
| _internal_defaults_do_not_set.image.repo | string | `"registry1.dso.mil/ironbank/opensource/istio/proxyv2"` |  |
| _internal_defaults_do_not_set.image.tag | string | `"1.25.1"` |  |
| _internal_defaults_do_not_set.imagePullPolicy | string | `""` |  |
| _internal_defaults_do_not_set.imagePullSecrets[0].name | string | `"private-registry"` |  |
| _internal_defaults_do_not_set.podDisruptionBudget | object | `{}` |  |
| _internal_defaults_do_not_set.terminationGracePeriodSeconds | int | `30` |  |
| _internal_defaults_do_not_set.volumes | list | `[]` |  |
| _internal_defaults_do_not_set.volumeMounts | list | `[]` |  |
| _internal_defaults_do_not_set.priorityClassName | string | `""` |  |
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
| service.type | string | `"LoadBalancer"` |  |
| service.ports[0].name | string | `"tcp-status-port"` |  |
| service.ports[0].port | int | `15021` |  |
| service.ports[0].protocol | string | `"TCP"` |  |
| service.ports[0].targetPort | int | `15021` |  |
| service.ports[1].name | string | `"http2"` |  |
| service.ports[1].port | int | `80` |  |
| service.ports[1].protocol | string | `"TCP"` |  |
| service.ports[1].targetPort | int | `8080` |  |
| service.ports[2].name | string | `"https"` |  |
| service.ports[2].port | int | `443` |  |
| service.ports[2].protocol | string | `"TCP"` |  |
| service.ports[2].targetPort | int | `8443` |  |
| service.annotations | object | `{}` |  |
| service.loadBalancerIP | string | `""` |  |
| service.loadBalancerSourceRanges | list | `[]` |  |
| service.externalTrafficPolicy | string | `""` |  |
| service.externalIPs | list | `[]` |  |
| service.ipFamilyPolicy | string | `""` |  |
| service.ipFamilies | list | `[]` |  |

## Contributing

Please see the [contributing guide](./CONTRIBUTING.md) if you are interested in contributing.

---

_This file is programatically generated using `helm-docs` and some BigBang-specific templates. The `gluon` repository has [instructions for regenerating package READMEs](https://repo1.dso.mil/big-bang/product/packages/gluon/-/blob/master/docs/bb-package-readme.md)._


# How to upgrade the Istio Gateway Package chart

1. Checkout the branch that renovate created. This branch will have the image tag updates and typically some other necessary version changes that you will want. You can either work off of this branch or branch off of it.
1. Update via `kpt`:
    ```bash
    # update to VERSION of the upstream chart auto-merging in changes
    kpt pkg update chart@1.23.2 --strategy alpha-git-patch
    ```
    Or if you'd like to pull down upstream to a fresh `DIR` and manually merge in the changes yourself:
    ```bash
    # get a fresh VERSION of the upstream chart to DIR
    kpt pkg get "https://github.com/istio/istio.git/manifests/charts/gateway@1.23.2" ./fresh
    ```
1. Update version references for the Chart. `version` should be `<version>-bb.0` (ex: `1.22.2-bb.0`) and `appVersion` should be `<version>` (ex: `1.22.2`). Also validate that the BB annotation for the main Istio version is updated (leave the Tetrate version as-is unless you are updating those images).
1. Add a changelog entry for the update. At minimum mention updating the image versions.
1. Update the readme following the [steps in Gluon](https://repo1.dso.mil/platform-one/big-bang/apps/library-charts/gluon/-/blob/master/docs/bb-package-readme.md).
1. Open MR (or check the one that Renovate created for you) and validate that the pipeline is successful. Also follow the testing steps below for some manual confirmations.

# Testing new Istio Gateway version

Generally, an `istio-gateway` update should be tested alongside the new versions of `istio-base` and `istiod`. Follow the steps outlined in the Istio base/istod [Development Maintenance Guide](https://repo1.dso.mil/big-bang/apps/sandbox/istio/-/blob/main/docs/DEVELOPMENT_MAINTENANCE.md?ref_type=heads#testing-new-istio-controlplane-version)

# Modifications made to upstream chart
This is a high-level list of modifications that Big Bang has made to the upstream helm chart. You can use this as as cross-check to make sure that no modifications were lost during the upgrade process.

##  chart/values.schema.json
- Removed the `imagePullSecrets` key from this json file. At the moment this is necessary so that the helm chart passes validation and begins deployment. A different workaround may obviate the need for this down the road.
    ```json
        - "imagePullSecrets": {
        -   "type": "array",
        -   "items": {
        -     "type": "object",
        -     "properties": {
        -       "name": {
        -         "type": "string"
        -       }
        -     }
        -   }
        - },
    ```

## chart/templates/deployment.yaml
- Added templating for Tetrate FIPs image integration lines 56-60.
- Modified the following section under `spec.template.spec.containers.ports` to suppress warnings from Kiali as the gateway deployment was not listening on the same ports as its associated service:

```
          {{- range $ports := .Values.service.ports }}
          - containerPort: {{ $ports.targetPort }}
            protocol: {{ $ports.protocol }}
            name: {{ $ports.name }}
          {{- end }}
```

## chart/values.yaml
- Added enterprise boolean, tidHub and tidTag for Tetrate FIPs image integraton lines 157-160.
- Prepended default `status-port` to `tcp-status-port` under `service.ports` section to appease Kiali warning.
- Added gateway which is used to pass down required values into `chart/templates/bigbang/gateway.yaml`
- Added the following `mtls` section to enable mutual TLS used in `chart/templates/bigbang/peerAuthentication.yaml`:

```
mtls:
  # -- STRICT = Allow only mutual TLS traffic,
  # PERMISSIVE = Allow both plain text and mutual TLS traffic
  mode: STRICT
```
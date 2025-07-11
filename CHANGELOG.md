# Changelog

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---
## [1.26.2-bb.0] (2025-07-11)

### Changed

- ironbank/opensource/istio/proxyv2 updated from 1.26.1 to 1.26.2

## [1.26.1-bb.3] (2025-07-08)

### Updated

- Updated all `namespace` keys to use `.Release.Namespace` instead of hardcoding `istio-gateway`

### Removed

- Removed extraneous flux labels from the `Gateway` manifest

## [1.26.1-bb.2] (2025-06-17)

### Added

- Added Helm values schema

## [1.26.1-bb.1] (2025-06-17)

### Changed

- Changed the chart name back to `gateway` from `istio-gateway` (accidentally flipped it back to istio-gateway as part of renovate update)

## [1.26.1-bb.0] (2025-06-12)

### Changed

- ironbank/opensource/istio/proxyv2 updated from 1.25.3 to 1.26.1

## [1.25.3-bb.4] - 2025-06-12

### Changed

- Changed the chart name back to `gateway` from `istio-gateway` due to an issue with service recreation on 3.0 upgrade

## [1.25.3-bb.3] - 2025-06-11

### Updated

- Updated all conditional resource creations to be per-release

## [1.25.3-bb.2] - 2025-06-09

### Updated

- Fixed an issue where duplicate default `AuthorizationPolicy` resources were being created

## [1.25.3-bb.0] - 2025-06-04

### Updated

- Updated chart name to `istio-gateway` from `gateway` to avoid collisions in registry1

## [1.25.3-bb.0] - 2025-05-28

### Changed

- ironbank/opensource/istio/proxyv2 updated from 1.25.2 to 1.25.3

## [1.25.2-bb.1] (2025-04-22)

### Changed

- Updated chart meta and added annotations

## [1.25.2-bb.0] (2025-04-18)

### Changed

- Updated for upstream 1.25.2

## [1.25.1-bb.3] - 2025-04-17

### Added

- Added a default `istio=ingressgateway` label

## [1.25.1-bb.2] - 2025-04-15

### Changed

- Refactored chart to passthrough pattern

## [1.25.1-bb.1] - 2025-04-09

### Added

- Readme updated for `enterprise` value removal.

## [1.25.1-bb.0] - 2025-04-02

### Added

- Updated to match upstream v1.25.1 of istio-gateway

## [1.23.3-bb.3] - 2024-02-13

### Added

- Updated dependency reference for operatorless istio

## [1.23.3-bb.2] - 2024-02-07

### Added

- Default network policies

## [1.23.3-bb.1] - 2024-12-31

### Added

- Updated gateway to use values from template
- Modified deployment.yaml to use service values on container as well
- Added missing peerAuthentication and authorizationPolicy
- Updated values.yaml to include settings for the above
- Updated image to IronBank image as the auto setting was problematic

## [1.23.3-bb.0] - 2024-12-26

### Added

- Update Gateway to 1.23.3

## [1.23.2-bb.3] - 2024-12-24

### Changed

- Updated ports in gateway template
- Updated service account name default in \_helpers.tpl

## [1.23.2-bb.2] - 2024-12-20

### Added

- Added Gateway template

## [1.23.2-bb.1] - 2024-12-06

### Added

- Added templating for Tetrate image Integration.

## [1.23.2-bb.0] - 2024-10-21

### Added

- Updated chart from 1.22.2 to 1.23.2

## [1.22.2-bb.0] - 2024-07-17

### Added

- Added Istio/gateway v1.22.2 chart files.
- Generated README.md

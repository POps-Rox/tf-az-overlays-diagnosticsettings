# Changelog

All notable changes to this project are documented here. Format based on
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0] - 2026-05-11

### Changed (BREAKING)

- Upgraded `hashicorp/azurerm` provider constraint from `~> 3.116` to `~> 4.20`.
- Raised minimum Terraform CLI version from `>= 1.9` to `>= 1.10`.

### Added

- New `azure/azapi ~> 2.0` provider declaration in `versions.tf` (root + both
  examples) for fleet alignment.
- Comment in the example `provider "azurerm"` blocks noting that
  `subscription_id` is provided by the consumer via the `ARM_SUBSCRIPTION_ID`
  environment variable (required by azurerm 4.x).
- Example `versions.tf` files (`examples/Commerical/default/versions.tf` and
  `examples/Government/default/versions.tf`) now declare a full `terraform`
  block with `required_version` and `required_providers` (previously only had
  a bare `provider "azurerm"` block).

### Notes

- Module already uses the 4.x-compatible `enabled_log` block on
  `azurerm_monitor_diagnostic_setting`; no migration from the deprecated `log`
  block was needed.
- No `retention_policy` blocks present on `azurerm_monitor_diagnostic_setting`
  in this module — Phase 1 retention audit returned zero hits.
- No mechanical attribute renames (`enable_*`, `allow_blob_public_access`, etc.)
  were required.
- CI may show transitive provider-constraint failures on the example stacks
  until upstream POps-Rox overlays are also bumped to `~> 4.20`. Failures
  resolve as Phase 1 PRs land.

## v1.0.0 - <date>

Added
- Add Something you added

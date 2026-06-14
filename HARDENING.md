<!-- markdownlint-disable -->

# Hardening Report: andrewmcodes--standardrb-action/v2.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **andrewmcodes--standardrb-action/v2.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### hardcoded-credentials (severity: high)

In action.yml, the env block sets `GITHUB_TOKEN: secrets.GITHUB_TOKEN`. The value `secrets.GITHUB_TOKEN` is a plain literal string — it is NOT a GitHub Actions expression (which would require `${{ secrets.GITHUB_TOKEN }}`). This means the GITHUB_TOKEN environment variable will be set to the literal text "secrets.GITHUB_TOKEN" rather than the actual secret, and the literal value matches the hardcoded-credentials pattern (key contains "token", value is a non-expression alphanumeric string). The correct form is `GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}`

Locations:

- `action.yml:9`

## Iteration Notes

### Iteration 1

**Fixes applied:** hardcoded-credentials

**Notes:**

Fixed action.yml line 9: changed `GITHUB_TOKEN: secrets.GITHUB_TOKEN` (a plain literal string) to `GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}` (a proper GitHub Actions expression). The original value was setting the environment variable to the literal text "secrets.GITHUB_TOKEN" rather than the actual secret token.


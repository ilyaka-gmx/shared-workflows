# shared-workflows

Reusable GitHub Actions workflows for `ilyaka-gmx`.

## `security-scan.yml`

Runs a security scanner against the caller's repository.
The scanner logic lives in `.github/actions/scan/` and **differs between releases** —
callers pin a ref and automatically get the scanner version that shipped with it.

### Usage

```yaml
jobs:
  scan:
    uses: ilyaka-gmx/shared-workflows/.github/workflows/security-scan.yml@v1
    permissions:
      id-token: write
      contents: read
```

No inputs required. Pin `@v1` or `@v2` to control which scanner runs.

| Ref | Scanner |
|-----|---------|
| `v1` | Basic — 4 secret patterns |
| `v2` | Extended — 47 patterns + TODO/FIXME + CVE hint |

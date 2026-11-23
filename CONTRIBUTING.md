# Contributing

Thank you for helping LXRAY. This repository publishes the signed packages and
their documentation; the source code is not published here, so pull requests
with code are not accepted.

## How you can help

- **Report a problem**: open an
  [issue](https://github.com/eljouan/lxray/issues/new/choose) with the bug report
  form. Attach `report/lxray-summary.txt` from your snapshot: it is redacted, but
  read it before posting.
- **Report a distribution**: tell us whether LXRAY runs on a distribution or a
  version that is not yet in the compatibility matrix of the [README](README.md).
- **Suggest an improvement**: a check that is missing, a false alert, a report
  that is unclear.
- **Security problems**: never in a public issue. See [SECURITY.md](SECURITY.md).

## Contact

El Mehdi Jouan, **ej@jouan.us**

## Repository rules (maintainers)

- `main` is protected: every change goes through a pull request, and its history
  stays linear.
- Release tags `vX.Y.Z` are never moved or deleted once published.
- Branch names:

| Prefix | Use | Example |
|---|---|---|
| `release/` | files of a new version (README, SHA256SUMS) | `release/1.3.0` |
| `docs/` | documentation only | `docs/community-files` |
| `fix/` | correction of a published file | `fix/readme-links` |

Branches are deleted automatically once merged.

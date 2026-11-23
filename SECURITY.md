# Security policy

## Supported versions

Only the latest version receives fixes. The repositories (`apt`, `dnf`, `zypper`)
always install it.

| Version | Supported |
|---|---|
| 1.2.x | Yes |
| 1.1.x and older | No, update to the latest version |

## Reporting a vulnerability

Please do not open a public issue for a security problem.

Report it privately, either:

- with the **Report a vulnerability** button in the
  [Security](https://github.com/eljouan/lxray/security) tab of this repository, or
- by e-mail to **ej@jouan.us**.

Include the LXRAY version (`lxray version`), the distribution and its version,
what you observed and the steps to reproduce it. You will receive an answer within
7 days. Once a fix is published, the report is credited in the release notes if you
wish.

## Verifying the packages

Every package is signed with the key
`2045 3DAF 3BD4 BDC9 B035 1D19 3F70 F7EA 1C48 682C` (El Mehdi Jouan).
Check a downloaded package against `SHA256SUMS` and its `.asc` signature with
`jouan.asc`, both attached to each release. The RPM signature is embedded: `rpm -K`.

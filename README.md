# LXRAY

All Linux Flavours Servers Diagnostics.

LXRAY reads the real state of a Linux server (identity, hardware, CPU and memory,
storage and RAID, network, firewall, kernel, services, packages, security, logs,
databases, containers and applications) and writes a scored HTML report with the
evidence for each problem and the fix to apply.

- It reads your real system: every finding comes from what the machine holds.
- No agent, no account, no cloud service, and no Internet connection needed.
- Read-only: it changes nothing on the machine it examines.
- Free to use, for personal and commercial purposes. See [LICENSE](LICENSE).

Project page: https://jouan.us/upstream/en/lxray/

## Install

The packages are published in a signed repository. Once the key is installed, `apt` and
`dnf` verify and update them like any other package.

### Debian, Ubuntu and derivatives

```
sudo install -d -m 0755 /etc/apt/keyrings
curl -fsSL https://jouan.us/upstream/packages/jouan.gpg | sudo tee /etc/apt/keyrings/jouan.gpg >/dev/null
curl -fsSL https://jouan.us/upstream/packages/jouan.sources | sudo tee /etc/apt/sources.list.d/jouan.sources >/dev/null
sudo apt update
sudo apt install lxray
```

### RHEL, Oracle Linux, AlmaLinux, Rocky, Fedora

```
sudo curl -fsSL -o /etc/yum.repos.d/jouan.repo https://jouan.us/upstream/packages/jouan.repo
sudo dnf install lxray
```

`dnf` shows the key fingerprint once and asks for confirmation. It must be
`2045 3DAF 3BD4 BDC9 B035 1D19 3F70 F7EA 1C48 682C`.

### openSUSE, SLES

```
sudo rpm --import https://jouan.us/upstream/packages/jouan.asc
sudo curl -fsSL -o /etc/zypp/repos.d/jouan.repo https://jouan.us/upstream/packages/jouan.repo
sudo zypper install lxray
```

The repositories always install the latest version; a system update moves existing
machines to it.

### Manual download

Download the package from the [Releases](https://github.com/eljouan/lxray/releases) page.
Check it against `SHA256SUMS`, and against its `.asc` signature with the public key
`jouan.asc`.

```
sudo apt install ./lxray_1.2.0_all.deb       # Debian, Ubuntu
sudo dnf install ./lxray-1.2.0-1.noarch.rpm  # RHEL family, Fedora
sudo zypper install ./lxray-1.2.0-1.noarch.rpm   # openSUSE, SLES
```

## Versions

| Version | Date | What changed |
|---|---|---|
| [1.2.0](https://github.com/eljouan/lxray/releases/tag/v1.2.0) | 2026-11-23 | HTML report redesigned as an enterprise infrastructure audit report. |
| [1.1.0](https://github.com/eljouan/lxray/releases/tag/v1.1.0) | 2026-11-23 | Complete snapshot without root, package for openSUSE and SLES, 14 distributions tested. |
| [1.0.0](https://github.com/eljouan/lxray/releases/tag/v1.0.0) | 2026-11-22 | First public version: snapshot, scored report, signed packages. |

Full notes for each version: https://jouan.us/upstream/en/lxray/versions/

## Compatibility

What was actually installed and run for each version, as root and without root.

| Distribution | Install | 1.2.0 | 1.1.0 | 1.0.0 |
|---|---|---|---|---|
| Debian 11 | .deb package | Tested (package) | Tested (package) | Not tested |
| Debian 12 | .deb package | Tested (package) | Tested (package) | Tested |
| Debian 13 | .deb package | Tested (package) | Tested (package) | Not tested |
| Ubuntu 22.04 | .deb package | Tested (package) | Tested (package) | Not tested |
| Ubuntu 24.04 | .deb package | Tested (package) | Tested (package) | Not tested |
| AlmaLinux 8 | .rpm package | Tested (package) | Tested (package) | Tested |
| AlmaLinux 10 | .rpm package | Tested (package) | Tested (package) | Not tested |
| Rocky Linux 9 | .rpm package | Tested (package) | Tested (package) | Not tested |
| Fedora 43 | .rpm package | Tested (package) | Tested (package) | Not tested |
| openSUSE Leap 15.6 | .rpm package | Tested (package) | Tested (package) | Not tested |
| openSUSE Leap 16.0 | .rpm package | Tested (package) | Tested (package) | Not tested |
| openSUSE Tumbleweed | .rpm package | Tested (package) | Tested (package) | Not tested |
| SLES 15 SP6 | .rpm package | Not tested | Dependencies checked | Not tested |
| Alpine 3.22 | archive | Tested (archive) | Tested (archive) | Not tested |
| Arch Linux | archive | Tested (archive) | Tested (archive) | Not tested |

- **Tested (package)**: installed from the signed package, snapshot and report as root and without root.
- **Tested (archive)**: same test, installed from the archive.
- **Dependencies checked**: the distribution's package manager resolves every dependency; the tool has not been run there yet.
- **Not tested**: no test for that version, which does not mean it is incompatible.

## Usage

```
sudo lxray run                 # collect a snapshot and build the HTML report
sudo lxray collect -p full     # detailed snapshot
lxray analyze <snapshot>       # analyse an existing snapshot
lxray deps                     # show which diagnostic tools are missing
lxray plugins                  # list the collection modules
```

Run as root for a complete snapshot. The report is written to
`/var/tmp/lxray-HOST-DATE/report/lxray-report.html`.

Without root, LXRAY still runs and says exactly what it could not read. Before
collecting, it tries each protected source (shadow, sudoers, kernel log, journal,
firewall rules, SMART, LVM, Docker...) and records the result in `access.tsv`. The
report lists every source it could not read or could only read in part, why, and
how to read it (`sudo`, or the group that grants access). The checks that depend on
them are shown as "not evaluated": they never count as passed. Where the kernel
exposes the same facts without root, LXRAY reads them there: RAID state and disk
error counters from `/sys`, firewall state from its services and configuration
files, SSH settings from `sshd_config` and its included files. A run without root
exits with code 3 (partial snapshot).

## Privacy

Collection is read-only. Secrets, MAC addresses, UUIDs and e-mail addresses are redacted
at collection time unless `--no-redact` is given; add `--redact-ips` to mask IP addresses
too. Nothing is ever sent anywhere.

## Support and contact

- Report a problem: [open an issue](https://github.com/eljouan/lxray/issues/new/choose).
- Security problem: see [SECURITY.md](SECURITY.md), never in a public issue.
- Every change, version by version: [CHANGELOG.md](CHANGELOG.md).
- Contact: El Mehdi Jouan, **ej@jouan.us**

## License

Free to use. All rights reserved by El Mehdi Jouan. See [LICENSE](LICENSE).

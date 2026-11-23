# Changelog

Every version of LXRAY. The packages of each version are on the
[Releases](https://github.com/eljouan/lxray/releases) page.

## 1.2.0 (2026-11-23)

HTML report redesigned as a true enterprise infrastructure audit report.

### Added

- HTML report redesigned as an infrastructure audit report: executive summary with score and grade, key indicators, priority actions, results by category, detailed findings with evidence and recommendations, system inventory. Print-ready, light and dark.

### Fixed

- No error message during collection on a host without an SSH server.

### Tested

- Installed from its package, as root and without root: Debian 11, 12 and 13, Ubuntu 22.04 and 24.04, AlmaLinux 8 and 10, Rocky Linux 9, Fedora 43, openSUSE Leap 15.6 and 16.0, openSUSE Tumbleweed; from the archive on Alpine 3.22 and Arch Linux.
- Upgrade from 1.1.0 on Debian 12, Rocky Linux 9 and openSUSE Leap 15.6.

## 1.1.0 (2026-11-23)

Complete snapshot without root, package for openSUSE and SLES, 14 distributions tested.

### Added

- A clear, complete snapshot without root: the report lists every piece of information it could not read, why, and the command that reads it. Those checks are marked "not evaluated" and never count as passed.
- Without root, more information is read anyway: RAID state, disk errors, firewall state, SSH server settings.
- New findings: disk offline, failed commands on a disk, broken package dependencies.
- The RPM also serves openSUSE and SLES. Diagnostic tools are recommended rather than required: a tool missing from one distribution no longer blocks the installation.

### Fixed

- CPU count read wrong, pending updates not counted, false "reboot required" on Debian and Ubuntu.
- False alerts about PostgreSQL, read-only mounts and inodes on network shares.
- "System up to date" shown although the update check had failed.
- Empty sections on Alpine and on the RHEL 8 family.

### Tested

- As root and without root: Debian 11, 12 and 13, Ubuntu 22.04 and 24.04, AlmaLinux 8 and 10, Rocky Linux 9, Fedora 43, openSUSE Leap 15.6 and 16.0, openSUSE Tumbleweed, Alpine 3.22, Arch Linux.
- Signed repository read and verified by `apt`, `dnf` and `zypper`, upgrade from 1.0.0, real installation with `zypper` on openSUSE Leap 15.6; dependencies checked on SLES 15 SP6.

### Known limits

- Not covered yet: RAID and SMART on physical disks, running on SLES, ARM processors.
- No package for Alpine and Arch yet.

## 1.0.0 (2026-11-22)

First public version: snapshot, scored report, signed packages.

### Added

- First version: complete snapshot, HTML report scored out of 100, signed packages for Debian and the RHEL family.

### Tested

- Debian 12 and AlmaLinux 8.

### Known limits

- RPM not tested on SUSE; incomplete snapshot without root.

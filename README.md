# specsync-security

Public, machine-readable security information about [SpecSync](https://docs.specsolutions.eu/specsync/), published by Spec Solutions Kft.

## Contents

| Path | What it is |
| --- | --- |
| [`vex/specsync.cdx-vex.json`](vex/specsync.cdx-vex.json) | The VEX (Vulnerability Exploitability eXchange) document of SpecSync, in [CycloneDX](https://cyclonedx.org) format. It states how known vulnerabilities of components used by SpecSync affect SpecSync, for example when a vulnerable component is included but the affected code is not used. It covers all versions and is updated when a new assessment is made. |
| `checksums/<package>/<version>/SHA256SUMS` | The SHA-256 checksums of the download packages of each release, from v5.7.0. They are the same checksums as on the [Downloads page](https://docs.specsolutions.eu/specsync/downloads); this repository keeps their public history. Files are only ever added, never changed. |

## SBOM and VEX

From v5.7.0, every SpecSync package contains a Software Bill of Materials (SBOM) in CycloneDX format, `specsync.cdx.json`, at the root of the package. The Docker image contains it as `/specsync/specsync.cdx.json`, and the SBOM of its operating system packages as `/specsync/os.cdx.json`.

Each SBOM refers to the VEX document in this repository with the URL

`https://raw.githubusercontent.com/specsolutions/specsync-security/main/vex/specsync.cdx-vex.json`

Vulnerability scanners that support VEX (for example Trivy) can use it to hide findings that do not affect SpecSync. See the [Security page](https://docs.specsolutions.eu/specsync/contact/security) of the documentation for details.

## Verifying a download

Download the `SHA256SUMS` file of the release and the package files into the same folder, then run:

```
sha256sum -c --ignore-missing SHA256SUMS
```

On Windows, compare the output of `Get-FileHash <file> -Algorithm SHA256` with the line of that file in `SHA256SUMS`.

## Reporting a vulnerability

See [SECURITY.md](SECURITY.md).

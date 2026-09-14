# Docker Sandbox Kits

Reusable sandbox kit mixins for development environments. Each kit defines the tools it installs and the network access it requires, so it can be composed into a sandbox without granting broader access than necessary.

## Getting started

Clone this repository:

```sh
cd ~/develop/github
gh repo clone thomd/sbx-kits
```

Use a kit when starting a sandbox:

```sh
sbx run --kit /absolute/path/to/sbx-kits/<kit-name> <agent> .
```

Or add it to an existing sandbox:

```sh
sbx kit add my-sandbox /absolute/path/to/sbx-kits/<kit-name>
```

Replace `<kit-name>` with one of the kits below. Kits are mixins and can be layered together when a sandbox needs more than one toolchain.

## Kits

### `node-secure`

Installs Node.js `22.20.0` from the official Node.js binaries and upgrades npm to `11.18.0`. The downloaded archive is verified against Node.js's published SHA-256 checksum before installation. It also applies the hardened `.npmrc` included with this kit.

```sh
sbx run --kit /absolute/path/to/sbx-kits/node-secure <agent> .
```

Network access is limited to `nodejs.org` for the verified runtime download and npm registry domains for dependency installation. The kit supports `x86_64` and `aarch64` Linux sandbox architectures.

### `maven`

Installs Apache Maven using `apt`.

```sh
sbx run --kit /absolute/path/to/sbx-kits/maven <agent> .
```

The kit permits the Ubuntu and Docker package mirrors needed during setup, plus Maven Central domains for resolving build dependencies.

## Combining kits

For example, layer Maven onto a sandbox that already uses the secure Node.js kit:

```sh
sbx kit add my-sandbox /absolute/path/to/sbx-kits/node-secure
sbx kit add my-sandbox /absolute/path/to/sbx-kits/maven
```

# FluorineOS Keyring

`Debian 13 Trixie | amd64`

> **Looking for the FluorineOS ISO?** Official installation images are published in the
> main repository:
> [FluorineOS/fluorine Releases](https://github.com/FluorineOS/fluorine/releases/latest).

`fluorine-keyring` installs the FluorineOS archive signing key and the APT source
definition for the official package repository. Install it before any FluorineOS package
obtained outside the ISO.

## Package Contents

| Path | Description |
| --- | --- |
| `/usr/share/keyrings/fluorineos-archive-keyring.gpg` | Binary archive signing keyring |
| `/etc/apt/sources.list.d/fluorineos.sources` | deb822 APT source definition |

## Source Definition

```ini
Types: deb
URIs: https://fluorineos.github.io/apt-repo
Suites: trixie
Components: main
Architectures: amd64
Signed-By: /usr/share/keyrings/fluorineos-archive-keyring.gpg
```

## Install

Install the package from the release ISO or from the repository pool, then refresh the
package index:

```sh
sudo dpkg -i fluorine-keyring_0.0.1_all.deb
sudo apt-get update
```

## Verify

```sh
gpg --show-keys /usr/share/keyrings/fluorineos-archive-keyring.gpg
```

The primary key fingerprint is
`DCF8D117141143E65F930B55206E495540B36253`.

## Build

Requires `dpkg-dev` and `debhelper` on Debian 13 `amd64`.

```sh
git clone https://github.com/FluorineOS/fluorine-keyring.git
cd fluorine-keyring
dpkg-buildpackage -us -uc -b
dpkg-deb -c ../fluorine-keyring_0.0.2_all.deb
```

The built `.deb` is written to the parent directory.

## License

Released under the MIT License. See [LICENSE](LICENSE) for the full text.

Source: [FluorineOS/fluorine-keyring](https://github.com/FluorineOS/fluorine-keyring)

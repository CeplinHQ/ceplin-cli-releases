# ceplin

`ceplin` is the Ceplin CLI: CEPL, the language for looking up and pivoting on
indicators (addresses, domains, URLs, hashes, command lines), in a terminal.
It is one file, with nothing to install and nothing else it needs. The
language and its documentation are at [ceplang.org](https://ceplang.org).

This repository holds the releases only: no source. Download the file for your
system from the [latest release](https://github.com/CeplinHQ/ceplin-cli-releases/releases/latest):

| file | for |
| --- | --- |
| [`ceplin-linux-amd64`](https://github.com/CeplinHQ/ceplin-cli-releases/releases/latest/download/ceplin-linux-amd64) | Linux on Intel or AMD |
| [`ceplin-linux-arm64`](https://github.com/CeplinHQ/ceplin-cli-releases/releases/latest/download/ceplin-linux-arm64) | 64-bit Linux on ARM, such as a Raspberry Pi 4 or 5 |
| [`ceplin-macos-arm64`](https://github.com/CeplinHQ/ceplin-cli-releases/releases/latest/download/ceplin-macos-arm64) | Macs with Apple silicon (M1 and later) |
| [`ceplin-macos-amd64`](https://github.com/CeplinHQ/ceplin-cli-releases/releases/latest/download/ceplin-macos-amd64) | Intel Macs |
| [`ceplin-windows-amd64.exe`](https://github.com/CeplinHQ/ceplin-cli-releases/releases/latest/download/ceplin-windows-amd64.exe) | Windows 10 and 11 on Intel or AMD |
| [`ceplin-windows-arm64.exe`](https://github.com/CeplinHQ/ceplin-cli-releases/releases/latest/download/ceplin-windows-arm64.exe) | Windows on ARM |

Older versions are on the [releases page](https://github.com/CeplinHQ/ceplin-cli-releases/releases).

## On Debian and Ubuntu: apt

apt installs `ceplin` and keeps it up to date, on Intel or AMD and on ARM:

```shell
sudo install -d -m 0755 /etc/apt/keyrings
sudo curl -fsSL -o /etc/apt/keyrings/ceplin.gpg https://apt.ceplin.com/ceplin.gpg
sudo curl -fsSL -o /etc/apt/sources.list.d/ceplin.sources https://apt.ceplin.com/ceplin.sources
sudo apt update
sudo apt install ceplin
```

The packages apt installs are attached to each release too, `ceplin_<version>_amd64.deb`
and `ceplin_<version>_arm64.deb`: `sudo apt install ./ceplin_<version>_amd64.deb`
installs one without the repository, and without updates.

## Check the download

Each file's SHA-256 is in `SHA256SUMS`. Put it in the folder you downloaded
the file to, before you rename the file, and run this there on Linux:

```shell
sha256sum -c SHA256SUMS --ignore-missing
```

or this on macOS:

```shell
shasum -a 256 -c SHA256SUMS --ignore-missing
```

Each prints the file's name and `OK`. On Windows, this prints the file's hash
in PowerShell, to compare with its line in `SHA256SUMS`:

```powershell
(Get-FileHash .\ceplin-windows-amd64.exe).Hash.ToLower()
```

## The first run

On Linux and macOS, make the file runnable with `chmod +x`. On macOS a
downloaded file is quarantined until you clear it:
`xattr -d com.apple.quarantine ceplin-macos-arm64`. The files are not yet
signed, so Windows may ask before running one.
[Get started](https://ceplang.org/start.html) goes through it step by step.

## Licences

`ceplin` is free to use under the Ceplin Terminal Beta Licence (`LICENSE`). By
downloading or using it you accept that licence. Each binary also includes the
Go runtime and code and data from other projects, under their own licences,
which that licence does not limit; they are listed in `NOTICE`, with the texts
in `LICENSE-GO`, `LICENSE-APACHE-2.0`, `LICENSE-GPL-2.0`. Three of those data files are
under the Mozilla Public License 2.0, and are attached to each release as each
binary includes them: `fortios.json.gz`, `iosxe.json.gz`, `public_suffix_list.dat.gz`.

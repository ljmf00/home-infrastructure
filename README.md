# home-server
Home Server ansible configuration

## Pre-configuration

They should have `base`, `base-devel`, `linux`, `linux-headers`
`python` and `netctl` installed.

It's possible to use different linux versions like:
- `linux-lts`
- `linux-hardened`
- `linux-zen`

Main network interface should have static IPv4 address to the specified on
`hosts` file.

### `torns` machine

This server should be installed with `linux-hardened`.

This machine should have `mdadm` package and `md80` and `md40` disks in software
RAID pre-configured.

## Post-configuration

### `torns` machine

After all configurations applied, make sure smb users doesn't have the default
password.

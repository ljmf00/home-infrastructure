# home-server
Home Server ansible configuration

## Usage

Running ansible playbooks can be done either with `ansible-playbook` binary
or using `configure` script:

```bash
./configure playbook setup-torns
```

This will run `playbooks/setup-torns.yml` ansible playbook.

### Configure every host

To configure every host properly, you can just run:

```bash
./configure
```

And it will run every playbook in order for you.


## Pre-configuration

They should have `base`, `base-devel`, `linux`, `linux-headers`
`python` and `netctl` installed.

It's possible to use different linux versions like:
- `linux-lts`
- `linux-hardened`
- `linux-zen`

Main network interface should have static IPv4 address to the specified on
`hosts` file.

### `mars` machine

This machine should be installed with `linux-lts` due to **fucking** nvidia.

This machine should have `mdadm` package and `md3` disks in software RAID
pre-configured.

### `torns` machine

This server should be installed with `linux-hardened`.

This machine should have `mdadm` package and `md80` and `md40` disks in software
RAID pre-configured.

## Post-configuration

### `torns` machine

After all configurations applied, make sure smb users doesn't have the default
password.

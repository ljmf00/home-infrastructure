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

### `luna` machine

This server should be installed with `linux-hardened`.

This machine should have `mdadm` package and configured following the below schema:

```
NAME      MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda         8:0    0  37.3G  0 disk
└─md127     9:127  0  74.5G  0 raid0 /srv
sdb         8:16   0  37.3G  0 disk
└─md127     9:127  0  74.5G  0 raid0 /srv
sdc         8:32   0 111.8G  0 disk
├─sdc1      8:33   0   100G  0 part  /
└─sdc2      8:34   0  11.8G  0 part  [SWAP]
sdd         8:48   0   2.7T  0 disk
└─sdd1      8:49   0   2.7T  0 part
  └─md126   9:126  0   2.7T  0 raid1 /mnt
sde         8:64   0 149.1G  0 disk
└─sde1      8:65   0   149G  0 part  /home
sdf         8:80   0   2.7T  0 disk
└─sdf1      8:81   0   2.7T  0 part
  └─md126   9:126  0   2.7T  0 raid1 /mnt
```

# Building snaps

## Prerequisites

CouchDB requires Ubuntu 16.04. If building on 18.04, then LXD might be useful.

1. `lxc launch ubuntu:16.04 couchdb-pkg`
1. `lxc exec couchdb-pkg bash`

1. `sudo apt update`
1. `sudo apt install snapd snapcraft`

1. `echo "deb https://apache.bintray.com/couchdb-deb xenial main" \ | sudo tee -a /etc/apt/sources.list`
1. `curl -L https://couchdb.apache.org/repo/bintray-pubkey.asc \ | sudo apt-key add -`

1. `sudo apt-get update -y`
1. `sudo apt install snapd snapcraft couchdb -y`

And select none

1. `git clone -b snap_deb_src https://github.com/sklassen/couchdb-pkg.git`
1. `git clone https://github.com/couchdb/couchdb-pkg.git`
1. `cd couchdb-pkg`

## How to do it

1. Edit `snap/snapcraft.yaml` to point to the correct tag (e.g. `2.2.0`)
1. `snapcraft`

## Instalation

You may need to pull the LXD file to the host system.

    $ lxc file pull couchdb-pkg/root/couchdb-pkg/couchdb_2.2.0_amd64.snap /tmp/couchdb_2.2.0_amd64.snap

The self crafted snap will need to be installed in devmode

    $ sudo snap install /tmp/couchdb_2.2.0_amd64.snap --devmode



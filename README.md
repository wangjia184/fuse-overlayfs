fuse-overlayfs
===========

An implementation of overlay+shiftfs in FUSE for rootless containers.

Usage:
=======================================================

```
$ fuse-overlayfs -o lowerdir=lowerdir/a:lowerdir/b,upperdir=up,workdir=workdir merged
```

Specify a different UID/GID mapping:

```
$ fuse-overlayfs -o uidmapping=0:10:100:100:10000:2000,gidmapping=0:10:100:100:10000:2000,lowerdir=lowerdir/a:lowerdir/b,upperdir=up,workdir=workdir merged
```

Requirements:
=======================================================

Your system needs `libfuse` >= v3.2.1.

* On Fedora: `dnf install fuse3-devel`
* On Ubuntu >= 19.04: `apt install libfuse3-dev`

Also, please note that, when using `fuse-overlayfs` **from a user namespace**
(for example, when using rootless `podman`) a Linux Kernel >= v4.18.0 is required.


Building:
=======================================================

fuse-overlayfs is written in Rust. To build:

```
cargo build --release
```

The resulting binary is at `target/release/fuse-overlayfs`.

To install:

```
make install
```

Pre-built static binaries for multiple architectures (x86_64, aarch64,
armv7l, s390x, ppc64le, riscv64) are available from the
[GitHub Releases](https://github.com/containers/fuse-overlayfs/releases) page.

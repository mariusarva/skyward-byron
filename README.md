# Skyward for the Xiaomi 17 Max (byron)

This branch carries everything the 17 Max build needs on top of the main line:
the configuration this phone boots by, the files its secure element and weaver
are served from, and the script that packs them into a recovery image.

```
byron/
  device.toml     the phone's configuration: display, modules, services, files
  files/          the 24 files device.toml's [[file]] entries name (3.8 MB)
  mk.sh           builds the binary and packs the image
```

## 0.5.9 起

二进制与 pudding 线是同一份源码（Root 管理、模块管理、Kinaxie 的服务与合并修复都在里面），
差别只在这份 `device.toml` 与 `files/`；Root 的素材（ksud、KMI 模块、两个管理器 APK）
不随包分发，写入时从 GitHub 取，需要联网。

`mk.sh` 2026-11-26 修过一处：原厂镜像自己的 vbmeta 在「它自己的」页对齐位置上，
ramdisk 一变长就不能拿新地址去读，否则打出来的镜像里没有 AVB0。

## How it differs from the 17 (pudding)

| | 17 (pudding) | 17 Max (byron) |
|---|---|---|
| services | 1 (post_boot) | 3 (secure element, weaver, boot control) |
| files copied into the ramdisk | none | 24 |
| how the data partition is opened | the gatekeeper-bound note (`weaver_first = false`, weaver and secure element left out) | the weaver, over the phone's own secure element service |
| modules | synaptics + novatek | synaptics + focaltech + nxp-nci |
| online update | on | **off** (`update = false`): this build is not what the repository's releases carry |

The two decryption routes are exclusive: on the 17 starting the weaver holds
the phone's devices back twenty seconds and leaves the keys unusable, which is
why its configuration leaves the weaver out and the 17 Max's does not.

## Building

```
git checkout byron
SKYWARD_SRC=<the skyward 0.3.1 tree with the pudding patch applied> \
  byron/mk.sh 0.3.15 /path/to/byron-stock-recovery.img
```

`stock-recovery.img` is the phone's own recovery partition, read out of its
firmware. Its ramdisk is the shell (props, fstab, init rules) and its AVB footer
and vbmeta are reused, with the size and digest rewritten for what was packed.

Always keep a copy of that stock image: it is also how the phone is put back.

## What the 24 files are for

`/system/lib64/libdl_android.so`, `libvndksupport.so`, `libapexsupport.so` are
real files here rather than the symlinks a running Android has, because a
recovery mounts no APEX. `libEseUtils.so`, `libGPQeSE.so`, `libQSEEComAPI.so`
are what the secure element service loads; `/skyward/lib64/*` and
`/skyward/hw/{se-qti, weaver-nxp}` are what the weaver chain runs against.

A build that leaves them out still draws its pages and takes touches, but the
secure element service exits with status 1 every second, the weaver never
registers, and opening the data partition fails with
`…IKeyMintDevice/default is not running` (2026-11-17).

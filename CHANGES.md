# 17 Max builds

| version | state |
|---|---|
| v0.5.12 | 与 pudding v0.5.12 同源：WLAN 手动 IP（进页用当前租约预填、网关须同网段、重启按它配置、详情页显示「地址来源」）；已保存的 WiFi 能真正删除；撤掉每秒重写 enable_touch_raw（改为唤醒补写一次）；DHCP 失败日志带服务器应答原文。mk.sh 的产物名默认改绝对路径、SRC 默认指到构建树 |
| v0.5.9 | 与 pudding 0.5.9 同源：Root 管理（在线装 KernelSU / Magisk，写前备份原厂 boot，只升不降，卡上显示百分比与速度、滑回即取消）；模块管理换成 KernelSU/Magisk 那一套；合并 Kinaxie 的服务复用与 optional、解密现场、解锁多处读、keep 双槽、快照未合并不许离开；修 mk.sh 取原厂 vbmeta 的地址（ramdisk 变长后原来读到空洞，镜像里没有 AVB0，2026-11-26） |
| v0.5.1 | 整体升级到上游 v0.5.0：payload 进度只算 payload 字节、未加密 data 可直接打开、刷 super/逻辑分区/稀疏镜像、备份恢复到新建分区、62 个时区；语言表裁到三种；修 Wi-Fi 手动连上后重复 join 导致 DHCP 失败的旧 bug（2026-11-23） |
| 0.0.36 | first build that opened the data partition, made 2026-11-16 on a shell that carried the 24 files already |
| 0.3.15 | the app list gains a read-only page for the system apps; the WLAN's driver is warmed as soon as its firmware is mounted, and the home page says “connecting” while the radio opens (2026-11-18) |
| 0.3.12 | rebuilt on the shared source line; the packing script had to learn to copy `[[file]]` before it worked (2026-11-17) |

The build is versioned with the main line (`0.3.12` here is the same source as
pudding's `v0.3.12`), and its online update is off: the repository's releases
carry the 17's image, not this phone's.
| v0.3.16 | 控制中心 12 个圆磁贴（3 行 4 列）+ 设备状态卡，时间与日期同一行；内置 AOSP 拼音输入；新增分区管理页；高级页精简、长页可滚动；修复磁贴命中与解密页间距（2026-11-19） |

| v0.3.17 | 磁贴标签 10dp；任务页、镜像备份、关机页、vbmeta 备份、息屏显示；本版不含浏览器（2026-11-20） |

| v0.3.23 | 新增录屏（三档设置 + AVI/MP4 + 计时胶囊）；磁贴排成「录屏 · 截图 · 重启 · 设置」（2026-11-21） |

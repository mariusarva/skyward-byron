# 17 Max builds

| version | state |
|---|---|
| v0.3.28 | 控制中心磁贴可自定义：长按磁贴进入编辑态、拖拽排序、点叉移除、候选区添加；磁贴 12 → 24；摆法存 `/metadata/skyward/tiles`（2026-11-22） |
| 0.0.36 | first build that opened the data partition, made 2026-11-16 on a shell that carried the 24 files already |
| 0.3.15 | the app list gains a read-only page for the system apps; the WLAN's driver is warmed as soon as its firmware is mounted, and the home page says “connecting” while the radio opens (2026-11-18) |
| 0.3.12 | rebuilt on the shared source line; the packing script had to learn to copy `[[file]]` before it worked (2026-11-17) |

The build is versioned with the main line (`0.3.12` here is the same source as
pudding's `v0.3.12`), and its online update is off: the repository's releases
carry the 17's image, not this phone's.
| v0.3.16 | 控制中心 12 个圆磁贴（3 行 4 列）+ 设备状态卡，时间与日期同一行；内置 AOSP 拼音输入；新增分区管理页；高级页精简、长页可滚动；修复磁贴命中与解密页间距（2026-11-19） |

| v0.3.17 | 磁贴标签 10dp；任务页、镜像备份、关机页、vbmeta 备份、息屏显示；本版不含浏览器（2026-11-20） |

| v0.3.23 | 新增录屏（三档设置 + AVI/MP4 + 计时胶囊）；磁贴排成「录屏 · 截图 · 重启 · 设置」（2026-11-21） |

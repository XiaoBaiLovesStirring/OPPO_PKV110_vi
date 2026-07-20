# OPPO PKV110 Kernel Exploit

基于 [NebuSec/CyberMeowfia](https://github.com/NebuSec/CyberMeowfia) 的 IonStack (CVE-2026-43499) 适配 OPPO PKV110 (OP5DFB)。

## 设备信息

| 项目 | 值 |
|------|-----|
| 设备 | OPPO PKV110 (OP5DFB) |
| Android | 16 (BP2A.250605.015) |
| 内核 | 5.15.180-android13-8 |
| 架构 | aarch64 |
| 基址 | 0xffffffc008000000 |
| 指纹 | OPPO/PKV110/OP5DFB:16/BP2A.250605.015/V.321da09-fd93bd-fd93c0:user/release-keys |

## 编译

需要 Android NDK r29，设置 `ANDROID_NDK_HOME` 环境变量后：

```bash
cd exploit
make PROJECT=PKV110-16.0.2.401 API=37
```

产物：
- `build/PKV110-16.0.2.401/bin/preload.so` — 主 exploit 载荷
- `build/embed/su_daemon_aarch64_pie` — 内嵌 su 守护进程

## GitHub Actions

本仓库包含自动编译工作流，每次推送自动编译 API 35 和 API 37 两个版本。

## 适配进度

- 137 个偏移变量
- 124 个已通过符号表/反汇编验证 ✅
- 13 个 task_struct PI 深层字段沿用 5.15 标准值 ⚠️

## 致谢

- [NebuSec/CyberMeowfia](https://github.com/NebuSec/CyberMeowfia) — 原始漏洞利用
- IonStack 系列研究

## 免责声明

本项目仅供安全研究目的使用。使用者需自行承担法律责任。

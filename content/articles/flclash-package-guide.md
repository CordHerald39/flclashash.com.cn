---
title: "FlClash 下载与校验教程：选对安装包并核对 SHA256"
category: "downloads"
label: "实用指南"
description: "结合 FlClash v0.8.98 真实附件和 Windows ZIP 下载校验结果，说明架构、包格式与校验边界。"
date: "2026-09-19"
updated: "2026-09-19"
author: "FlClash 中文指南编辑部"
draft: false
---

> 核验日期：2026-09-19。Windows ZIP 已实际下载并核对 SHA256；客户端连接与同步尚未实测。

## 先选平台，再选架构和包格式

本文使用开发者 v0.8.98 发行资产作具体示例，核验日期为 2026-09-19。以后版本应重新打开对应发行页，不把本文文件名中的版本号直接替换后猜下载地址。

| 系统 | 本次发行中的示例 | 选择依据 |
| --- | --- | --- |
| Windows x64 | windows-amd64-setup.exe / windows-amd64.zip | 安装器与压缩包是不同交付方式 |
| Windows ARM64 | windows-arm64-setup.exe / windows-arm64.zip | 对应 Windows on ARM |
| Android | android-arm64-v8a.apk / armeabi-v7a.apk / x86_64.apk | 按设备 ABI，不能按文件大小猜 |
| macOS | macos-amd64.dmg / macos-arm64.dmg | Intel 与 Apple Silicon 分别选择 |
| Linux | amd64 / arm64 的 AppImage、deb、rpm | 同时匹配 CPU 和发行版包管理 |

本表只列发行资产，不代表所有系统版本都兼容。实际要求及 Linux 依赖仍以[开发者说明](https://github.com/chen08209/FlClash)为准。

## Windows ZIP 的实际下载校验

本站从[开发者 v0.8.98 发行页](https://github.com/chen08209/FlClash/releases/tag/v0.8.98)下载 FlClash-0.8.98-windows-amd64.zip 和同页 SHA256SUMS。2026-09-19 本地计算得到：

~~~text
6ff2cee438c48c8fe98959c70ff909a4fb39540086d1898094d33951125faa70
~~~

结果与 SHA256SUMS 中对应 ZIP 条目完全一致。这里只核验了 Windows amd64 ZIP，不能把这个哈希拿去对照安装器、ARM64 包或以后版本。

## 你可以怎样复核

把 ZIP 与 SHA256SUMS 下载到自己确定的目录，在该目录打开 PowerShell，执行：

~~~powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\FlClash-0.8.98-windows-amd64.zip'
Select-String -LiteralPath '.\SHA256SUMS' -Pattern 'windows-amd64.zip'
~~~

比较完整的 64 位十六进制摘要，而不是只看首尾几位；大小写不影响值。若不同，先确认版本和附件名，再重新下载核验，暂不运行不一致的文件。发布者同源校验和能帮助确认下载一致性，并不等于完成独立代码安全审计。

## 压缩包不是只有一个 exe

本次实际查看 ZIP 目录，包含 FlClash.exe、FlClashCore.exe、FlClashHelperService.exe 和 EnableLoopback.exe 等文件。应完整解压并保持随附目录结构，不单独拖出主程序，也不因见到辅助 exe 就逐个运行。

这项检查是“下载与归档内容核验”，并没有启动 GUI、安装服务、开启系统代理或验证真实订阅。安装完成后还要做[订阅与连接验收](/articles/import-subscription/)。

## 版本更新时保留的三份材料

保留旧版本号、有效配置备份和新旧发行说明。第一次升级先复测一条已有成功路径，再启用新增功能。若需要回退，用原版本适配的备份，先保存新版本错误信息，不反复覆盖唯一数据目录。

## 来源与证据范围

附件名称和校验值来自上述开发者固定版本发行页；多平台说明来自开发者 README。下载、SHA256 对照和 ZIP 文件列表是本次实际执行结果，安装后使用效果尚未实测。本文不提供第三方重新打包程序，也不把校验一致写成“绝对安全”。

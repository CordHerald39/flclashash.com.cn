---
title: "FlClash Android 自动化：START、STOP 与 TOGGLE 怎么选"
category: tutorials
label: "专题指南"
description: "按 FlClash v0.8.99 官方 Intent 接口配置 Tasker 类自动化，区分活动动作、切换状态和实际连接验收。"
date: "2026-10-04"
updated: "2026-10-04"
author: "FlClash 中文指南编辑部"
draft: false
---

想在固定场景启动 FlClash，应先决定自动化需要“启动到指定状态”，还是“把现有状态反转”。这两类任务对应不同动作。本文以 FlClash v0.8.99 Android 版的官方说明、清单和活动处理源码为依据，不提供已经替你运行的自动化任务。

## 官方入口是启动 Activity

项目文档给出三个动作，供 Tasker、MacroDroid 等能够发送 Android Intent 的工具使用：

| 动作 | 表达的请求 |
| --- | --- |
| `com.follow.clash.action.START` | 请求启动 |
| `com.follow.clash.action.STOP` | 请求停止 |
| `com.follow.clash.action.TOGGLE` | 请求切换现有状态 |

[AndroidManifest](https://github.com/chen08209/FlClash/blob/68c71b8ef9b7486a224972eb371ff153c6b2de0f/android/app/src/main/AndroidManifest.xml)为这些动作设置活动入口，[QuickActionActivity](https://github.com/chen08209/FlClash/blob/68c71b8ef9b7486a224972eb371ff153c6b2de0f/android/app/src/main/kotlin/com/follow/clash/QuickActionActivity.kt)将三个动作分别交给对应处理函数。这里不是广播接收器接口；自动化工具中应使用启动活动的目标类型。界面字段随工具版本变化，不必照抄第三方截图中的按钮位置。

## 先准备一台能够手动连接的设备

先手动打开 FlClash，选择有效配置，完成系统要求的 VPN 授权，并确认一次实际请求可用。若手动操作尚未成功，自动化只能重复同样的失败。

在自动化工具中新建一个可手动触发的测试任务，将动作填写为 START，其余参数只按工具与 Android 的实际要求填写，不附订阅 URL、口令或整份配置。先在前台手动执行，再观察 FlClash 状态和系统 VPN 标志；最后访问同一个授权目标，确认流量接管。

## 固定场景通常更适合明确的动作

如果“进入某场景就启动”使用 TOGGLE，任务重复触发时可能把刚启动的代理又停掉。使用 START 和 STOP 可以更清楚地表达进入与退出场景的意图。仍应核对设备上重复触发的实际结果，不承诺所有系统都以同样方式调度后台活动。

官方还给出电脑通过 adb 启动动作的形式。已配置并授权 adb 的设备可以使用：

```sh
adb shell am start -a com.follow.clash.action.START
```

这是对你自己设备的状态变更命令，不是诊断读数；执行后按界面与实际请求验收。测试停止动作前，应结束依赖 VPN 的重要会话。

## 任务触发了，但网络没有接管

| 阶段 | 要记录什么 |
| --- | --- |
| 自动化任务运行记录 | 是否发出正确动作、目标类型是否为活动 |
| FlClash 状态 | 配置是否可用、启动是否报错 |
| Android 授权 | 是否仍等待 VPN 许可或受到系统限制 |
| 实际请求 | 新请求是否在预期路径上完成 |

只有任务日志写着“成功”时，不能推断代理连接成功。也不要为了让规则自动运行去随意放开所有后台权限；按设备要求处理具体限制，并保留手动开关作为回退。

## 来源与范围

2026-10-04 核对[固定 v0.8.99 README](https://github.com/chen08209/FlClash/blob/68c71b8ef9b7486a224972eb371ff153c6b2de0f/README.md)、上述清单及活动实现。本文未配置你的 Tasker 或 MacroDroid，也未在真实手机上验证后台触发。

首次连接尚未完成时，可先阅读[单设备订阅验收](/articles/import-subscription/)；自动化任务不负责同步配置或恢复备份。


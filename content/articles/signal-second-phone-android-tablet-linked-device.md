---
title: "Signal 想在第二部手机或安卓平板同时用：关联设备，不要重新注册主号"
description: "Signal 想在第二部手机或安卓平板同时用：关联设备，不要重新注册主号。按适用条件、操作步骤和失败分支处理，保留官方参考入口。"
date: "2026-10-05"
category: "tutorials"
updated: "2026-10-05"
author: "FlClash 中文指南 内容编辑"
draft: false
label: "海外社交"
---

已有一部完成主注册的手机，还想在第二部手机或安卓平板上同时使用同一 Signal 账号时，适用关联设备：不要在新机上重新注册主号，也不要把这次操作当成换机迁移。换机迁移是更换主设备身份，不是把会话复制到第二台并让两台一起在线。处理方向是主设备保持注册；新机只在首次安装或重装后的注册流程里用三点菜单 Link Device 出示二维码，由主设备在 Linked devices 扫码。2026年8月4日官方已支持关联另一部 Android 手机、Android 平板以及 iPhone，不要再套用只能 Desktop、iPad 的旧说明。步骤与限制见 [Linked Devices](https://support.signal.org/hc/en-us/articles/360007320551-Linked-Devices)，版本背景见 [More linked devices are on the table (and the Android tablet)](https://signal.org/blog/linked-devices-and-android-tablets/)。

## 先分清主号、换机迁移和关联设备

主注册发生在第一部手机，该机是 primary Signal Device。关联设备是在主设备之外再挂 Desktop、iPad、iPhone 或 Android 手机/平板，关联设备上的通讯同样按私密通道处理。每个账号最多 5 台已关联设备，可随时在主设备 Signal Settings > Linked devices 查看列表。

若目标是两台同时收发，应走关联，而不是在第二台按主设备方式重新注册。关联只能出现在该设备首次安装或重装后的注册流程；已经进入聊天界面后，不能中途再点一次关联。博客写明 Signal Android v8.20、Signal iOS v8.22 起滚动发布第二台手机与大屏支持，商店是否已推到你的设备以实际为准，不保证立即可用。

## 新装时用三点菜单出示二维码，由主机扫码

从官方应用商店安装 Signal。打开要关联的那台设备上的应用：

- Android 手机或平板：选 Continue，再点左上角三点菜单，选 Link Device，查看二维码。
- iPhone：同样 Continue，再左上角三点菜单 > Link Device。
- iPad：Continue > Add as New Device。
- Desktop：打开应用即可查看二维码。

回到已注册的主手机：打开 Signal，进入 Signal Settings > Linked devices > Link a new device。用设备解锁方式（生物识别或解锁设备的同一套密码/图案，不是 Signal PIN）打开应用内相机，扫描新机上的二维码。

扫码后选择 Transfer Message History 或 Don't Transfer。前者可从主手机同步全部聊天以及最近 45 天的媒体，过程基于与 Desktop、iPad 相同的 link-and-sync，端到端加密。选 Don't Transfer 后若改主意，必须在该关联设备上重装 Signal 才能再选传输。关联完成后，从新设备发一条消息以确认。

Android 平板上部分界面仍在完善，如 Settings、应用内相机和完整键盘快捷键；Chromebook 可用最新更新运行，但形态适配仍在进行。这些是体验差异，不单独证明关联失败。

## 同步范围、失联重装和失败分支

媒体同步范围是最近 45 天已保存的媒体，不是无限历史附件。聊天可选整份同步或不传；不传则新设备只有此后的新消息。

关联后主手机不能长期离线：至少每 30 天上线一次，否则已关联设备会解除关联。已关联设备自身连续 45 天不活动也会解除关联。解除后只能再用已注册的主设备重新关联。若设备已变成 unlinked，会提供清除当前数据并从主手机同步的选项；重装或清除都会丢掉该设备上未回到主设备的本地内容，操作前先确认主设备仍保有需要的记录。

常见失败与改法：新机已过注册界面、找不到 Link Device 时，只能卸载重装，再次进入 Continue 后的三点菜单；iPad 路径是 Add as New Device，不要和手机套用同一句。主设备扫码前要解锁设备本身，Signal PIN 打不开相机。已达 5 台时，先在主设备 Linked devices 查看列表；解除关联的后续点选以官方专页为准，本文不补充未给出的路径。选了 Don't Transfer 又想要历史：重装该关联设备并在流程中改选 Transfer Message History。关联后不同步时，确认主设备曾上线、未触犯 30 天规则，且两边版本已含上述更新。不要把第二台手机做成新的主注册。

以上不保证商店版本或地区渠道一定提供关联入口，以设备上实际出现的注册流程为准。

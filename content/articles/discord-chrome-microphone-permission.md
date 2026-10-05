---
title: "Discord 网页版麦克风没声音：Chrome 权限与输入设备排查"
description: "Discord 网页版麦克风没声音：Chrome 权限与输入设备排查。按适用条件、操作步骤、失败分支和官方参考逐项检查。"
date: "2026-10-06"
category: "tutorials"
updated: "2026-10-06"
author: "FlClash 中文指南 内容编辑"
draft: false
label: "海外社交与沟通平台"
---

Discord 网页版加入语音后别人听不到你时，按「Chrome 是否屏蔽站点 → 系统是否允许浏览器用麦 → 输入设备与 Mic Test」分层检查。处理方向是：网页版先核对浏览器与系统权限，同时排除自己静音、按键说话、频道没有 Speak 权限、选错麦克风。不要把所有语音故障都归到网络代理。学校或公司托管的 Chrome 可能无法自行改权限。

## 先分清没声音的类型，排除静音和频道权限

别人听不到你、自己听不到别人、只在某个频道失败，原因不同。先看麦克风或耳机图标是否有斜线：有斜线表示自己静音或闭音。服务器管理员也可能在服务器层面对你静音或闭音，需联系管理员解除。若只在部分服务器或频道出问题，更可能是权限：Connect 决定能否进入语音，Speak 决定能否开麦。输入模式不要误开成 Push to Talk。自己听不到某一个人时，可在语音频道里对该用户右键调节其音量，这与麦克风无输入不是同一问题。网页版通用步骤见 [Discord 语音与视频排查指南](https://support.discord.com/hc/en-us/articles/360045138471-Discord-Voice-and-Video-Troubleshooting-Guide)。

## Chrome 曾屏蔽 Discord：站点权限与系统权限分开处理

若以前在 Chrome 里拒绝过 Discord 使用麦克风，需要到浏览器设置里恢复。打开右上角更多，进入设置，左侧选隐私和安全，再打开网站设置，进入麦克风。在不允许使用麦克风的列表中找到 Discord，点右侧删除图标去掉屏蔽。回到网页客户端加入语音频道，出现提示时选择允许。也可以在不允许列表中点开站点，把麦克风权限改为允许。提示选项包括访问该网站时允许、仅这次访问时允许或一律不允许。未允许的站点无法参加语音；即使已允许，切到其他标签页或使用其他应用时，该站点也不能开始录制，需回到 Discord 标签页再试。

Chrome 还可能向操作系统申请麦克风。对话框中选择打开设置，开启麦克风后按提示退出或重启 Chrome。工作单位或学校的托管浏览器，网络管理员可能锁定摄像头和麦克风，本机改不了。官方步骤见 [Discord：在 Chrome 中启用麦克风](https://support.discord.com/hc/en-us/articles/205093487-How-do-I-enable-my-mic-in-Chrome) 与 [Chrome 中使用摄像头和麦克风](https://support.google.com/chrome/answer/2693767?co=GENIE.Platform%3DDesktop&hl=zh-Hans)。

## 输入设备、Mic Test 与常见失败分支

权限恢复后，用左下角齿轮打开用户设置，进入 Voice & Video。确认 Input Device 是当前要用的麦克风，输入音量不要过低；需要时在 Chrome 网站设置的麦克风页用向下箭头指定默认麦克风。用 Mic Test 的 Let's Check 确认系统能收到输入。线控静音要关掉，USB 或耳机插口插紧，可换其他 USB 口。系统里把该麦克风设为默认录音设备。仍无输入时，到 Debugging 使用 Reset Voice and Video Settings；退出语音再加入；重启 Chrome；再重启电脑。同时确认浏览器版本兼容、操作系统与音频驱动已更新。

常见失败：站点仍在不允许列表、系统未授权 Chrome、选成别的输入设备、Push to Talk 未按键、自己或服务器静音、频道没有 Speak。这些都会表现为没声音，与代理无关。托管环境改不了权限时，只能换未被策略锁定的浏览器，或改在其他客户端上核对设备。硬件仍异常可联系麦克风制造商。仍未解决可向 Discord 支持提交工单，说明浏览器及版本、发生在网页端，并附 Voice & Video 设置说明和输入输出设备列表。

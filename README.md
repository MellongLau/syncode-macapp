# Syncode Mac Introduction and User Guide

## Product Overview

Syncode Mac is a local AI coding workstation server running on macOS.  
It centralizes workspace management, security policy, project access control, and session execution on your Mac, then connects with mobile clients through secure pairing so you can submit tasks, review outputs, and approve commands/patches remotely.

In one sentence: **Mac hosts execution and governance; mobile handles remote collaboration and approvals.**

## Key Features

1. Server Control
   - Start/stop the local server with one click.
   - Configure listening port (default `8787`).
   - Monitor runtime status and system events.

2. Workspace Management
   - Add/remove accessible directories.
   - Enforce workspace path sandboxing to block out-of-scope file access.

3. Pairing and Connectivity
   - Generate one-time pairing codes (`120` seconds validity).
   - Support QR pairing for auto-filling host, port, and pairing code on mobile.

4. Device and Project Access Policy
   - Manage paired devices (disconnect, revoke, delete).
   - Configure per `device + workspace` access policy:
     - `All Projects`
     - `Selected Projects`

5. Logs and Security Monitoring
   - Live connections, connection history, token usage stats.
   - Operation logs and security events for auditability and troubleshooting.

6. AI Execution with Fallback
   - Supports OpenAI API execution.
   - Supports Codex CLI fallback when available.

7. Localization
   - Chinese, English, and follow-system language modes.

## Requirements

1. macOS (local network access permission recommended).
2. Node.js `18+` (for Codex CLI installation).
3. Codex CLI available in terminal.
4. Run `codex login` before first use.
5. If using OpenAI API, set:

```bash
export OPENAI_API_KEY=your_api_key
```

## Quick Start (About 5 Minutes)

1. Install Codex CLI

```bash
npm install -g @openai/codex
codex --version
```

2. Complete CLI authentication

```bash
codex login
```

3. Open Syncode Mac and go to the `Server` panel
   - Set port (default `8787`).
   - Click `Start`.

4. Go to the `Workspaces` panel
   - Add project root directories you want exposed to mobile clients.

5. Configure network policy as needed
   - LAN access
   - WAN access
   - AI outbound
   - Network wake

6. Generate a pairing code in the `Pairing` section
   - You can scan via iOS app for auto-fill.

7. Pair and connect from iOS app
   - After success, mobile can browse projects, create sessions, and submit tasks.

8. Daily workflow
   - Submit requests on mobile.
   - Approve command/patch prompts when required.
   - Monitor health via `Logs`, `Security`, and `Project Access` panels on Mac.

## Recommended Operating Practice

1. Validate stability in LAN mode first.
2. Enable WAN access only when required.
3. Use `Selected Projects` policy for external devices to enforce least privilege.
4. Periodically review paired devices and revoke unused authorizations.

## FAQ

1. Codex CLI is installed, but app says it is missing.
   - GUI processes may not inherit the expected `PATH`. Restart the app or fix system PATH.

2. Mobile cannot discover the server.
   - Ensure both devices are on the same subnet, LAN access is allowed by policy, and firewall/port settings are correct.

3. Pairing code keeps failing.
   - Pairing code is one-time and time-limited. Regenerate and verify host/port input.

4. AI request fails.
   - Check AI outbound policy first; if using OpenAI API, verify `OPENAI_API_KEY`.

5. How to allow a device to access only certain projects?
   - In `Project Access`, select the target `device + workspace`, switch policy to `Selected Projects`, then save.

## Contact and Download

- Contact Email: `mellong@qq.com`
- iOS App: <https://apps.apple.com/app/id6759236231>
[macapp-guide.zh-Hans.md](https://github.com/user-attachments/files/25521304/macapp-guide.zh-Hans.md)


-----


# 同栈 Mac（Syncode Mac）介绍与使用说明

## 产品介绍

同栈 Mac 是一个运行在 macOS 上的本地 AI 编码工作站服务端。  
它将你的 Mac 工作区、安全策略、项目权限和会话执行能力统一管理，并通过配对机制与移动端连接，让你可以在手机上发起任务、查看结果、审批命令和补丁。

一句话概括：**用 Mac 托管执行能力，用移动端完成远程协作与审批。**

## 核心功能

1. 服务管理
   - 一键启动/停止本地服务。
   - 自定义监听端口（默认 `8787`）。
   - 查看运行状态与关键系统事件。

2. 工作区管理（Workspace）
   - 添加/移除可访问目录。
   - 基于工作区边界进行路径沙箱保护，阻止越界访问。

3. 配对连接
   - 生成一次性配对码（`120` 秒有效）。
   - 支持二维码配对，移动端可自动填充 Host、端口和配对码。

4. 设备与权限控制
   - 管理已配对设备（断开、撤销、删除）。
   - 按“设备 + 工作区”设置项目访问策略：
     - `全部项目`
     - `指定项目`

5. 日志与安全监控
   - 实时连接、连接历史、Token 使用统计。
   - 操作日志与安全事件追踪，便于审计与排障。

6. AI 执行与回退
   - 支持 OpenAI API。
   - 在可用条件下支持 Codex CLI 回退执行。

7. 多语言支持
   - 支持中文/英文与跟随系统语言。

## 环境要求

1. macOS（建议授予本地网络访问权限）。
2. Node.js `18+`（用于安装 Codex CLI）。
3. Codex CLI（命令行可用）。
4. 首次使用前建议完成 `codex login` 授权。
5. 若使用 OpenAI API，请配置环境变量：

```bash
export OPENAI_API_KEY=your_api_key
```

## 快速上手（5 分钟）

1. 安装 Codex CLI

```bash
npm install -g @openai/codex
codex --version
```

2. 完成 CLI 登录

```bash
codex login
```

3. 打开同栈 Mac，进入 `服务` 面板
   - 设置端口（默认 `8787`）。
   - 点击“启动”。

4. 进入 `工作区` 面板
   - 添加你希望开放给移动端访问的项目根目录。

5. 配置网络策略（按你的部署场景）
   - 局域网连接
   - 外网连接
   - AI 出网
   - 网络唤醒

6. 进入 `配对` 区域并生成配对码
   - 可直接让 iOS App 扫码完成填充。

7. 在 iOS App 发起配对并连接
   - 成功后可查看项目、创建会话、发送任务。

8. 日常使用
   - 在移动端提交需求。
   - 在需要时审批命令/补丁。
   - 在 Mac 侧通过“日志/安全/项目权限”面板持续监控。

## 推荐使用流程

1. 先在同一局域网内完成联调与稳定性验证。
2. 再按需开放公网访问。
3. 对外网设备使用“指定项目”策略，最小化访问范围。
4. 定期检查设备列表并撤销不再使用的设备授权。

## 常见问题（FAQ）

1. 已安装 Codex CLI，但应用里显示未检测到？
   - 常见原因是 GUI 进程未读取到最新 `PATH`。重启应用或修正系统 PATH 后重试。

2. 手机发现不到服务端？
   - 确认 Mac 与手机在同一网段，且网络策略允许局域网连接；检查防火墙与端口放行。

3. 配对码总是失败？
   - 配对码一次性且有时效，过期后请重新生成；同时确认 Host/端口输入正确。

4. AI 请求失败？
   - 检查 AI 出网策略是否开启；如走 OpenAI API，确认 `OPENAI_API_KEY` 有效。

5. 如何限制某台设备只能访问部分项目？
   - 在 `项目权限` 面板中选择对应“设备 + 工作区”，将策略改为“指定项目”并保存。

## 联系与下载

- 联系邮箱：`mellong@qq.com`
- iOS App 下载：<https://apps.apple.com/app/id6759236231>


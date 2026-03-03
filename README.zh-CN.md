# 🦞 OpenClaw — 个人 AI 助手

<p align="center">
    <picture>
        <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text-dark.png">
        <img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.png" alt="OpenClaw" width="500">
    </picture>
</p>

<p align="center">
  <strong>EXFOLIATE! EXFOLIATE!</strong>
</p>

<p align="center">
  <a href="https://github.com/openclaw/openclaw/actions/workflows/ci.yml?branch=main"><img src="https://img.shields.io/github/actions/workflow/status/openclaw/openclaw/ci.yml?branch=main&style=for-the-badge" alt="CI status"></a>
  <a href="https://github.com/openclaw/openclaw/releases"><img src="https://img.shields.io/github/v/release/openclaw/openclaw?include_prereleases&style=for-the-badge" alt="GitHub release"></a>
  <a href="https://discord.gg/clawd"><img src="https://img.shields.io/discord/1456350064065904867?label=Discord&logo=discord&logoColor=white&color=5865F2&style=for-the-badge" alt="Discord"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="MIT License"></a>
</p>

**OpenClaw** 是一个运行在你自己设备上的_个人 AI 助手_。
它会在你已经在使用的渠道里回复你（WhatsApp、Telegram、Slack、Discord、Google Chat、Signal、iMessage、BlueBubbles、IRC、Microsoft Teams、Matrix、Feishu、LINE、Mattermost、Nextcloud Talk、Nostr、Synology Chat、Tlon、Twitch、Zalo、Zalo Personal、WebChat）。它还能在 macOS/iOS/Android 上进行语音输入输出，并渲染一个由你控制的实时 Canvas。Gateway 只是控制平面，真正的产品是这个助手本身。

如果你想要一个个人专属、单用户、感觉本地化、快速且常驻在线的助手，就是它。

[English](README.md) | [简体中文](README.zh-CN.md)

[网站](https://openclaw.ai) · [文档](https://docs.openclaw.ai) · [愿景](VISION.md) · [DeepWiki](https://deepwiki.com/openclaw/openclaw) · [快速开始](https://docs.openclaw.ai/start/getting-started) · [更新](https://docs.openclaw.ai/install/updating) · [展示](https://docs.openclaw.ai/start/showcase) · [常见问题](https://docs.openclaw.ai/help/faq) · [向导](https://docs.openclaw.ai/start/wizard) · [Nix](https://github.com/openclaw/nix-openclaw) · [Docker](https://docs.openclaw.ai/install/docker) · [Discord](https://discord.gg/clawd)

推荐的安装方式：在终端里运行引导向导（`openclaw onboard`）。
向导会一步步带你完成 gateway、workspace、channels 和 skills 的设置。CLI 向导是推荐路径，并且可在 **macOS、Linux 和 Windows（通过 WSL2，强烈推荐）** 上使用。
支持 npm、pnpm 或 bun。
首次安装？从这里开始：[快速开始](https://docs.openclaw.ai/start/getting-started)

## 赞助商

| OpenAI                                                            | Vercel                                                            | Blacksmith                                                                   | Convex                                                                |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ---------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| [![OpenAI](docs/assets/sponsors/openai.svg)](https://openai.com/) | [![Vercel](docs/assets/sponsors/vercel.svg)](https://vercel.com/) | [![Blacksmith](docs/assets/sponsors/blacksmith.svg)](https://blacksmith.sh/) | [![Convex](docs/assets/sponsors/convex.svg)](https://www.convex.dev/) |

**订阅（OAuth）：**

- **[OpenAI](https://openai.com/)**（ChatGPT/Codex）

模型说明：虽然支持很多 provider 和 model，但为了获得最佳体验并降低 prompt injection 风险，建议使用你能访问到的最新一代最强模型。参见[引导说明](https://docs.openclaw.ai/start/onboarding)。

## 模型（选择与认证）

- 模型配置与 CLI：[Models](https://docs.openclaw.ai/concepts/models)
- 认证配置轮换（OAuth vs API keys）与回退：[Model failover](https://docs.openclaw.ai/concepts/model-failover)

## 安装（推荐）

运行时：**Node ≥22**。

```bash
npm install -g openclaw@latest
# or: pnpm add -g openclaw@latest

openclaw onboard --install-daemon
```

向导会安装 Gateway 后台服务（launchd/systemd 用户服务），确保它持续运行。

## 快速开始（TL;DR）

运行时：**Node ≥22**。

完整的新手指南（认证、配对、渠道）：[快速开始](https://docs.openclaw.ai/start/getting-started)

```bash
openclaw onboard --install-daemon

openclaw gateway --port 18789 --verbose

# 发送一条消息
openclaw message send --to +1234567890 --message "Hello from OpenClaw"

# 和助手对话（可选：回传到任何已连接渠道：WhatsApp/Telegram/Slack/Discord/Google Chat/Signal/iMessage/BlueBubbles/IRC/Microsoft Teams/Matrix/Feishu/LINE/Mattermost/Nextcloud Talk/Nostr/Synology Chat/Tlon/Twitch/Zalo/Zalo Personal/WebChat）
openclaw agent --message "Ship checklist" --thinking high
```

要升级？参见[更新指南](https://docs.openclaw.ai/install/updating)（并运行 `openclaw doctor`）。

## 开发通道

- **stable**：正式标签版本（`vYYYY.M.D` 或 `vYYYY.M.D-<patch>`），npm dist-tag 为 `latest`。
- **beta**：预发布标签（`vYYYY.M.D-beta.N`），npm dist-tag 为 `beta`（可能没有 macOS app）。
- **dev**：`main` 分支的滚动版本，npm dist-tag 为 `dev`（发布时）。

切换通道（git + npm）：`openclaw update --channel stable|beta|dev`。
详情参见：[Development channels](https://docs.openclaw.ai/install/development-channels)。

## 从源码运行（开发）

从源码构建时推荐使用 `pnpm`。如果要直接运行 TypeScript，Bun 是可选的。

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw

pnpm install
pnpm ui:build # 首次运行会自动安装 UI 依赖
pnpm build

pnpm openclaw onboard --install-daemon

# 开发循环（TS 变更自动重载）
pnpm gateway:watch
```

说明：`pnpm openclaw ...` 会直接运行 TypeScript（通过 `tsx`）。`pnpm build` 会生成 `dist/`，供 Node 或打包后的 `openclaw` 二进制运行。

## 安全默认值（私信访问）

OpenClaw 会连接真实的消息渠道。请把收到的私信视为**不可信输入**。

完整安全指南：[Security](https://docs.openclaw.ai/gateway/security)

在 Telegram/WhatsApp/Signal/iMessage/Microsoft Teams/Discord/Google Chat/Slack 上的默认行为：

- **DM 配对**（`dmPolicy="pairing"` / `channels.discord.dmPolicy="pairing"` / `channels.slack.dmPolicy="pairing"`；旧配置：`channels.discord.dm.policy`、`channels.slack.dm.policy`）：未知发送者会收到一个简短的配对码，机器人不会处理他们的消息。
- 使用以下命令批准：`openclaw pairing approve <channel> <code>`（之后发送者会加入本地 allowlist 存储）。
- 如果要公开接受私信，需要显式启用：设置 `dmPolicy="open"`，并在渠道 allowlist 中加入 `"*"`（`allowFrom` / `channels.discord.allowFrom` / `channels.slack.allowFrom`；旧配置：`channels.discord.dm.allowFrom`、`channels.slack.dm.allowFrom`）。

运行 `openclaw doctor` 可发现高风险或配置错误的 DM 策略。

## 亮点

- **[本地优先 Gateway](https://docs.openclaw.ai/gateway)**：用于会话、渠道、工具和事件的统一控制平面。
- **[多渠道收件箱](https://docs.openclaw.ai/channels)**：WhatsApp、Telegram、Slack、Discord、Google Chat、Signal、BlueBubbles（iMessage）、iMessage（legacy）、IRC、Microsoft Teams、Matrix、Feishu、LINE、Mattermost、Nextcloud Talk、Nostr、Synology Chat、Tlon、Twitch、Zalo、Zalo Personal、WebChat、macOS、iOS/Android。
- **[多 agent 路由](https://docs.openclaw.ai/gateway/configuration)**：按入站渠道、账号、对端把消息路由到隔离的 agents（workspace 和每个 agent 的 session）。
- **[Voice Wake](https://docs.openclaw.ai/nodes/voicewake) + [Talk Mode](https://docs.openclaw.ai/nodes/talk)**：macOS/iOS 上支持唤醒词，Android 上支持连续语音（ElevenLabs + 系统 TTS 回退）。
- **[实时 Canvas](https://docs.openclaw.ai/platforms/mac/canvas)**：agent 驱动的可视化工作区，支持 [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)。
- **[一等公民工具](https://docs.openclaw.ai/tools)**：浏览器、canvas、nodes、cron、sessions，以及 Discord/Slack 动作。
- **[伴随应用](https://docs.openclaw.ai/platforms/macos)**：macOS 菜单栏应用，以及 iOS/Android [nodes](https://docs.openclaw.ai/nodes)。
- **[引导流程](https://docs.openclaw.ai/start/wizard) + [skills](https://docs.openclaw.ai/tools/skills)**：通过向导完成设置，支持 bundled/managed/workspace skills。

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=openclaw/openclaw&type=date&legend=top-left)](https://www.star-history.com/#openclaw/openclaw&type=date&legend=top-left)

## 我们目前构建的全部内容

### 核心平台

- [Gateway WS control plane](https://docs.openclaw.ai/gateway)，包含 sessions、presence、config、cron、webhooks、[Control UI](https://docs.openclaw.ai/web) 和 [Canvas host](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)。
- [CLI surface](https://docs.openclaw.ai/tools/agent-send)：gateway、agent、send、[wizard](https://docs.openclaw.ai/start/wizard) 和 [doctor](https://docs.openclaw.ai/gateway/doctor)。
- [Pi agent runtime](https://docs.openclaw.ai/concepts/agent)（RPC 模式），支持 tool streaming 和 block streaming。
- [Session model](https://docs.openclaw.ai/concepts/session)：直接聊天使用 `main`，支持群组隔离、激活模式、队列模式和 reply-back。群组规则参见：[Groups](https://docs.openclaw.ai/channels/groups)。
- [Media pipeline](https://docs.openclaw.ai/nodes/images)：图片/音频/视频、转录 hooks、大小限制、临时文件生命周期。音频细节参见：[Audio](https://docs.openclaw.ai/nodes/audio)。

### 渠道

- [Channels](https://docs.openclaw.ai/channels)：[WhatsApp](https://docs.openclaw.ai/channels/whatsapp)（Baileys）、[Telegram](https://docs.openclaw.ai/channels/telegram)（grammY）、[Slack](https://docs.openclaw.ai/channels/slack)（Bolt）、[Discord](https://docs.openclaw.ai/channels/discord)（discord.js）、[Google Chat](https://docs.openclaw.ai/channels/googlechat)（Chat API）、[Signal](https://docs.openclaw.ai/channels/signal)（signal-cli）、[BlueBubbles](https://docs.openclaw.ai/channels/bluebubbles)（iMessage，推荐）、[iMessage](https://docs.openclaw.ai/channels/imessage)（legacy imsg）、[IRC](https://docs.openclaw.ai/channels/irc)、[Microsoft Teams](https://docs.openclaw.ai/channels/msteams)、[Matrix](https://docs.openclaw.ai/channels/matrix)、[Feishu](https://docs.openclaw.ai/channels/feishu)、[LINE](https://docs.openclaw.ai/channels/line)、[Mattermost](https://docs.openclaw.ai/channels/mattermost)、[Nextcloud Talk](https://docs.openclaw.ai/channels/nextcloud-talk)、[Nostr](https://docs.openclaw.ai/channels/nostr)、[Synology Chat](https://docs.openclaw.ai/channels/synology-chat)、[Tlon](https://docs.openclaw.ai/channels/tlon)、[Twitch](https://docs.openclaw.ai/channels/twitch)、[Zalo](https://docs.openclaw.ai/channels/zalo)、[Zalo Personal](https://docs.openclaw.ai/channels/zalouser)、[WebChat](https://docs.openclaw.ai/web/webchat)。
- [群组路由](https://docs.openclaw.ai/channels/group-messages)：mention gating、reply tags、按渠道分块与路由。渠道规则参见：[Channels](https://docs.openclaw.ai/channels)。

### 应用与 nodes

- [macOS app](https://docs.openclaw.ai/platforms/macos)：菜单栏控制平面、[Voice Wake](https://docs.openclaw.ai/nodes/voicewake)/PTT、[Talk Mode](https://docs.openclaw.ai/nodes/talk) 浮层、[WebChat](https://docs.openclaw.ai/web/webchat)、调试工具，以及 [remote gateway](https://docs.openclaw.ai/gateway/remote) 控制。
- [iOS node](https://docs.openclaw.ai/platforms/ios)：[Canvas](https://docs.openclaw.ai/platforms/mac/canvas)、[Voice Wake](https://docs.openclaw.ai/nodes/voicewake)、[Talk Mode](https://docs.openclaw.ai/nodes/talk)、相机、屏幕录制、Bonjour 和设备配对。
- [Android node](https://docs.openclaw.ai/platforms/android)：Connect 标签页（设置码/手动模式）、聊天会话、语音标签页、[Canvas](https://docs.openclaw.ai/platforms/mac/canvas)、相机/屏幕录制，以及 Android 设备命令（通知/定位/SMS/照片/联系人/日历/运动/app 更新）。
- [macOS node mode](https://docs.openclaw.ai/nodes)：暴露 system.run/system.notify 与 canvas/camera。

### 工具与自动化

- [Browser control](https://docs.openclaw.ai/tools/browser)：专用 openclaw Chrome/Chromium、快照、动作、上传、profiles。
- [Canvas](https://docs.openclaw.ai/platforms/mac/canvas)：[A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui) push/reset、eval、snapshot。
- [Nodes](https://docs.openclaw.ai/nodes)：camera snap/clip、screen record、[location.get](https://docs.openclaw.ai/nodes/location-command)、notifications。
- [Cron + wakeups](https://docs.openclaw.ai/automation/cron-jobs)、[webhooks](https://docs.openclaw.ai/automation/webhook)、[Gmail Pub/Sub](https://docs.openclaw.ai/automation/gmail-pubsub)。
- [Skills platform](https://docs.openclaw.ai/tools/skills)：bundled、managed 和 workspace skills，带安装门控和 UI。

### 运行时与安全

- [渠道路由](https://docs.openclaw.ai/channels/channel-routing)、[重试策略](https://docs.openclaw.ai/concepts/retry) 和 [流式/分块](https://docs.openclaw.ai/concepts/streaming)。
- [Presence](https://docs.openclaw.ai/concepts/presence)、[输入指示器](https://docs.openclaw.ai/concepts/typing-indicators) 和 [用量跟踪](https://docs.openclaw.ai/concepts/usage-tracking)。
- [Models](https://docs.openclaw.ai/concepts/models)、[model failover](https://docs.openclaw.ai/concepts/model-failover) 和 [session pruning](https://docs.openclaw.ai/concepts/session-pruning)。
- [Security](https://docs.openclaw.ai/gateway/security) 与 [troubleshooting](https://docs.openclaw.ai/channels/troubleshooting)。

### 运维与打包

- [Control UI](https://docs.openclaw.ai/web) + [WebChat](https://docs.openclaw.ai/web/webchat) 由 Gateway 直接提供。
- [Tailscale Serve/Funnel](https://docs.openclaw.ai/gateway/tailscale) 或 [SSH tunnels](https://docs.openclaw.ai/gateway/remote)，支持 token/password 认证。
- 用于声明式配置的 [Nix mode](https://docs.openclaw.ai/install/nix)；以及基于 [Docker](https://docs.openclaw.ai/install/docker) 的安装方式。
- [Doctor](https://docs.openclaw.ai/gateway/doctor) 迁移、[logging](https://docs.openclaw.ai/logging)。

## 工作原理（简版）

```
WhatsApp / Telegram / Slack / Discord / Google Chat / Signal / iMessage / BlueBubbles / IRC / Microsoft Teams / Matrix / Feishu / LINE / Mattermost / Nextcloud Talk / Nostr / Synology Chat / Tlon / Twitch / Zalo / Zalo Personal / WebChat
               │
               ▼
┌───────────────────────────────┐
│            Gateway            │
│           （控制平面）         │
│     ws://127.0.0.1:18789      │
└──────────────┬────────────────┘
               │
               ├─ Pi agent (RPC)
               ├─ CLI (openclaw …)
               ├─ WebChat UI
               ├─ macOS app
               └─ iOS / Android nodes
```

## 关键子系统

- **[Gateway WebSocket network](https://docs.openclaw.ai/concepts/architecture)**：单一 WS 控制平面，用于连接客户端、工具和事件（运维参见 [Gateway runbook](https://docs.openclaw.ai/gateway)）。
- **[Tailscale exposure](https://docs.openclaw.ai/gateway/tailscale)**：通过 Serve/Funnel 暴露 Gateway dashboard + WS（远程访问参见 [Remote](https://docs.openclaw.ai/gateway/remote)）。
- **[Browser control](https://docs.openclaw.ai/tools/browser)**：由 openclaw 管理的 Chrome/Chromium，支持 CDP 控制。
- **[Canvas + A2UI](https://docs.openclaw.ai/platforms/mac/canvas)**：agent 驱动的可视化工作区（A2UI host 参见 [Canvas/A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)）。
- **[Voice Wake](https://docs.openclaw.ai/nodes/voicewake) + [Talk Mode](https://docs.openclaw.ai/nodes/talk)**：macOS/iOS 上支持唤醒词，Android 上支持连续语音。
- **[Nodes](https://docs.openclaw.ai/nodes)**：Canvas、camera snap/clip、screen record、`location.get`、notifications，以及仅限 macOS 的 `system.run`/`system.notify`。

## Tailscale 访问（Gateway 仪表盘）

当 Gateway 仍然绑定在 loopback 时，OpenClaw 可以自动配置 Tailscale **Serve**（仅 tailnet）或 **Funnel**（公开）。配置 `gateway.tailscale.mode`：

- `off`：不启用 Tailscale 自动化（默认）。
- `serve`：通过 `tailscale serve` 提供仅 tailnet 可访问的 HTTPS（默认使用 Tailscale identity headers）。
- `funnel`：通过 `tailscale funnel` 提供公开 HTTPS（需要共享密码认证）。

说明：

- 开启 Serve/Funnel 时，`gateway.bind` 必须保持为 `loopback`（OpenClaw 会强制执行）。
- 通过设置 `gateway.auth.mode: "password"` 或 `gateway.auth.allowTailscale: false`，可以强制 Serve 也要求密码。
- 如果没有设置 `gateway.auth.mode: "password"`，Funnel 会拒绝启动。
- 可选：设置 `gateway.tailscale.resetOnExit`，在退出时撤销 Serve/Funnel 配置。

详情参见：[Tailscale guide](https://docs.openclaw.ai/gateway/tailscale) · [Web surfaces](https://docs.openclaw.ai/web)

## 远程 Gateway（Linux 很合适）

完全可以把 Gateway 运行在一个小型 Linux 实例上。客户端（macOS app、CLI、WebChat）可以通过 **Tailscale Serve/Funnel** 或 **SSH tunnels** 连接，你仍然可以配对设备 nodes（macOS/iOS/Android）以便在需要时执行设备本地动作。

- **Gateway host** 默认运行 exec tool 和各类渠道连接。
- **Device nodes** 通过 `node.invoke` 运行设备本地动作（`system.run`、相机、屏幕录制、通知）。
  简言之：exec 在 Gateway 所在位置执行；设备动作在设备所在位置执行。

详情参见：[Remote access](https://docs.openclaw.ai/gateway/remote) · [Nodes](https://docs.openclaw.ai/nodes) · [Security](https://docs.openclaw.ai/gateway/security)

## 通过 Gateway 协议管理 macOS 权限

macOS app 可以运行在 **node mode** 下，并通过 Gateway WebSocket（`node.list` / `node.describe`）公布自己的能力和权限映射。随后客户端可以通过 `node.invoke` 执行本地动作：

- `system.run` 会运行本地命令并返回 stdout/stderr/exit code；如果设置 `needsScreenRecording: true`，则需要屏幕录制权限（否则会得到 `PERMISSION_MISSING`）。
- `system.notify` 会发送用户通知；若通知权限被拒绝则失败。
- `canvas.*`、`camera.*`、`screen.record` 和 `location.get` 也通过 `node.invoke` 路由，并遵循 TCC 权限状态。

提升 bash 权限（host permissions）与 macOS TCC 是分离的：

- 使用 `/elevated on|off` 切换每个 session 的提升权限（前提是已启用并在 allowlist 中）。
- Gateway 会通过 `sessions.patch`（WS 方法）持久化这个每会话开关，同时还会保存 `thinkingLevel`、`verboseLevel`、`model`、`sendPolicy` 和 `groupActivation`。

详情参见：[Nodes](https://docs.openclaw.ai/nodes) · [macOS app](https://docs.openclaw.ai/platforms/macos) · [Gateway protocol](https://docs.openclaw.ai/concepts/architecture)

## Agent to Agent（sessions\_\* 工具）

- 可用这些工具在不同 session 间协同工作，而不用来回切换聊天渠道。
- `sessions_list`：发现活跃 session（agents）及其元数据。
- `sessions_history`：获取某个 session 的转录日志。
- `sessions_send`：给另一个 session 发消息；可选 reply-back ping-pong 和 announce step（`REPLY_SKIP`、`ANNOUNCE_SKIP`）。

详情参见：[Session tools](https://docs.openclaw.ai/concepts/session-tool)

## Skills registry（ClawHub）

ClawHub 是一个极简 skill 注册表。启用 ClawHub 后，agent 可以自动搜索 skills，并在需要时拉取新的技能。

[ClawHub](https://clawhub.com)

## 聊天命令

把这些命令发送到 WhatsApp/Telegram/Slack/Google Chat/Microsoft Teams/WebChat 中即可（群组命令仅 owner 可用）：

- `/status`：紧凑会话状态（model + tokens，支持时显示 cost）
- `/new` 或 `/reset`：重置会话
- `/compact`：压缩会话上下文（summary）
- `/think <level>`：off|minimal|low|medium|high|xhigh（仅限 GPT-5.2 + Codex models）
- `/verbose on|off`
- `/usage off|tokens|full`：每条响应的 usage footer
- `/restart`：重启 gateway（群组中仅 owner 可用）
- `/activation mention|always`：切换群组激活模式（仅群组）

## Apps（可选）

单独使用 Gateway 就已经有很好的体验。所有 app 都是可选的，用于增加额外能力。

如果你计划构建或运行这些 companion apps，请参照对应平台的 runbook。

### macOS（OpenClaw.app）（可选）

- Gateway 和健康状态的菜单栏控制。
- Voice Wake + push-to-talk 浮层。
- WebChat + 调试工具。
- 通过 SSH 远程控制 gateway。

说明：要让 macOS 权限在重新构建后依然生效，需要签名构建（参见 `docs/mac/permissions.md`）。

### iOS node（可选）

- 通过 Gateway WebSocket 作为 node 配对（设备配对）。
- 转发语音触发 + Canvas 界面。
- 通过 `openclaw nodes …` 控制。

运行说明：[iOS connect](https://docs.openclaw.ai/platforms/ios)

### Android node（可选）

- 通过设备配对作为 WS node（`openclaw devices ...`）。
- 提供 Connect/Chat/Voice 标签页，以及 Canvas、相机、屏幕采集和 Android 设备命令族。
- 运行说明：[Android connect](https://docs.openclaw.ai/platforms/android)。

## Agent workspace 与 skills

- Workspace 根目录：`~/.openclaw/workspace`（可通过 `agents.defaults.workspace` 配置）。
- 注入的 prompt 文件：`AGENTS.md`、`SOUL.md`、`TOOLS.md`。
- Skills：`~/.openclaw/workspace/skills/<skill>/SKILL.md`。

## 配置

最小 `~/.openclaw/openclaw.json` 配置（model + defaults）：

```json5
{
  agent: {
    model: "anthropic/claude-opus-4-6",
  },
}
```

[完整配置参考（所有 key 与示例）](https://docs.openclaw.ai/gateway/configuration)

## 安全模型（重要）

- **默认行为**：在 **main** session 中，tools 运行在宿主机上，所以当只有你自己使用时，agent 拥有完整访问权限。
- **群组/渠道安全**：设置 `agents.defaults.sandbox.mode: "non-main"` 后，**非 main session**（群组/渠道）会在每个 session 对应的 Docker sandbox 中运行；这时 bash 也在 Docker 里执行。
- **Sandbox 默认值**：allowlist 包含 `bash`、`process`、`read`、`write`、`edit`、`sessions_list`、`sessions_history`、`sessions_send`、`sessions_spawn`；denylist 包含 `browser`、`canvas`、`nodes`、`cron`、`discord`、`gateway`。

详情参见：[Security guide](https://docs.openclaw.ai/gateway/security) · [Docker + sandboxing](https://docs.openclaw.ai/install/docker) · [Sandbox config](https://docs.openclaw.ai/gateway/configuration)

### [WhatsApp](https://docs.openclaw.ai/channels/whatsapp)

- 关联设备：`pnpm openclaw channels login`（凭据保存到 `~/.openclaw/credentials`）。
- 通过 `channels.whatsapp.allowFrom` 设置谁可以和助手对话。
- 如果设置了 `channels.whatsapp.groups`，它会变成群组 allowlist；加入 `"*"` 可允许所有群组。

### [Telegram](https://docs.openclaw.ai/channels/telegram)

- 设置 `TELEGRAM_BOT_TOKEN` 或 `channels.telegram.botToken`（环境变量优先）。
- 可选：设置 `channels.telegram.groups`（配合 `channels.telegram.groups."*".requireMention`）；设置后它会成为群组 allowlist（加入 `"*"` 可允许所有）。按需也可设置 `channels.telegram.allowFrom` 或 `channels.telegram.webhookUrl` + `channels.telegram.webhookSecret`。

```json5
{
  channels: {
    telegram: {
      botToken: "123456:ABCDEF",
    },
  },
}
```

### [Slack](https://docs.openclaw.ai/channels/slack)

- 设置 `SLACK_BOT_TOKEN` + `SLACK_APP_TOKEN`（或 `channels.slack.botToken` + `channels.slack.appToken`）。

### [Discord](https://docs.openclaw.ai/channels/discord)

- 设置 `DISCORD_BOT_TOKEN` 或 `channels.discord.token`（环境变量优先）。
- 可选：按需设置 `commands.native`、`commands.text` 或 `commands.useAccessGroups`，以及 `channels.discord.allowFrom`、`channels.discord.guilds` 或 `channels.discord.mediaMaxMb`。

```json5
{
  channels: {
    discord: {
      token: "1234abcd",
    },
  },
}
```

### [Signal](https://docs.openclaw.ai/channels/signal)

- 需要 `signal-cli`，并配置 `channels.signal` 配置段。

### [BlueBubbles（iMessage）](https://docs.openclaw.ai/channels/bluebubbles)

- **推荐的** iMessage 集成方式。
- 配置 `channels.bluebubbles.serverUrl` + `channels.bluebubbles.password`，以及 webhook（`channels.bluebubbles.webhookPath`）。
- BlueBubbles server 运行在 macOS 上；Gateway 可以运行在 macOS 或其他地方。

### [iMessage（legacy）](https://docs.openclaw.ai/channels/imessage)

- 基于 `imsg` 的旧版仅 macOS 集成方式（Messages 必须已登录）。
- 如果设置了 `channels.imessage.groups`，它会变成群组 allowlist；加入 `"*"` 可允许所有群组。

### [Microsoft Teams](https://docs.openclaw.ai/channels/msteams)

- 配置 Teams app + Bot Framework，然后添加 `msteams` 配置段。
- 通过 `msteams.allowFrom` 设置谁可以对话；群组访问可通过 `msteams.groupAllowFrom` 或 `msteams.groupPolicy: "open"` 配置。

### [WebChat](https://docs.openclaw.ai/web/webchat)

- 使用 Gateway WebSocket；没有单独的 WebChat 端口或配置。

浏览器控制（可选）：

```json5
{
  browser: {
    enabled: true,
    color: "#FF4500",
  },
}
```

## 文档

当你完成引导流程、需要更深入的参考时，请使用这些文档。

- [先从文档首页开始，了解导航和内容分布。](https://docs.openclaw.ai)
- [阅读架构总览，理解 gateway 与协议模型。](https://docs.openclaw.ai/concepts/architecture)
- [需要所有配置项和示例时，使用完整配置参考。](https://docs.openclaw.ai/gateway/configuration)
- [按标准方式运行 Gateway，请参考运维 runbook。](https://docs.openclaw.ai/gateway)
- [了解 Control UI/Web 界面的工作方式，以及如何安全暴露它们。](https://docs.openclaw.ai/web)
- [了解如何通过 SSH tunnels 或 tailnets 进行远程访问。](https://docs.openclaw.ai/gateway/remote)
- [按引导向导流程完成分步设置。](https://docs.openclaw.ai/start/wizard)
- [通过 webhook 接入外部触发器。](https://docs.openclaw.ai/automation/webhook)
- [设置 Gmail Pub/Sub 触发器。](https://docs.openclaw.ai/automation/gmail-pubsub)
- [了解 macOS 菜单栏 companion 的细节。](https://docs.openclaw.ai/platforms/mac/menu-bar)
- [平台指南：Windows (WSL2)](https://docs.openclaw.ai/platforms/windows)、[Linux](https://docs.openclaw.ai/platforms/linux)、[macOS](https://docs.openclaw.ai/platforms/macos)、[iOS](https://docs.openclaw.ai/platforms/ios)、[Android](https://docs.openclaw.ai/platforms/android)
- [使用故障排查指南定位常见失败。](https://docs.openclaw.ai/channels/troubleshooting)
- [在暴露任何能力之前先阅读安全指南。](https://docs.openclaw.ai/gateway/security)

## 高级文档（发现与控制）

- [Discovery + transports](https://docs.openclaw.ai/gateway/discovery)
- [Bonjour/mDNS](https://docs.openclaw.ai/gateway/bonjour)
- [Gateway pairing](https://docs.openclaw.ai/gateway/pairing)
- [Remote gateway README](https://docs.openclaw.ai/gateway/remote-gateway-readme)
- [Control UI](https://docs.openclaw.ai/web/control-ui)
- [Dashboard](https://docs.openclaw.ai/web/dashboard)

## 运维与故障排查

- [Health checks](https://docs.openclaw.ai/gateway/health)
- [Gateway lock](https://docs.openclaw.ai/gateway/gateway-lock)
- [Background process](https://docs.openclaw.ai/gateway/background-process)
- [Browser troubleshooting (Linux)](https://docs.openclaw.ai/tools/browser-linux-troubleshooting)
- [Logging](https://docs.openclaw.ai/logging)

## 深入阅读

- [Agent loop](https://docs.openclaw.ai/concepts/agent-loop)
- [Presence](https://docs.openclaw.ai/concepts/presence)
- [TypeBox schemas](https://docs.openclaw.ai/concepts/typebox)
- [RPC adapters](https://docs.openclaw.ai/reference/rpc)
- [Queue](https://docs.openclaw.ai/concepts/queue)

## Workspace 与 skills

- [Skills config](https://docs.openclaw.ai/tools/skills-config)
- [Default AGENTS](https://docs.openclaw.ai/reference/AGENTS.default)
- [Templates: AGENTS](https://docs.openclaw.ai/reference/templates/AGENTS)
- [Templates: BOOTSTRAP](https://docs.openclaw.ai/reference/templates/BOOTSTRAP)
- [Templates: IDENTITY](https://docs.openclaw.ai/reference/templates/IDENTITY)
- [Templates: SOUL](https://docs.openclaw.ai/reference/templates/SOUL)
- [Templates: TOOLS](https://docs.openclaw.ai/reference/templates/TOOLS)
- [Templates: USER](https://docs.openclaw.ai/reference/templates/USER)

## 平台内部实现

- [macOS dev setup](https://docs.openclaw.ai/platforms/mac/dev-setup)
- [macOS menu bar](https://docs.openclaw.ai/platforms/mac/menu-bar)
- [macOS voice wake](https://docs.openclaw.ai/platforms/mac/voicewake)
- [iOS node](https://docs.openclaw.ai/platforms/ios)
- [Android node](https://docs.openclaw.ai/platforms/android)
- [Windows (WSL2)](https://docs.openclaw.ai/platforms/windows)
- [Linux app](https://docs.openclaw.ai/platforms/linux)

## 邮件 hooks（Gmail）

- [docs.openclaw.ai/gmail-pubsub](https://docs.openclaw.ai/automation/gmail-pubsub)

## Molty

OpenClaw 是为 **Molty** 打造的，一个太空龙虾 AI 助手。🦞
由 Peter Steinberger 和社区共同构建。

- [openclaw.ai](https://openclaw.ai)
- [soul.md](https://soul.md)
- [steipete.me](https://steipete.me)
- [@openclaw](https://x.com/openclaw)

## 社区

参见 [CONTRIBUTING.md](CONTRIBUTING.md) 了解贡献指南、维护者信息和如何提交 PR。
欢迎 AI/vibe-coded PR！🤖

特别感谢 [Mario Zechner](https://mariozechner.at/) 的支持，以及 [pi-mono](https://github.com/badlogic/pi-mono)。
也特别感谢 Adam Doppelt 为 lobster.bot 所做的贡献。

感谢所有 clawtributors：

<p align="left">
  <a href="https://github.com/steipete"><img src="https://avatars.githubusercontent.com/u/58493?v=4&s=48" width="48" height="48" alt="steipete" title="steipete"/></a> <a href="https://github.com/vincentkoc"><img src="https://avatars.githubusercontent.com/u/25068?v=4&s=48" width="48" height="48" alt="vincentkoc" title="vincentkoc"/></a> <a href="https://github.com/vignesh07"><img src="https://avatars.githubusercontent.com/u/1436853?v=4&s=48" width="48" height="48" alt="vignesh07" title="vignesh07"/></a> <a href="https://github.com/obviyus"><img src="https://avatars.githubusercontent.com/u/22031114?v=4&s=48" width="48" height="48" alt="obviyus" title="obviyus"/></a> <a href="https://github.com/mbelinky"><img src="https://avatars.githubusercontent.com/u/132747814?v=4&s=48" width="48" height="48" alt="Mariano Belinky" title="Mariano Belinky"/></a> <a href="https://github.com/sebslight"><img src="https://avatars.githubusercontent.com/u/19554889?v=4&s=48" width="48" height="48" alt="sebslight" title="sebslight"/></a> <a href="https://github.com/gumadeiras"><img src="https://avatars.githubusercontent.com/u/5599352?v=4&s=48" width="48" height="48" alt="gumadeiras" title="gumadeiras"/></a> <a href="https://github.com/Takhoffman"><img src="https://avatars.githubusercontent.com/u/781889?v=4&s=48" width="48" height="48" alt="Takhoffman" title="Takhoffman"/></a> <a href="https://github.com/thewilloftheshadow"><img src="https://avatars.githubusercontent.com/u/35580099?v=4&s=48" width="48" height="48" alt="thewilloftheshadow" title="thewilloftheshadow"/></a> <a href="https://github.com/cpojer"><img src="https://avatars.githubusercontent.com/u/13352?v=4&s=48" width="48" height="48" alt="cpojer" title="cpojer"/></a>
  <a href="https://github.com/tyler6204"><img src="https://avatars.githubusercontent.com/u/64381258?v=4&s=48" width="48" height="48" alt="tyler6204" title="tyler6204"/></a> <a href="https://github.com/joshp123"><img src="https://avatars.githubusercontent.com/u/1497361?v=4&s=48" width="48" height="48" alt="joshp123" title="joshp123"/></a> <a href="https://github.com/Glucksberg"><img src="https://avatars.githubusercontent.com/u/80581902?v=4&s=48" width="48" height="48" alt="Glucksberg" title="Glucksberg"/></a> <a href="https://github.com/mcaxtr"><img src="https://avatars.githubusercontent.com/u/7562095?v=4&s=48" width="48" height="48" alt="mcaxtr" title="mcaxtr"/></a> <a href="https://github.com/quotentiroler"><img src="https://avatars.githubusercontent.com/u/40643627?v=4&s=48" width="48" height="48" alt="quotentiroler" title="quotentiroler"/></a> <a href="https://github.com/osolmaz"><img src="https://avatars.githubusercontent.com/u/2453968?v=4&s=48" width="48" height="48" alt="osolmaz" title="osolmaz"/></a> <a href="https://github.com/Sid-Qin"><img src="https://avatars.githubusercontent.com/u/201593046?v=4&s=48" width="48" height="48" alt="Sid-Qin" title="Sid-Qin"/></a> <a href="https://github.com/joshavant"><img src="https://avatars.githubusercontent.com/u/830519?v=4&s=48" width="48" height="48" alt="joshavant" title="joshavant"/></a> <a href="https://github.com/shakkernerd"><img src="https://avatars.githubusercontent.com/u/165377636?v=4&s=48" width="48" height="48" alt="shakkernerd" title="shakkernerd"/></a> <a href="https://github.com/bmendonca3"><img src="https://avatars.githubusercontent.com/u/208517100?v=4&s=48" width="48" height="48" alt="bmendonca3" title="bmendonca3"/></a>
  <a href="https://github.com/mukhtharcm"><img src="https://avatars.githubusercontent.com/u/56378562?v=4&s=48" width="48" height="48" alt="mukhtharcm" title="mukhtharcm"/></a> <a href="https://github.com/zerone0x"><img src="https://avatars.githubusercontent.com/u/39543393?v=4&s=48" width="48" height="48" alt="zerone0x" title="zerone0x"/></a> <a href="https://github.com/mcinteerj"><img src="https://avatars.githubusercontent.com/u/3613653?v=4&s=48" width="48" height="48" alt="mcinteerj" title="mcinteerj"/></a> <a href="https://github.com/ngutman"><img src="https://avatars.githubusercontent.com/u/1540134?v=4&s=48" width="48" height="48" alt="ngutman" title="ngutman"/></a> <a href="https://github.com/lailoo"><img src="https://avatars.githubusercontent.com/u/20536249?v=4&s=48" width="48" height="48" alt="lailoo" title="lailoo"/></a> <a href="https://github.com/arosstale"><img src="https://avatars.githubusercontent.com/u/117890364?v=4&s=48" width="48" height="48" alt="arosstale" title="arosstale"/></a> <a href="https://github.com/rodrigouroz"><img src="https://avatars.githubusercontent.com/u/384037?v=4&s=48" width="48" height="48" alt="rodrigouroz" title="rodrigouroz"/></a> <a href="https://github.com/robbyczgw-cla"><img src="https://avatars.githubusercontent.com/u/239660374?v=4&s=48" width="48" height="48" alt="robbyczgw-cla" title="robbyczgw-cla"/></a> <a href="https://github.com/0xRaini"><img src="https://avatars.githubusercontent.com/u/190923101?v=4&s=48" width="48" height="48" alt="Elonito" title="Elonito"/></a> <a href="https://github.com/Clawborn"><img src="https://avatars.githubusercontent.com/u/261310391?v=4&s=48" width="48" height="48" alt="Clawborn" title="Clawborn"/></a>
  <a href="https://github.com/yinghaosang"><img src="https://avatars.githubusercontent.com/u/261132136?v=4&s=48" width="48" height="48" alt="yinghaosang" title="yinghaosang"/></a> <a href="https://github.com/BunsDev"><img src="https://avatars.githubusercontent.com/u/68980965?v=4&s=48" width="48" height="48" alt="BunsDev" title="BunsDev"/></a> <a href="https://github.com/christianklotz"><img src="https://avatars.githubusercontent.com/u/69443?v=4&s=48" width="48" height="48" alt="christianklotz" title="christianklotz"/></a> <a href="https://github.com/echoVic"><img src="https://avatars.githubusercontent.com/u/16428813?v=4&s=48" width="48" height="48" alt="echoVic" title="echoVic"/></a> <a href="https://github.com/coygeek"><img src="https://avatars.githubusercontent.com/u/65363919?v=4&s=48" width="48" height="48" alt="coygeek" title="coygeek"/></a> <a href="https://github.com/roshanasingh4"><img src="https://avatars.githubusercontent.com/u/88576930?v=4&s=48" width="48" height="48" alt="roshanasingh4" title="roshanasingh4"/></a> <a href="https://github.com/mneves75"><img src="https://avatars.githubusercontent.com/u/2423436?v=4&s=48" width="48" height="48" alt="mneves75" title="mneves75"/></a> <a href="https://github.com/joaohlisboa"><img src="https://avatars.githubusercontent.com/u/8200873?v=4&s=48" width="48" height="48" alt="joaohlisboa" title="joaohlisboa"/></a> <a href="https://github.com/bohdanpodvirnyi"><img src="https://avatars.githubusercontent.com/u/31819391?v=4&s=48" width="48" height="48" alt="bohdanpodvirnyi" title="bohdanpodvirnyi"/></a> <a href="https://github.com/Nachx639"><img src="https://avatars.githubusercontent.com/u/71144023?v=4&s=48" width="48" height="48" alt="nachx639" title="nachx639"/></a>
  <a href="https://github.com/onutc"><img src="https://avatars.githubusercontent.com/u/152018508?v=4&s=48" width="48" height="48" alt="onutc" title="onutc"/></a> <a href="https://github.com/VeriteIgiraneza"><img src="https://avatars.githubusercontent.com/u/69280208?v=4&s=48" width="48" height="48" alt="Verite Igiraneza" title="Verite Igiraneza"/></a> <a href="https://github.com/widingmarcus-cyber"><img src="https://avatars.githubusercontent.com/u/245375637?v=4&s=48" width="48" height="48" alt="widingmarcus-cyber" title="widingmarcus-cyber"/></a> <a href="https://github.com/akramcodez"><img src="https://avatars.githubusercontent.com/u/179671552?v=4&s=48" width="48" height="48" alt="akramcodez" title="akramcodez"/></a> <a href="https://github.com/aether-ai-agent"><img src="https://avatars.githubusercontent.com/u/261339948?v=4&s=48" width="48" height="48" alt="aether-ai-agent" title="aether-ai-agent"/></a> <a href="https://github.com/bjesuiter"><img src="https://avatars.githubusercontent.com/u/2365676?v=4&s=48" width="48" height="48" alt="bjesuiter" title="bjesuiter"/></a> <a href="https://github.com/MaudeBot"><img src="https://avatars.githubusercontent.com/u/255777700?v=4&s=48" width="48" height="48" alt="MaudeBot" title="MaudeBot"/></a> <a href="https://github.com/YuriNachos"><img src="https://avatars.githubusercontent.com/u/19365375?v=4&s=48" width="48" height="48" alt="YuriNachos" title="YuriNachos"/></a> <a href="https://github.com/chilu18"><img src="https://avatars.githubusercontent.com/u/7957943?v=4&s=48" width="48" height="48" alt="chilu18" title="chilu18"/></a> <a href="https://github.com/byungsker"><img src="https://avatars.githubusercontent.com/u/72309817?v=4&s=48" width="48" height="48" alt="byungsker" title="byungsker"/></a>
  <a href="https://github.com/dbhurley"><img src="https://avatars.githubusercontent.com/u/5251425?v=4&s=48" width="48" height="48" alt="dbhurley" title="dbhurley"/></a> <a href="https://github.com/JayMishra-source"><img src="https://avatars.githubusercontent.com/u/82963117?v=4&s=48" width="48" height="48" alt="JayMishra-source" title="JayMishra-source"/></a> <a href="https://github.com/iHildy"><img src="https://avatars.githubusercontent.com/u/25069719?v=4&s=48" width="48" height="48" alt="iHildy" title="iHildy"/></a> <a href="https://github.com/mudrii"><img src="https://avatars.githubusercontent.com/u/220262?v=4&s=48" width="48" height="48" alt="mudrii" title="mudrii"/></a> <a href="https://github.com/dlauer"><img src="https://avatars.githubusercontent.com/u/757041?v=4&s=48" width="48" height="48" alt="dlauer" title="dlauer"/></a> <a href="https://github.com/Solvely-Colin"><img src="https://avatars.githubusercontent.com/u/211764741?v=4&s=48" width="48" height="48" alt="Solvely-Colin" title="Solvely-Colin"/></a> <a href="https://github.com/czekaj"><img src="https://avatars.githubusercontent.com/u/1464539?v=4&s=48" width="48" height="48" alt="czekaj" title="czekaj"/></a> <a href="https://github.com/advaitpaliwal"><img src="https://avatars.githubusercontent.com/u/66044327?v=4&s=48" width="48" height="48" alt="advaitpaliwal" title="advaitpaliwal"/></a> <a href="https://github.com/lc0rp"><img src="https://avatars.githubusercontent.com/u/2609441?v=4&s=48" width="48" height="48" alt="lc0rp" title="lc0rp"/></a> <a href="https://github.com/grp06"><img src="https://avatars.githubusercontent.com/u/1573959?v=4&s=48" width="48" height="48" alt="grp06" title="grp06"/></a>
  <a href="https://github.com/HenryLoenwind"><img src="https://avatars.githubusercontent.com/u/1485873?v=4&s=48" width="48" height="48" alt="HenryLoenwind" title="HenryLoenwind"/></a> <a href="https://github.com/azade-c"><img src="https://avatars.githubusercontent.com/u/252790079?v=4&s=48" width="48" height="48" alt="azade-c" title="azade-c"/></a> <a href="https://github.com/Lukavyi"><img src="https://avatars.githubusercontent.com/u/1013690?v=4&s=48" width="48" height="48" alt="Lukavyi" title="Lukavyi"/></a> <a href="https://github.com/vrknetha"><img src="https://avatars.githubusercontent.com/u/20596261?v=4&s=48" width="48" height="48" alt="vrknetha" title="vrknetha"/></a> <a href="https://github.com/brandonwise"><img src="https://avatars.githubusercontent.com/u/21148772?v=4&s=48" width="48" height="48" alt="brandonwise" title="brandonwise"/></a> <a href="https://github.com/conroywhitney"><img src="https://avatars.githubusercontent.com/u/249891?v=4&s=48" width="48" height="48" alt="conroywhitney" title="conroywhitney"/></a> <a href="https://github.com/tobiasbischoff"><img src="https://avatars.githubusercontent.com/u/711564?v=4&s=48" width="48" height="48" alt="Tobias Bischoff" title="Tobias Bischoff"/></a> <a href="https://github.com/davidrudduck"><img src="https://avatars.githubusercontent.com/u/47308254?v=4&s=48" width="48" height="48" alt="davidrudduck" title="davidrudduck"/></a> <a href="https://github.com/xinhuagu"><img src="https://avatars.githubusercontent.com/u/562450?v=4&s=48" width="48" height="48" alt="xinhuagu" title="xinhuagu"/></a> <a href="https://github.com/jaydenfyi"><img src="https://avatars.githubusercontent.com/u/213395523?v=4&s=48" width="48" height="48" alt="jaydenfyi" title="jaydenfyi"/></a>
  <a href="https://github.com/petter-b"><img src="https://avatars.githubusercontent.com/u/62076402?v=4&s=48" width="48" height="48" alt="petter-b" title="petter-b"/></a> <a href="https://github.com/heyhudson"><img src="https://avatars.githubusercontent.com/u/258693705?v=4&s=48" width="48" height="48" alt="heyhudson" title="heyhudson"/></a> <a href="https://github.com/MatthieuBizien"><img src="https://avatars.githubusercontent.com/u/173090?v=4&s=48" width="48" height="48" alt="MatthieuBizien" title="MatthieuBizien"/></a> <a href="https://github.com/huntharo"><img src="https://avatars.githubusercontent.com/u/5617868?v=4&s=48" width="48" height="48" alt="huntharo" title="huntharo"/></a> <a href="https://github.com/omair445"><img src="https://avatars.githubusercontent.com/u/32237905?v=4&s=48" width="48" height="48" alt="omair445" title="omair445"/></a> <a href="https://github.com/adam91holt"><img src="https://avatars.githubusercontent.com/u/9592417?v=4&s=48" width="48" height="48" alt="adam91holt" title="adam91holt"/></a> <a href="https://github.com/adhitShet"><img src="https://avatars.githubusercontent.com/u/131381638?v=4&s=48" width="48" height="48" alt="adhitShet" title="adhitShet"/></a> <a href="https://github.com/smartprogrammer93"><img src="https://avatars.githubusercontent.com/u/33181301?v=4&s=48" width="48" height="48" alt="smartprogrammer93" title="smartprogrammer93"/></a> <a href="https://github.com/radek-paclt"><img src="https://avatars.githubusercontent.com/u/50451445?v=4&s=48" width="48" height="48" alt="radek-paclt" title="radek-paclt"/></a> <a href="https://github.com/frankekn"><img src="https://avatars.githubusercontent.com/u/4488090?v=4&s=48" width="48" height="48" alt="frankekn" title="frankekn"/></a>
  <a href="https://github.com/bradleypriest"><img src="https://avatars.githubusercontent.com/u/167215?v=4&s=48" width="48" height="48" alt="bradleypriest" title="bradleypriest"/></a> <a href="https://github.com/rahthakor"><img src="https://avatars.githubusercontent.com/u/8470553?v=4&s=48" width="48" height="48" alt="rahthakor" title="rahthakor"/></a> <a href="https://github.com/shadril238"><img src="https://avatars.githubusercontent.com/u/63901551?v=4&s=48" width="48" height="48" alt="shadril238" title="shadril238"/></a> <a href="https://github.com/VACInc"><img src="https://avatars.githubusercontent.com/u/3279061?v=4&s=48" width="48" height="48" alt="VACInc" title="VACInc"/></a> <a href="https://github.com/juanpablodlc"><img src="https://avatars.githubusercontent.com/u/92012363?v=4&s=48" width="48" height="48" alt="juanpablodlc" title="juanpablodlc"/></a> <a href="https://github.com/jonisjongithub"><img src="https://avatars.githubusercontent.com/u/86072337?v=4&s=48" width="48" height="48" alt="jonisjongithub" title="jonisjongithub"/></a> <a href="https://github.com/magimetal"><img src="https://avatars.githubusercontent.com/u/36491250?v=4&s=48" width="48" height="48" alt="magimetal" title="magimetal"/></a> <a href="https://github.com/stakeswky"><img src="https://avatars.githubusercontent.com/u/64798754?v=4&s=48" width="48" height="48" alt="stakeswky" title="stakeswky"/></a> <a href="https://github.com/AbhisekBasu1"><img src="https://avatars.githubusercontent.com/u/40645221?v=4&s=48" width="48" height="48" alt="abhisekbasu1" title="abhisekbasu1"/></a> <a href="https://github.com/MisterGuy420"><img src="https://avatars.githubusercontent.com/u/255743668?v=4&s=48" width="48" height="48" alt="MisterGuy420" title="MisterGuy420"/></a>
  <a href="https://github.com/hsrvc"><img src="https://avatars.githubusercontent.com/u/129702169?v=4&s=48" width="48" height="48" alt="hsrvc" title="hsrvc"/></a> <a href="https://github.com/nabbilkhan"><img src="https://avatars.githubusercontent.com/u/203121263?v=4&s=48" width="48" height="48" alt="nabbilkhan" title="nabbilkhan"/></a> <a href="https://github.com/aldoeliacim"><img src="https://avatars.githubusercontent.com/u/17973757?v=4&s=48" width="48" height="48" alt="aldoeliacim" title="aldoeliacim"/></a> <a href="https://github.com/jamesgroat"><img src="https://avatars.githubusercontent.com/u/2634024?v=4&s=48" width="48" height="48" alt="jamesgroat" title="jamesgroat"/></a> <a href="https://github.com/orlyjamie"><img src="https://avatars.githubusercontent.com/u/6668807?v=4&s=48" width="48" height="48" alt="orlyjamie" title="orlyjamie"/></a> <a href="https://github.com/Elarwei001"><img src="https://avatars.githubusercontent.com/u/168552401?v=4&s=48" width="48" height="48" alt="Elarwei001" title="Elarwei001"/></a> <a href="https://github.com/rubyrunsstuff"><img src="https://avatars.githubusercontent.com/u/246602379?v=4&s=48" width="48" height="48" alt="rubyrunsstuff" title="rubyrunsstuff"/></a> <a href="https://github.com/Phineas1500"><img src="https://avatars.githubusercontent.com/u/41450967?v=4&s=48" width="48" height="48" alt="Phineas1500" title="Phineas1500"/></a> <a href="https://github.com/meaningfool"><img src="https://avatars.githubusercontent.com/u/2862331?v=4&s=48" width="48" height="48" alt="meaningfool" title="meaningfool"/></a> <a href="https://github.com/sfo2001"><img src="https://avatars.githubusercontent.com/u/103369858?v=4&s=48" width="48" height="48" alt="sfo2001" title="sfo2001"/></a>
  <a href="https://github.com/Marvae"><img src="https://avatars.githubusercontent.com/u/11957602?v=4&s=48" width="48" height="48" alt="Marvae" title="Marvae"/></a> <a href="https://github.com/liuy"><img src="https://avatars.githubusercontent.com/u/1192888?v=4&s=48" width="48" height="48" alt="liuy" title="liuy"/></a> <a href="https://github.com/shtse8"><img src="https://avatars.githubusercontent.com/u/8020099?v=4&s=48" width="48" height="48" alt="shtse8" title="shtse8"/></a> <a href="https://github.com/thebenignhacker"><img src="https://avatars.githubusercontent.com/u/32418586?v=4&s=48" width="48" height="48" alt="thebenignhacker" title="thebenignhacker"/></a> <a href="https://github.com/carrotRakko"><img src="https://avatars.githubusercontent.com/u/24588751?v=4&s=48" width="48" height="48" alt="carrotRakko" title="carrotRakko"/></a> <a href="https://github.com/ranausmanai"><img src="https://avatars.githubusercontent.com/u/257128159?v=4&s=48" width="48" height="48" alt="ranausmanai" title="ranausmanai"/></a> <a href="https://github.com/kevinWangSheng"><img src="https://avatars.githubusercontent.com/u/118158941?v=4&s=48" width="48" height="48" alt="kevinWangSheng" title="kevinWangSheng"/></a> <a href="https://github.com/gregmousseau"><img src="https://avatars.githubusercontent.com/u/5036458?v=4&s=48" width="48" height="48" alt="gregmousseau" title="gregmousseau"/></a> <a href="https://github.com/rrenamed"><img src="https://avatars.githubusercontent.com/u/87486610?v=4&s=48" width="48" height="48" alt="rrenamed" title="rrenamed"/></a> <a href="https://github.com/akoscz"><img src="https://avatars.githubusercontent.com/u/1360047?v=4&s=48" width="48" height="48" alt="akoscz" title="akoscz"/></a>
  <a href="https://github.com/jarvis-medmatic"><img src="https://avatars.githubusercontent.com/u/252428873?v=4&s=48" width="48" height="48" alt="jarvis-medmatic" title="jarvis-medmatic"/></a> <a href="https://github.com/danielz1z"><img src="https://avatars.githubusercontent.com/u/235270390?v=4&s=48" width="48" height="48" alt="danielz1z" title="danielz1z"/></a> <a href="https://github.com/pandego"><img src="https://avatars.githubusercontent.com/u/7780875?v=4&s=48" width="48" height="48" alt="pandego" title="pandego"/></a> <a href="https://github.com/xadenryan"><img src="https://avatars.githubusercontent.com/u/165437834?v=4&s=48" width="48" height="48" alt="xadenryan" title="xadenryan"/></a> <a href="https://github.com/NicholasSpisak"><img src="https://avatars.githubusercontent.com/u/129075147?v=4&s=48" width="48" height="48" alt="NicholasSpisak" title="NicholasSpisak"/></a> <a href="https://github.com/graysurf"><img src="https://avatars.githubusercontent.com/u/10785178?v=4&s=48" width="48" height="48" alt="graysurf" title="graysurf"/></a> <a href="https://github.com/gupsammy"><img src="https://avatars.githubusercontent.com/u/20296019?v=4&s=48" width="48" height="48" alt="gupsammy" title="gupsammy"/></a> <a href="https://github.com/nyanjou"><img src="https://avatars.githubusercontent.com/u/258645604?v=4&s=48" width="48" height="48" alt="nyanjou" title="nyanjou"/></a> <a href="https://github.com/sibbl"><img src="https://avatars.githubusercontent.com/u/866535?v=4&s=48" width="48" height="48" alt="sibbl" title="sibbl"/></a> <a href="https://github.com/gejifeng"><img src="https://avatars.githubusercontent.com/u/17561857?v=4&s=48" width="48" height="48" alt="gejifeng" title="gejifeng"/></a>
  <a href="https://github.com/ide-rea"><img src="https://avatars.githubusercontent.com/u/30512600?v=4&s=48" width="48" height="48" alt="ide-rea" title="ide-rea"/></a> <a href="https://github.com/leszekszpunar"><img src="https://avatars.githubusercontent.com/u/13106764?v=4&s=48" width="48" height="48" alt="leszekszpunar" title="leszekszpunar"/></a> <a href="https://github.com/Yida-Dev"><img src="https://avatars.githubusercontent.com/u/92713555?v=4&s=48" width="48" height="48" alt="Yida-Dev" title="Yida-Dev"/></a> <a href="https://github.com/AI-Reviewer-QS"><img src="https://avatars.githubusercontent.com/u/255312808?v=4&s=48" width="48" height="48" alt="AI-Reviewer-QS" title="AI-Reviewer-QS"/></a> <a href="https://github.com/SocialNerd42069"><img src="https://avatars.githubusercontent.com/u/118244303?v=4&s=48" width="48" height="48" alt="SocialNerd42069" title="SocialNerd42069"/></a> <a href="https://github.com/maxsumrall"><img src="https://avatars.githubusercontent.com/u/628843?v=4&s=48" width="48" height="48" alt="maxsumrall" title="maxsumrall"/></a> <a href="https://github.com/hougangdev"><img src="https://avatars.githubusercontent.com/u/105773686?v=4&s=48" width="48" height="48" alt="hougangdev" title="hougangdev"/></a> <a href="https://github.com/Minidoracat"><img src="https://avatars.githubusercontent.com/u/11269639?v=4&s=48" width="48" height="48" alt="Minidoracat" title="Minidoracat"/></a> <a href="https://github.com/AnonO6"><img src="https://avatars.githubusercontent.com/u/124311066?v=4&s=48" width="48" height="48" alt="AnonO6" title="AnonO6"/></a> <a href="https://github.com/sreekaransrinath"><img src="https://avatars.githubusercontent.com/u/50989977?v=4&s=48" width="48" height="48" alt="sreekaransrinath" title="sreekaransrinath"/></a>
  <a href="https://github.com/YuzuruS"><img src="https://avatars.githubusercontent.com/u/1485195?v=4&s=48" width="48" height="48" alt="YuzuruS" title="YuzuruS"/></a> <a href="https://github.com/riccardogiorato"><img src="https://avatars.githubusercontent.com/u/4527364?v=4&s=48" width="48" height="48" alt="riccardogiorato" title="riccardogiorato"/></a> <a href="https://github.com/Bridgerz"><img src="https://avatars.githubusercontent.com/u/24499532?v=4&s=48" width="48" height="48" alt="Bridgerz" title="Bridgerz"/></a> <a href="https://github.com/Mrseenz"><img src="https://avatars.githubusercontent.com/u/101962919?v=4&s=48" width="48" height="48" alt="Mrseenz" title="Mrseenz"/></a> <a href="https://github.com/buddyh"><img src="https://avatars.githubusercontent.com/u/31752869?v=4&s=48" width="48" height="48" alt="buddyh" title="buddyh"/></a> <a href="https://github.com/omniwired"><img src="https://avatars.githubusercontent.com/u/322761?v=4&s=48" width="48" height="48" alt="Eng. Juan Combetto" title="Eng. Juan Combetto"/></a> <a href="https://github.com/peschee"><img src="https://avatars.githubusercontent.com/u/63866?v=4&s=48" width="48" height="48" alt="peschee" title="peschee"/></a> <a href="https://github.com/cash-echo-bot"><img src="https://avatars.githubusercontent.com/u/252747386?v=4&s=48" width="48" height="48" alt="cash-echo-bot" title="cash-echo-bot"/></a> <a href="https://github.com/jalehman"><img src="https://avatars.githubusercontent.com/u/550978?v=4&s=48" width="48" height="48" alt="jalehman" title="jalehman"/></a> <a href="https://github.com/zknicker"><img src="https://avatars.githubusercontent.com/u/1164085?v=4&s=48" width="48" height="48" alt="zknicker" title="zknicker"/></a>
  <a href="https://github.com/buerbaumer"><img src="https://avatars.githubusercontent.com/u/44548809?v=4&s=48" width="48" height="48" alt="Harald Buerbaumer" title="Harald Buerbaumer"/></a> <a href="https://github.com/taw0002"><img src="https://avatars.githubusercontent.com/u/42811278?v=4&s=48" width="48" height="48" alt="taw0002" title="taw0002"/></a> <a href="https://github.com/scald"><img src="https://avatars.githubusercontent.com/u/1215913?v=4&s=48" width="48" height="48" alt="scald" title="scald"/></a> <a href="https://github.com/openperf"><img src="https://avatars.githubusercontent.com/u/80630709?v=4&s=48" width="48" height="48" alt="openperf" title="openperf"/></a> <a href="https://github.com/BUGKillerKing"><img src="https://avatars.githubusercontent.com/u/117326392?v=4&s=48" width="48" height="48" alt="BUGKillerKing" title="BUGKillerKing"/></a> <a href="https://github.com/Oceanswave"><img src="https://avatars.githubusercontent.com/u/760674?v=4&s=48" width="48" height="48" alt="Oceanswave" title="Oceanswave"/></a> <a href="https://github.com/patelhiren"><img src="https://avatars.githubusercontent.com/u/172098?v=4&s=48" width="48" height="48" alt="Hiren Patel" title="Hiren Patel"/></a> <a href="https://github.com/kiranjd"><img src="https://avatars.githubusercontent.com/u/25822851?v=4&s=48" width="48" height="48" alt="kiranjd" title="kiranjd"/></a> <a href="https://github.com/antons"><img src="https://avatars.githubusercontent.com/u/129705?v=4&s=48" width="48" height="48" alt="antons" title="antons"/></a> <a href="https://github.com/dan-dr"><img src="https://avatars.githubusercontent.com/u/6669808?v=4&s=48" width="48" height="48" alt="dan-dr" title="dan-dr"/></a>
  <a href="https://github.com/jadilson12"><img src="https://avatars.githubusercontent.com/u/36805474?v=4&s=48" width="48" height="48" alt="jadilson12" title="jadilson12"/></a> <a href="https://github.com/sumleo"><img src="https://avatars.githubusercontent.com/u/29517764?v=4&s=48" width="48" height="48" alt="sumleo" title="sumleo"/></a> <a href="https://github.com/Whoaa512"><img src="https://avatars.githubusercontent.com/u/1581943?v=4&s=48" width="48" height="48" alt="Whoaa512" title="Whoaa512"/></a> <a href="https://github.com/luijoc"><img src="https://avatars.githubusercontent.com/u/96428056?v=4&s=48" width="48" height="48" alt="luijoc" title="luijoc"/></a> <a href="https://github.com/niceysam"><img src="https://avatars.githubusercontent.com/u/256747835?v=4&s=48" width="48" height="48" alt="niceysam" title="niceysam"/></a> <a href="https://github.com/JustYannicc"><img src="https://avatars.githubusercontent.com/u/52761674?v=4&s=48" width="48" height="48" alt="JustYannicc" title="JustYannicc"/></a> <a href="https://github.com/emanuelst"><img src="https://avatars.githubusercontent.com/u/9994339?v=4&s=48" width="48" height="48" alt="emanuelst" title="emanuelst"/></a> <a href="https://github.com/TsekaLuk"><img src="https://avatars.githubusercontent.com/u/79151285?v=4&s=48" width="48" height="48" alt="TsekaLuk" title="TsekaLuk"/></a> <a href="https://github.com/JustasMonkev"><img src="https://avatars.githubusercontent.com/u/59362982?v=4&s=48" width="48" height="48" alt="JustasM" title="JustasM"/></a> <a href="https://github.com/loiie45e"><img src="https://avatars.githubusercontent.com/u/15420100?v=4&s=48" width="48" height="48" alt="loiie45e" title="loiie45e"/></a>
</p>

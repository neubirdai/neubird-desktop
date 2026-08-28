<div align="center">
  <h1>Neubird Desktop</h1>
  <p><strong>The AI-native workspace for SRE operations.</strong></p>
  <p>
    <a href="https://neubird.ai">neubird.ai</a> &nbsp;·&nbsp;
    <a href="https://github.com/neubirdai/neubird-desktop/releases">Releases</a> &nbsp;·&nbsp;
    <a href="https://neubird.ai/docs">Documentation</a>
  </p>
</div>

---

## What is Neubird Desktop?

Neubird Desktop is the AI workspace built for modern SRE teams. It brings active investigation management, AI-assisted root-cause analysis, and team coordination into a single desktop environment — so your engineers spend less time context-switching and more time resolving incidents.

Connect Neubird Desktop to your Neubird environment and it starts working immediately: surfacing active incidents, analyzing signals across your stack, and recommending next steps.

---

## Capabilities

**Active investigation tracking**
See all open investigations in one place, with live status and AI-generated summaries. Your team always knows what needs attention right now and what's already being worked.

**AI-assisted root-cause analysis**
Neubird Desktop correlates signals across logs, metrics, and traces and presents a plain-language explanation of what's happening and why. Ask follow-up questions in natural language and get answers grounded in your actual infrastructure data.

**Smart team routing**
When an incident needs escalation, Neubird Desktop identifies the right owners and surfaces the fastest path to reach them — including direct links into your team's communication channels. No more guessing who's on call.

**Institutional memory**
Capture what your team learns from each incident and apply it automatically to future investigations. Neubird Desktop gets smarter the more your team uses it, reducing time-to-resolution on recurring issues.

**Environment health at a glance**
A unified view of service health, recent deployments, and active incidents — giving you the situational awareness to make fast, confident decisions under pressure.

**Proactive risk detection**
Neubird Desktop continuously monitors your environment and surfaces anomalies before they escalate into incidents, giving your team a head start on prevention rather than just reaction.

**Deployment correlation**
Automatically links releases with system behavior changes so you can quickly confirm or rule out whether a recent deploy is causing a degradation.

**Extensible by design**
Connect Neubird Desktop to additional data sources, internal tools, and runbooks using the Model Context Protocol (MCP). Bring your own context without custom integrations.

**Always human-in-the-loop**
Neubird Desktop assists and recommends — it never acts autonomously in your production environment. Every action requires explicit approval.

---

## Download

One app, two modes — pick the workspace that fits you on first launch, and switch any time from the account menu:

- **Co-Worker** — the standard workspace for SRE operations.
- **Aerie** — the manager workspace: Activity, Analyst and Insights.

Direct downloads (always the latest release):

| macOS (universal) | Windows x64 | Windows arm64 |
| --- | --- | --- |
| [Download .dmg](https://github.com/neubirdai/neubird-desktop/releases/latest/download/NeubirdDesktopShell-darwin-universal.dmg) | [Download installer](https://github.com/neubirdai/neubird-desktop/releases/latest/download/NeubirdDesktopShellSetup-x64.exe) | [Download installer](https://github.com/neubirdai/neubird-desktop/releases/latest/download/NeubirdDesktopShellSetup-arm64.exe) |

All versions, with release notes, are on the [Releases](https://github.com/neubirdai/neubird-desktop/releases) page.

### macOS

**Homebrew (recommended — it is also the auto-update path):**

```bash
brew install --cask neubirdai/tap/neubird-desktop   # first install
brew upgrade --cask neubird-desktop                 # updates
```

**Direct download:** open the `.dmg` and drag the app to **Applications**. macOS builds are codesigned and notarized, so no quarantine workarounds are needed.

### Windows

Download the installer matching your architecture (`x64` for standard machines, `arm64` for Snapdragon/Copilot+ devices) and run it. If SmartScreen shows "Windows protected your PC", click **More info → Run anyway**.

---

## Getting started

1. Install Neubird Desktop using one of the methods above.
2. Launch the app and choose your workspace — **Co-Worker** or **Aerie**. You can switch later from the account menu.
3. Enter your Neubird environment URL.
4. Sign in with your organization credentials.
5. Neubird Desktop connects to your environment and begins surfacing active investigations immediately.

For full documentation, visit [neubird.ai/docs](https://neubird.ai/docs).

---

## Support

For help and feedback, visit [neubird.ai/docs](https://neubird.ai/docs) or reach out via [neubird.ai](https://neubird.ai).

<div align="center">
  <h1>Neubird Falcon</h1>
  <p><strong>The AI-native workspace for SRE operations.</strong></p>
  <p>
    <a href="https://neubird.ai">neubird.ai</a> &nbsp;·&nbsp;
    <a href="https://github.com/neubirdai/neubird-falcon-app/releases">Releases</a> &nbsp;·&nbsp;
    <a href="https://neubird.ai/docs">Documentation</a>
  </p>
</div>

---

## What is Falcon?

Falcon is the AI workspace built for modern SRE teams. It brings active investigation management, AI-assisted root-cause analysis, and team coordination into a single desktop environment — so your engineers spend less time context-switching and more time resolving incidents.

Connect Falcon to your Neubird environment and it starts working immediately: surfacing active incidents, analyzing signals across your stack, and recommending next steps.

---

## Capabilities

**Active investigation tracking**
See all open investigations in one place, with live status and AI-generated summaries. Your team always knows what needs attention right now and what's already being worked.

**AI-assisted root-cause analysis**
Falcon correlates signals across logs, metrics, and traces and presents a plain-language explanation of what's happening and why. Ask follow-up questions in natural language and get answers grounded in your actual infrastructure data.

**Smart team routing**
When an incident needs escalation, Falcon identifies the right owners and surfaces the fastest path to reach them — including direct links into your team's communication channels. No more guessing who's on call.

**Institutional memory**
Capture what your team learns from each incident and apply it automatically to future investigations. Falcon gets smarter the more your team uses it, reducing time-to-resolution on recurring issues.

**Environment health at a glance**
A unified view of service health, recent deployments, and active incidents — giving you the situational awareness to make fast, confident decisions under pressure.

**Proactive risk detection**
Falcon continuously monitors your environment and surfaces anomalies before they escalate into incidents, giving your team a head start on prevention rather than just reaction.

**Deployment correlation**
Automatically links releases with system behavior changes so you can quickly confirm or rule out whether a recent deploy is causing a degradation.

**Extensible by design**
Connect Falcon to additional data sources, internal tools, and runbooks using the Model Context Protocol (MCP). Bring your own context without custom integrations.

**Always human-in-the-loop**
Falcon assists and recommends — it never acts autonomously in your production environment. Every action requires explicit approval.

---

## Install (macOS)

### Homebrew (recommended)

```bash
brew install --cask neubirdai/tap/falcon
```

For upgrades:

```bash
brew upgrade --cask neubirdai/tap/falcon
```

### Direct download

1. Download the latest `NeubirdFalcon-darwin-arm64.dmg` from [Releases](https://github.com/neubirdai/neubird-falcon-app/releases).
2. Remove quarantine (required until notarization is enabled):

```bash
xattr -d com.apple.quarantine ~/Downloads/NeubirdFalcon-darwin-arm64.dmg
```

3. Open the DMG and drag **Neubird Falcon** to **Applications**.
4. Launch and sign in with your Neubird environment URL.

---

## Getting started

1. Install Falcon using one of the methods above.
2. Launch the app and enter your Neubird environment URL.
3. Sign in with your organization credentials.
4. Falcon connects to your environment and begins surfacing active investigations immediately.

For full documentation, visit [neubird.ai/docs](https://neubird.ai/docs).

---

## Reporting issues

Please open an issue at: https://github.com/neubirdai/falcon-app/issues

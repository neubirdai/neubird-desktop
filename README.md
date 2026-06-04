<div align="center">
  <h1>Neubird Falcon</h1>
  <p><strong>The AI-native workspace for SRE operations.</strong></p>
  <p>
    <a href="https://neubird.ai">neubird.ai</a> ·
    <a href="https://github.com/neubirdai/neubird-falcon-app/releases">Releases</a> ·
    <a href="https://github.com/neubirdai/falcon-app/issues">Report an issue</a>
  </p>
</div>

---

## What is Falcon?

Falcon is Neubird's AI-native SRE workspace — a desktop application built on Code OSS that replaces the fragmented tab-switching of traditional SRE workflows with a single, always-on environment that understands your infrastructure.

Falcon connects to your Neubird environment and surfaces the right context, investigations, and recommended actions exactly when you need them. Instead of correlating logs, traces, alerts, and runbooks across five separate tools, you work inside one workspace where the AI has already done that correlation for you.

---

## Features

### Falcon Flow — Investigation management
Track and navigate active investigations from a dedicated panel. Falcon Flow shows open incidents with real-time status, lets you drill into the AI's root-cause analysis, and surfaces follow-up actions as the situation evolves.

### Falcon Agent — AI-powered SRE assistant
An AI agent embedded in your workspace that answers questions about your infrastructure, runs diagnostic commands (with your approval), and synthesizes findings across logs, metrics, and traces into plain-language explanations your whole team can act on.

### Falcon Huddle — Smart incident routing
When an incident needs human escalation, Falcon Huddle identifies the right team and surfaces the relevant Slack channels and on-call handles — with the reasoning behind the recommendation. One click opens the Slack conversation with context pre-filled.

### Falcon Learnings — Institutional memory
Teach Falcon what your organization has already learned from past incidents. Learnings are automatically applied during future investigations so the AI doesn't re-discover the same root causes or recommend already-ruled-out fixes.

### Mission Control — Unified status view
A birds-eye view of your environment's health. Mission Control aggregates service status, active incidents, and recent deployments so you always know the current state of your system at a glance — without opening a browser.

### Risk Sentinel — Proactive risk monitoring
Falcon watches your environment continuously and surfaces anomalies before they become incidents. Risk Sentinel highlights signals that warrant attention, with confidence scores and direct links to the underlying data.

### Falcon Build — CI/deployment awareness
Correlates deployment events with incident timelines so you can quickly determine whether a recent release is related to an ongoing degradation — cutting the most common "is this a deploy?" back-and-forth from your war room.

### Service Map integration
Falcon understands your service dependency graph and uses it to scope investigations. When `auth-service` is slow, Falcon knows which upstream and downstream services to check next, and prioritizes them automatically.

### MCP (Model Context Protocol) support
Extend Falcon with additional data sources and tools via MCP servers. Connect internal dashboards, runbooks, or proprietary observability data to give the AI richer context for investigations — no code changes required.

### Human-in-the-loop safety
Falcon never takes autonomous action in production. Every proposed command or remediation step goes through an approval gate, keeping your team in control of what actually runs.

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
2. Launch the app and enter your Neubird environment URL (e.g. `https://app.neubird.ai`).
3. Sign in with your organization credentials.
4. Falcon will connect to your environment and begin populating Falcon Flow with active investigations.

---

## About "Source code" assets on Releases

GitHub automatically adds **Source code (zip/tar.gz)** links to every tag.
In this repo, those archives contain only this public release metadata
(for example this README) and **not** the private Falcon application source.

- **App source code is not in this repository.**
- Falcon source lives in the private engineering repo: `neubirdai/falcon-app`.

## Reporting issues

Please open issues at: https://github.com/neubirdai/falcon-app/issues

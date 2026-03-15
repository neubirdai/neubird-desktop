<p align="center">
  <a href="https://asciinema.org/a/eNVVnr9DfzfTHW4r">
    <img src="https://asciinema.org/a/eNVVnr9DfzfTHW4r.svg" alt="NeuBird.ai terminal demo" />
  </a>
</p>

<h1 align="center">Neubird Desktop</h1>

<p align="center">
  <strong>The AI SRE that lives in your terminal.</strong><br/>
  Predict outages. Prevent incidents. Remediate in real time. Cut cloud waste.<br/>
  One command. Zero context-switching.
</p>

<p align="center">
  <a href="https://neubird.ai">Website</a> ·
  <a href="https://help.neubird.ai">Docs</a> ·
  <a href="https://github.com/neubirdai/falcon-desktop/releases">Releases</a> ·
  <a href="https://neubird.ai/signup">Get a Free Account</a>
</p>

---

## What is Neubird?

Neubird is an **Agentic AI SRE platform** that connects to the tools already in your observability and operations stack — Datadog, Splunk, Grafana, PagerDuty, AWS, Azure, GCP, ServiceNow, GitHub, and more — and reasons across all of them together.

**Neubird Desktop** brings that power to your terminal. Ask questions in plain English and get back root cause analysis, cost projections, risk forecasts, and remediation plans backed by real evidence from your live telemetry.

No dashboards. No tab switching. No runbooks.

At the core is the **Falcon engine** — Neubird’s lightweight, fast investigation engine for desktop workflows. Falcon is designed to move quickly, synthesize evidence across systems, and continuously improve as Neubird upgrades the engine over time.

```text
┌──────────────────────────────────────────────────────────────────────┐
│                                                                      │
│   You:  "What's quietly degrading that could page me tonight?"       │
│                                                                      │
│   Falcon:                                                            │
│   ⚡ querying trace_grafana_tempo.spans — p99 latency by service     │
│   ⚡ querying metric_datadog.cpu_utilization — saturation check      │
│   ⚡ querying firehydrant.incidents — open incidents last 72h        │
│                                                                      │
│   Three services are trending toward degradation:                    │
│   1. payment-gateway — p99 latency up 340% in the last 2h            │
│   2. auth-service — connection pool at 87% saturation                │
│   3. order-processor — error rate doubled since last deploy          │
│                                                                      │
│   Recommended actions: ...                                           │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

---

## Quick Start

### 1. Install

**macOS** (Homebrew)

```sh
brew tap neubirdai/tap
brew install neubird
```

**Ubuntu / Debian**

```sh
snap install neubird-desktop
```

**Other platforms** — grab the binary from [Releases](https://github.com/neubirdai/falcon-desktop/releases).

### 2. Connect your account

Sign up at **[neubird.ai/signup](https://neubird.ai/signup)** if you do not have an account yet.

Neubird connects to your existing telemetry tools — Datadog, Splunk, Grafana, AWS, and more — via read-only API keys. No agents to install. No infrastructure changes.

### 3. Launch

```sh
neubird
```

That is it. Neubird discovers your telemetry inventory, maps your schemas, and drops you into an interactive terminal session. Ask anything.

---

## What Can It Do?

### 🔮 Predict — Know what breaks before it breaks

Neubird detects degradation signatures before they become incidents. It reads trends across metrics, traces, logs, incidents, and topology to forecast what is most likely to page you next.

```text
› Based on current trends, what services are at risk of degrading in the next 24 hours?
```

Neubird queries latency percentiles, error rates, resource saturation, traffic growth, and dependency health to tell you where capacity runs out and which services are on a collision course.

### 🛡️ Prevent — Stop incidents before they start

Do not wait for alerts. Run a proactive health sweep and catch issues while they are still cheap to fix.

```text
› /health
```

Neubird runs a systematic sweep across your infrastructure — metrics, logs, traces, incidents, topology, and cost signals — and produces a structured report:

| Section | What it covers |
|---|---|
| 🟢 **Good** | Services operating normally, with evidence to prove it |
| 🔴 **Bad** | Active problems with evidence, blast radius, and timeline |
| 🟡 **Ugly** | Not broken yet, but trending the wrong way |
| ⚠️ **Watch** | Monitoring gaps, single points of failure, upcoming capacity cliffs |
| 💰 **Cost** | Cardinality hotspots, log noise, idle compute, waste |

### 🔧 Remediate — Fix what is broken right now

When something is on fire, Neubird investigates autonomously. Falcon queries telemetry, correlates across tools, and delivers a root cause analysis with supporting evidence and a remediation plan — in minutes, not hours.

```text
› The checkout service is returning 503s — what's causing it and what should I do?
```

Neubird traces the failure across service maps, correlates with recent deploys and config changes, checks upstream and downstream dependencies, and returns a step-by-step fix ranked by likelihood and blast radius.

### 💰 Optimize — Find the cloud spend you are wasting

Run a cost analysis to identify metric cardinality bloat, log volume waste, over-provisioned compute, and idle resources — then project what spend looks like in 7 and 30 days if nothing changes.

```text
› /cost
```

You get a ranked list of waste drivers separated into **quick wins** and **engineering projects**, with ROI estimates for each.

### 🔍 Discover — Catch risks before they ship

Ask Neubird to cross-reference code changes with production telemetry so you can identify what could go wrong before a change is merged or deployed.

```text
› What pending PRs or recent merges are most likely to cause problems?
```

Neubird checks current production load, historical incidents, related services, recent changes, and dependency health — and tells you which changes look risky and why.

---

## Built-In Commands

| Command | What it does |
|---|---|
| `/health` | Full infrastructure health sweep (default: 1 hour lookback) |
| `/health 24h` | Deep dive with 24-hour context |
| `/cost` | Cloud cost baseline + 24-hour spend projection |
| `/reset` | Clear conversation history and start fresh |
| `/help` | Show available commands |

Or just type a question in plain English. Neubird figures out what to query.

---

## How It Works

```text
┌─────────────────────────────────────────────────────────────────┐
│                         YOUR TERMINAL                           │
│                       neubird desktop                           │
└──────────────────────┬──────────────────────────────────────────┘
                       │  natural language question
                       ▼
┌─────────────────────────────────────────────────────────────────┐
│                      FALCON ENGINE                              │
│                                                                 │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌────────────┐    │
│  │ Discover  │→ │Understand │→ │Investigate│→ │ Synthesize │    │
│  │ schemas   │  │ tables    │  │ execute   │  │ findings   │    │
│  │ & tools   │  │ & signals │  │ queries   │  │ & actions  │    │
│  └───────────┘  └───────────┘  └───────────┘  └────────────┘    │
│                                                                 │
│            reads from your telemetry (read-only)                │
└──────────────────────┬──────────────────────────────────────────┘
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
  ┌──────────┐  ┌──────────┐  ┌──────────┐
  │ Datadog  │  │  Splunk  │  │   AWS    │   ... and 30+ more
  │ metrics  │  │   logs   │  │CloudWatch│
  └──────────┘  └──────────┘  └──────────┘
```

Falcon operates in an **agentic loop**: it forms a hypothesis, queries your telemetry to test it, refines based on what it finds, and repeats until it has a confident answer — like a strong SRE working through evidence, just much faster.

Because Falcon is the engine inside Neubird Desktop, the desktop experience can improve over time as Neubird upgrades the engine, expands connectors, and sharpens its reasoning.

Every important claim is grounded in evidence from the connected telemetry and systems it inspected.

---

## What It Connects To

Neubird integrates with your existing stack through read-only API connections. Nothing to install on your infrastructure.

| Category | Integrations |
|---|---|
| **Monitoring** | Datadog, Splunk, Dynatrace, Grafana, Prometheus, New Relic, CloudWatch |
| **Incident Management** | PagerDuty, OpsGenie, FireHydrant, ServiceNow |
| **Cloud** | AWS, Azure, GCP |
| **Traces** | Grafana Tempo, Jaeger, OpenTelemetry |
| **CI/CD & Code** | GitHub, GitLab, ArgoCD, Jenkins |
| **Communication** | Slack, Jira |
| **Coding Agents** | Cursor, Copilot, Windsurf, Cline, Claude Code |
| **IaC** | Terraform, Pulumi, Ansible, Helm, Crossplane |

---

## Security

Neubird is built for enterprises that take security seriously.

- **SOC 2 Type II certified**
- **Zero data persistence** — telemetry is processed in memory and purged after each session
- **Read-only access** — Neubird does not modify your infrastructure
- **Your data is never used to train models**
- **VPC deployment available** for regulated environments
- **SSO/SAML, RBAC, and full audit trails**

---

## Who It Is For

- **SRE / IT Ops** — Cut MTTR and get root cause in minutes, not hours
- **DevOps / Platform Engineering** — Proactive health checks, cost optimization, and deployment risk analysis from your terminal
- **Network Ops** — Cross-stack correlation that connects network metrics to application behavior
- **Engineering Leadership** — Evidence-backed health reports and cost projections on demand

---

## Real-World Results

| Metric | Result |
|---|---|
| **MTTR Reduction** | Up to 90% |
| **Alert Noise Reduction** | 78% |
| **Avg Investigation Time** | 18 minutes |
| **Cost Reduction** | 60%+ |

> *"Having an expert SRE working alongside our teams 24/7 has transformed how we operate. Critical issues that once took days to resolve are now handled in minutes."*

---

## Get Started

```sh
# Install
brew tap neubirdai/tap && brew install neubird

# Sign up for an account at neubird.ai/signup
# Connect your telemetry tools

# Launch
neubird
```

Questions? Reach us at [neubird.ai](https://neubird.ai) or open an issue in this repo.

---

<p align="center">
  <sub>Built by <a href="https://neubird.ai">NeuBird.ai</a> · Backed by Microsoft M12, Mayfield, and Prosperity7</sub>
</p>

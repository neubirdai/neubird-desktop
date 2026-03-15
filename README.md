<p align="center">
  <a href="https://youtu.be/mM4DyT2u8_s">
    <img src="https://img.youtube.com/vi/mM4DyT2u8_s/0.jpg" alt="NeuBird.ai desktop demo" />
  </a><br/>
  <strong>NeuBird.ai desktop demo</strong>:
  <a href="https://youtu.be/mM4DyT2u8_s">Watch on YouTube</a>
</p>

<h1 align="center">Neubird Desktop</h1>

<p align="center">
  <strong>The AI SRE that lives in your terminal.</strong><br/>
  Predict outages. Prevent incidents. Remediate in real time. Cut cloud waste.<br/>
  One command. Zero context-switching.
</p>

<p align="center">
  <a href="https://neubird.ai">Website</a> · <a href="https://help.neubird.ai">Docs</a> · <a href="https://github.com/neubirdai/falcon-desktop/releases">Releases</a> · <a href="https://neubird.ai/signup">Get a Free Account</a>
</p>

---

## What is Neubird?

Neubird's **Hawkeye** is an Agentic AI SRE platform that connects to every tool in your observability stack — Datadog, Splunk, Grafana, PagerDuty, AWS, Azure, GCP, ServiceNow, and more — and reasons across all of them simultaneously.

**Neubird Desktop** brings that power to your terminal. Ask questions in plain English, get back root cause analysis, cost projections, risk forecasts, and remediation plans — backed by real evidence from your live telemetry. No dashboards. No tab-switching. No runbooks.

```
┌──────────────────────────────────────────────────────────────────────┐
│                                                                      │
│   You:  "What's quietly degrading that could page me tonight?"       │
│                                                                      │
│   Hawkeye:                                                           │
│   ⚡ querying trace_grafana_tempo.spans — p99 latency by service     │
│   ⚡ querying metric_datadog.cpu_utilization — saturation check      │
│   ⚡ querying firehydrant.incidents — open incidents last 72h        │
│                                                                      │
│   Three services are trending toward degradation:                    │
│   1. payment-gateway — p99 latency up 340% in the last 2h           │
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

Sign up at **[neubird.ai/signup](https://neubird.ai/signup)** if you don't have an account yet. Neubird connects to your existing telemetry tools (Datadog, Splunk, Grafana, AWS, etc.) via read-only API keys — no agents to install, no infrastructure changes.

### 3. Launch

```sh
neubird
```

That's it. Hawkeye discovers your telemetry inventory, builds a map of your schemas, and drops you into an interactive session. Ask anything.

---

## What Can It Do?

### 🔮 Predict — Know what breaks before it breaks

Hawkeye detects degradation signatures **30–60 minutes before they become incidents**. It reads trends across metrics, traces, and logs to forecast what's likely to page you next.

```
› Based on current trends, what services are at risk of degrading in the next 24 hours?
```

Hawkeye queries latency percentiles, error rates, resource saturation, and traffic growth, then extrapolates to tell you exactly where capacity runs out and which services are on a collision course.

### 🛡️ Prevent — Stop incidents before they start

Don't wait for alerts. Run a proactive health sweep and catch issues while they're still cheap to fix.

```
› /health
```

Hawkeye runs a systematic sweep across your infrastructure — metrics, logs, traces, incidents, topology, and cost signals — and produces a structured report:

| Section | What it covers |
|---|---|
| 🟢 **Good** | Services operating normally, with numbers to prove it |
| 🔴 **Bad** | Active problems with evidence, blast radius, and timeline |
| 🟡 **Ugly** | Not broken yet, but trending the wrong way |
| ⚠️ **Watch** | Monitoring gaps, single points of failure, upcoming capacity cliffs |
| 💰 **Cost** | Cardinality hotspots, log noise, idle compute |

### 🔧 Remediate — Fix what's broken right now

When something is on fire, Hawkeye investigates autonomously. It queries your telemetry, correlates across tools, and delivers a root cause analysis with supporting evidence and a remediation plan — in minutes, not hours.

```
› The checkout service is returning 503s — what's causing it and what do I do?
```

Hawkeye traces the failure across service maps, correlates with recent deploys and config changes, checks upstream dependencies, and returns a step-by-step fix ranked by likelihood and blast radius.

### 💰 Optimize — Find the cloud spend you're wasting

Run a cost analysis that identifies metric cardinality bloat, log volume waste, over-provisioned compute, and idle resources — then projects what your spend looks like in 7 and 30 days if nothing changes.

```
› /cost
```

You get a ranked list of the top waste drivers, separated into **quick wins** (under 1 hour) and **engineering projects**, with ROI estimates for each.

### 🔍 Discover — Catch risks in PRs before they ship

Ask Hawkeye to cross-reference code changes with production telemetry. Identify what could go wrong with a deployment *before* it merges.

```
› Daniel just opened a PR that changes the connection pool config for auth-service.
  Based on current production load, will that cause problems?
```

Hawkeye checks current connection utilization, peak traffic patterns, and historical incidents related to pool exhaustion — and tells you whether the PR's new values are safe at production scale.

---

## Built-In Commands

| Command | What it does |
|---|---|
| `/health` | Full infrastructure health sweep (default: 1 hour lookback) |
| `/health 24h` | Deep dive with 24-hour context |
| `/cost` | Cloud cost baseline + 24-hour spend projection |
| `/reset` | Clear conversation history and start fresh |
| `/help` | Show all available commands |

Or just type a question in plain English. Hawkeye figures out what to query.

---

## How It Works

```
┌─────────────────────────────────────────────────────────────────┐
│                      YOUR TERMINAL                              │
│                    neubird desktop                               │
└──────────────────────┬──────────────────────────────────────────┘
                       │  natural language question
                       ▼
┌─────────────────────────────────────────────────────────────────┐
│                   HAWKEYE AI ENGINE                              │
│                                                                 │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌────────────┐  │
│  │  Discover  │→ │Understand │→ │Investigate│→ │ Synthesize │  │
│  │  schemas   │  │  tables   │  │  exec SQL │  │  senior    │  │
│  │  & tables  │  │  & cols   │  │  & trace  │  │  review    │  │
│  └───────────┘  └───────────┘  └───────────┘  └────────────┘  │
│                                                                 │
│          reads from your telemetry (read-only)                  │
└──────────────────────┬──────────────────────────────────────────┘
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
  ┌──────────┐  ┌──────────┐  ┌──────────┐
  │ Datadog  │  │  Splunk  │  │   AWS    │   ... and 30+ more
  │ metrics  │  │   logs   │  │CloudWatch│
  └──────────┘  └──────────┘  └──────────┘
```

Hawkeye operates in an **agentic loop**: it forms a hypothesis, queries your telemetry to test it, refines based on what it finds, and repeats until it has a confident answer — the same way a senior SRE would investigate, just faster.

Every claim is backed by the specific table and query that produced it. No hallucinations. No made-up numbers.

---

## What It Connects To

Neubird integrates with your existing stack via read-only API connections. Nothing to install on your infrastructure.

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
- **Read-only access** — Hawkeye never modifies your infrastructure
- **Your data is never used to train models**
- **VPC deployment available** for regulated environments
- **SSO/SAML, RBAC, and full audit trails**

---

## Who It's For

- **SRE / IT Ops** — Cut MTTR by up to 90%. Get root cause in minutes, not hours.
- **DevOps / Platform Engineering** — Proactive health checks, cost optimization, and deployment risk analysis from your terminal.
- **Network Ops** — Cross-stack correlation that connects network metrics to application behavior.
- **Engineering Leadership** — Evidence-backed health reports and cost projections, generated on demand.

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
# Connect your telemetry tools (takes ~5 minutes)

# Launch
neubird
```

Questions? Reach us at [neubird.ai](https://neubird.ai) or open an issue in this repo.

---

<p align="center">
  <sub>Built by <a href="https://neubird.ai">NeuBird AI</a> · Backed by Microsoft M12, Mayfield, and Prosperity 7</sub>
</p>

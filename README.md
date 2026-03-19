<p align="center">
  <a href="https://asciinema.org/a/eNVVnr9DfzfTHW4r" target="_blank"><img src="https://asciinema.org/a/eNVVnr9DfzfTHW4r.svg" /></a>
</p>

<h1 align="center">NeuBird Desktop — Production Ops Agent in Your Terminal</h1>

<p align="center">
  <strong>The AI DevOps and SRE agent that lives in your terminal.</strong><br/>
  Prevent outages. Resolve incidents. Optimize cloud spend.<br/>
  One command. Zero context-switching.
</p>

<p align="center">
  <a href="https://neubird.ai">Website</a> ·
  <a href="https://help.neubird.ai">Docs</a> ·
  <a href="https://github.com/neubirdai/falcon/releases">Releases</a> ·
  <a href="https://signup.registration.neubird.ai/registrations">Get a Free Account</a>
</p>

---

## What is NeuBird?

NeuBird is an **agentic AI SRE platform** that connects to the tools already in your observability and operations stack — Datadog, Splunk, Grafana, PagerDuty, AWS, Azure, GCP, ServiceNow, GitHub, and more — and reasons across all of them together.

**NeuBird Desktop** brings that power to your terminal. Ask questions in plain English and get back root cause analysis, cost projections, risk forecasts, and remediation plans backed by real evidence from your live telemetry.

No dashboards. No tab switching. No runbooks.

At the core is the **Falcon engine** — NeuBird's investigation engine powered by Claude. Falcon explores your schema, writes and executes SQL, correlates evidence across data sources, and continuously improves as it learns your infrastructure.

```text
┌──────────────────────────────────────────────────────────────────────┐
│                                                                      │
│   You:  "What's quietly degrading that could page me tonight?"       │
│                                                                      │
│   Falcon:                                                            │
│   ⚡ querying trace_grafana_tempo.spans — p99 latency by service      │
│   ⚡ querying metric_datadog.cpu_utilization — saturation check       │
│   ⚡ querying firehydrant.incidents — open incidents last 72h         │
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
brew install neubirdai/tap/neubird
```

**Linux** (Snap)

```sh
sudo snap install neubird-desktop
```

**Linux** (Debian / Ubuntu)

```sh
curl -LO https://github.com/neubirdai/falcon/releases/latest/download/neubird_linux_amd64.deb
sudo dpkg -i neubird_linux_amd64.deb
```

**Linux** (Fedora / RHEL)

```sh
curl -LO https://github.com/neubirdai/falcon/releases/latest/download/neubird_linux_amd64.rpm
sudo rpm -i neubird_linux_amd64.rpm
```

**Windows**

```powershell
# Download and extract
Invoke-WebRequest -Uri "https://github.com/neubirdai/falcon/releases/latest/download/neubird_windows_amd64.zip" -OutFile neubird.zip
Expand-Archive neubird.zip -DestinationPath "$env:LOCALAPPDATA\neubird"

# Add to PATH (current session)
$env:PATH += ";$env:LOCALAPPDATA\neubird"

# Add to PATH permanently (requires terminal restart)
[Environment]::SetEnvironmentVariable("PATH", $env:PATH + ";$env:LOCALAPPDATA\neubird", "User")
```

**Docker**

```sh
docker run -it --rm \
  -e ANTHROPIC_API_KEY=sk-ant-... \
  neubirdai/neubird-desktop:latest
```

**Other platforms** — pre-built binaries for macOS (Apple Silicon + Intel), Linux (x86_64 + ARM64), and Windows (x86_64) are available on the [releases page](https://github.com/neubirdai/falcon/releases/latest).

### 2. Connect your account

Sign up at **[neubird.ai/signup](https://signup.registration.neubird.ai/registrations)** if you do not have an account yet.

NeuBird connects to your existing telemetry tools — Datadog, Splunk, Grafana, AWS, and more — via read-only API keys. No agents to install. No infrastructure changes.

### 3. Launch

```sh
neubird
```

NeuBird discovers your telemetry inventory, maps your schemas, and drops you into an interactive terminal session. Ask anything.

### 4. Updating

```sh
# macOS
brew upgrade neubird

# Snap
sudo snap refresh neubird-desktop

# Windows / other — download the latest release
```

---

## What Can It Do?

### Prevent — Stop incidents before they start

Run a proactive health sweep and catch issues while they are still cheap to fix.

```text
> /health
```

NeuBird scans across your infrastructure — metrics, logs, traces, incidents, topology, and cost signals — and produces a structured Good/Bad/Ugly report with evidence and recommended actions.

It also detects degradation signatures before they become incidents. Ask what is most likely to page you next, and NeuBird queries latency percentiles, error rates, resource saturation, and dependency health to tell you where capacity runs out.

### Resolve — Fix what is broken right now

When something is on fire, NeuBird investigates autonomously — querying telemetry, correlating across tools, and delivering root cause analysis with a remediation plan in minutes.

```text
> The checkout service is returning 503s — what's causing it and what should I do?
```

NeuBird traces the failure across service maps, correlates with recent deploys and config changes, checks upstream and downstream dependencies, and returns a step-by-step fix ranked by likelihood and blast radius.

### Optimize — Find the cloud spend you are wasting

```text
> /cost
```

Get a ranked list of waste drivers — metric cardinality bloat, log volume noise, over-provisioned compute, idle resources — with ROI estimates and 7/30-day projections.

---

## It Learns Your Infrastructure

Most AI tools start from zero every session. NeuBird remembers.

The more you use it, the smarter it gets — learning your infrastructure, your preferences, and the investigation patterns that work for your environment. Everything is stored locally and persists across sessions.

### Teach it your role

Tell NeuBird what you care about, and it reshapes how it investigates:

```text
❯ remember my preferences that you should focus on k8s

  🧠 Learned (preference): When investigating incidents, prioritize Kubernetes-layer
     evidence first: pod events, kubelet logs, node conditions, workload status...

  completed in 12.7s

Saved. Going forward I'll lead with Kubernetes-layer evidence — pod events,
kubelet logs, node conditions, workload status (Deployments, DaemonSets,
CronJobs), ECR/image pull issues, and scheduler/controller-manager signals —
before diving into app metrics or traces.
```

This works for any specialization:

```text
❯ you are a network admin, focus on network issues first
  🧠 Learned (preference): Prioritize network-layer evidence first: VPC flow logs,
     security groups, NACLs, DNS resolution, load balancer health, and connectivity...

❯ always check deploy logs before blaming a service
  🧠 Learned (preference): Always check deploy logs before blaming a service...

❯ our payment service has a known 30s timeout that causes false positives in latency alerts
  🧠 Learned (knowledge): Payment service has a known 30s timeout that causes
     false positives in latency alerts...
```

Every 🧠 is a permanent memory. NeuBird carries these forward into every future investigation — no need to repeat yourself.

### What it remembers

NeuBird builds persistent memory across every session:

| What | How it learns | Example |
|---|---|---|
| **Your preferences** | You tell it what to focus on | _"Prioritize Kubernetes-layer evidence first"_ |
| **Tribal knowledge** | You share facts about your environment | _"Payment service has a known 30s timeout"_ |
| **Investigation patterns** | Saved after successful investigations | _"For latency issues, check the API gateway first, then trace upstream"_ |
| **Corrections** | You tell it when it's wrong | _"That's the wrong metric table — use custom\_duration instead"_ |
| **Best practices** | You endorse what works | _"Good — checking deploy logs first saved time"_ |

Some of this comes from you. The rest NeuBird figures out on its own by observing which approaches lead to answers and which hit dead ends.

### It also learns from your feedback

When an investigation completes, NeuBird asks for a 👍 or 👎. That feedback shapes future behavior:

- **👍** — NeuBird notes the approach that worked and repeats it
- **👎** — NeuBird records what to avoid and tries a different path next time
- **Corrections** — Say _"no, check the deployment history first"_ mid-investigation and NeuBird saves it permanently

Over time, NeuBird stops guessing and goes straight to the services, signals, and investigation patterns that work for _your_ environment.

---

## Key Features

**Three agent personas** — Switch investigation styles to match the situation:

| Persona | Model | Best for |
|---|---|---|
| **Responder** | Claude Haiku | Fast triage, immediate next actions |
| **Analyst** | Claude Sonnet | Root cause analysis, deep investigation |
| **Architect** | Claude Opus | Runbooks, design reviews, systemic fixes |

Switch at any time with `/agent`.

**Persistent learning** — NeuBird remembers your preferences, your infrastructure quirks, and which investigation patterns work. It gets faster and more accurate every session. See [It Learns Your Infrastructure](#it-learns-your-infrastructure).

**Collapsible tool output** — Press `Ctrl+]` to review every SQL query and tool result from an investigation. Expand individual calls to inspect the raw data, or collapse them to focus on the analysis.

**Custom slash commands** — Drop a `.md` file into the `skills/` directory to create reusable investigation templates. The filename becomes the command, and the content becomes the prompt.

**Context-aware starter tiles** — On startup, NeuBird analyzes your telemetry schema and suggests relevant investigation starting points. Navigate with arrow keys and hit Enter.

**MCP tool support** — Extend NeuBird with [Model Context Protocol](https://modelcontextprotocol.io/) servers for capabilities beyond SQL.

**Input history & search** — Use `↑`/`↓` to cycle through previous questions, or `Ctrl+R` to search.

---

## Built-In Commands

| Command | What it does |
|---|---|
| `/health` | Full infrastructure health sweep (default: 1h lookback) |
| `/health 4h` | Health sweep with custom lookback window |
| `/cost` | Cloud cost analysis + 24h spend projection |
| `/agent` | Switch agent persona (Responder / Analyst / Architect) |
| `/tables` | List available telemetry tables |
| `/project` | Switch database |
| `/reset` | Clear conversation history |

Or just type a question in plain English.

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
│  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌────────────┐   │
│  │ Discover  │→ │Understand │→ │Investigate│→ │ Synthesize │   │
│  │ schemas   │  │ tables    │  │ execute   │  │ findings   │   │
│  │ & tools   │  │ & signals │  │ queries   │  │ & actions  │   │
│  └───────────┘  └───────────┘  └───────────┘  └────────────┘   │
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

Every claim is grounded in evidence from the data sources it inspected.

---

## What It Connects To

NeuBird integrates with your existing stack through read-only API connections. Nothing to install on your infrastructure.

| Category | Integrations |
|---|---|
| **Monitoring** | Datadog, Splunk, Dynatrace, Grafana, Prometheus, New Relic, CloudWatch |
| **Incident Management** | PagerDuty, OpsGenie, FireHydrant, ServiceNow |
| **Cloud** | AWS, Azure, GCP |
| **Traces** | Grafana Tempo, Jaeger, OpenTelemetry |
| **CI/CD & Code** | GitHub, GitLab, ArgoCD, Jenkins |
| **Communication** | Slack, Jira |
| **Data Warehouses** | Snowflake, BigQuery, Redshift |
| **IaC** | Terraform, Pulumi, Ansible, Helm, Crossplane |

---

## Security

NeuBird is built for enterprises that take security seriously.

- **SOC 2 Type II certified**
- **Zero data persistence** — telemetry is processed in memory and purged after each session
- **Read-only access** — NeuBird never modifies your infrastructure
- **Your data is never used to train models**
- **VPC deployment available** for regulated environments
- **SSO/SAML, RBAC, and full audit trails**

---

## Who It Is For

- **SRE / IT Ops** — Cut MTTR and get root cause in minutes, not hours
- **DevOps / Platform Engineering** — Proactive health checks, cost optimization, and deployment risk analysis from your terminal
- **Engineering Leadership** — Evidence-backed health reports and cost projections on demand

---

## Real-World Results

| Metric | Result |
|---|---|
| **MTTR Reduction** | Up to 90% |
| **Alert Noise Reduction** | 78% |
| **Avg Investigation Time** | ~2 minutes |
| **Cost Reduction** | 70%+ |
| **Average Confidence Score** | 92%+ |

---

## Get Started

```sh
brew install neubirdai/tap/neubird
neubird
```


Questions? Reach us at [neubird.ai](https://neubird.ai) or open an issue in this repo.

---

<p align="center">
  <sub>Built by <a href="https://neubird.ai">NeuBird.ai</a> · Backed by Microsoft M12, Mayfield, and Prosperity7</sub>
</p>

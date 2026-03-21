<p align="center">
  <a href="https://asciinema.org/a/eNVVnr9DfzfTHW4r" target="_blank"><img src="https://asciinema.org/a/eNVVnr9DfzfTHW4r.svg" /></a>
</p>

<h1 align="center">NeuBird Desktop — Production Ops Agent in Your Terminal</h1>

<p align="center">
  <strong>The industry's most accurate AI SRE agent.</strong><br/>
  92%+ confidence score. Learns your infrastructure. Gets smarter every session.<br/>
  Prevent outages. Resolve incidents. Optimize cloud spend.<br/>
  One command. Zero context-switching.
</p>

<p align="center">
  <a href="https://neubird.ai">Website</a> ·
  <a href="https://help.neubird.ai">Docs</a> ·
  <a href="https://github.com/neubirdai/neubird-desktop/releases">Releases</a> ·
  <a href="https://signup.registration.neubird.ai/registrations">Get a Free Account</a>
</p>

---

## Why NeuBird?

Every SRE tool gives you dashboards. NeuBird gives you **answers**.

NeuBird is an **agentic AI SRE platform** that connects to the tools already in your observability and operations stack — Datadog, Splunk, Grafana, PagerDuty, AWS, Azure, GCP, ServiceNow, GitHub, and 30+ more — and reasons across all of them **together**, in real time, from your terminal.

Other AI ops tools pattern-match against logs or summarize alerts. NeuBird **investigates**. It forms hypotheses, queries your telemetry to test them, correlates evidence across data sources, and iterates until it reaches a confident root cause — exactly how a senior SRE works, just in minutes instead of hours.

The result: **92%+ average confidence scores** across production investigations — the highest accuracy of any engineering AI agent in the industry.

```text
┌──────────────────────────────────────────────────────────────────────┐
│                                                                      │
│   You:  "What's quietly degrading that could page me tonight?"       │
│                                                                      │
│   Falcon:                                                            │
│   ⚡ querying trace_grafana_tempo.spans — p99 latency by service      │
│   ⚡ querying metric_datadog.cpu_utilization — saturation check       │
│   ⚡ querying firehydrant.incidents — open incidents last 72h         │
│   ⚡ kubectl get pods -n production — checking pod health             │
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

## How It Works — Agentic Context Engineering

At the core of NeuBird is the **Falcon engine**, powered by **ACE (Agentic Context Engineering)** — a proprietary protocol that dynamically assembles the right context for every investigation step.

Traditional AI tools send a static prompt to an LLM and hope for the best. Falcon does something fundamentally different:

```text
┌─────────────────────────────────────────────────────────────────┐
│                         YOUR TERMINAL                           │
│                       neubird desktop                           │
└──────────────────────┬──────────────────────────────────────────┘
                       │  natural language question
                       ▼
┌─────────────────────────────────────────────────────────────────┐
│                      FALCON ENGINE (ACE)                        │
│                                                                 │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌────────────┐    │
│  │ Context   │→ │ Evidence  │→ │ Agentic   │→ │ Synthesis  │    │
│  │ Assembly  │  │ Gathering │  │ Reasoning │  │ & Review   │    │
│  │           │  │           │  │           │  │            │    │
│  │ Schema    │  │ SQL       │  │ Parallel  │  │ Sonnet     │    │
│  │ Inventory │  │ Queries   │  │ Tool Exec │  │ Analysis   │    │
│  │ Learnings │  │ CLI Tools │  │ Hypothesis│  │    +       │    │
│  │ History   │  │ MCP Calls │  │ Testing   │  │ Opus       │    │
│  │ Skills    │  │ API Calls │  │ Iteration │  │ Review     │    │
│  └───────────┘  └───────────┘  └───────────┘  └────────────┘    │
│                                                                 │
│          confidence tracking at every step (0-100%)             │
└──────────────────────┬──────────────────────────────────────────┘
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
  ┌──────────┐  ┌──────────┐  ┌──────────┐
  │ Datadog  │  │  Splunk  │  │   AWS    │   ... and 30+ more
  │ metrics  │  │   logs   │  │CloudWatch│
  └──────────┘  └──────────┘  └──────────┘
```

**Context Assembly** — Before each investigation, Falcon assembles a precise context window: your telemetry schema inventory, learned SQL patterns, table-to-scenario mappings, your stated preferences, tribal knowledge, and conversation history. This isn't a fixed prompt — it's dynamically engineered for every question.

**Evidence Gathering** — Falcon executes tools in parallel across your entire telemetry stack: SQL queries against your observability data, kubectl commands against your clusters, AWS/Azure/GCP CLI calls for live cloud state, MCP protocol calls to external services — whatever the investigation demands.

**Agentic Reasoning** — Unlike single-shot AI responses, Falcon operates in an iterative loop — up to 25 evidence-gathering cycles per investigation. It forms hypotheses, tests them against real data, refines when evidence contradicts expectations, and tracks its own confidence at every step.

**Two-Stage Synthesis** — Complex investigations get a two-stage review: Claude Sonnet gathers and analyzes evidence, then Claude Opus performs a senior SRE review — checking for consistency, identifying connected failures, and ranking recommendations by blast radius.

The result is an AI agent that doesn't just retrieve data — it **reasons** like the best engineer on your team, backed by evidence from every telemetry source you have.

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
curl -LO https://github.com/neubirdai/neubird-desktop/releases/latest/download/neubird_linux_amd64.deb
sudo dpkg -i neubird_linux_amd64.deb
```

**Linux** (Fedora / RHEL)

```sh
curl -LO https://github.com/neubirdai/neubird-desktop/releases/latest/download/neubird_linux_amd64.rpm
sudo rpm -i neubird_linux_amd64.rpm
```

**Windows**

```powershell
$VERSION = "1.0.32"
Invoke-WebRequest -Uri "https://github.com/neubirdai/neubird-desktop/releases/download/v$VERSION/neubird_${VERSION}_windows_amd64.zip" -OutFile neubird.zip
Expand-Archive neubird.zip -DestinationPath "$env:LOCALAPPDATA\neubird"
$env:PATH += ";$env:LOCALAPPDATA\neubird"
[Environment]::SetEnvironmentVariable("PATH", $env:PATH + ";$env:LOCALAPPDATA\neubird", "User")
```

**Docker**

```sh
docker run -it --rm \
  -e ANTHROPIC_API_KEY=sk-ant-... \
  neubirdai/neubird-desktop:latest
```

**Other platforms** — pre-built binaries for macOS (Apple Silicon + Intel), Linux (x86_64 + ARM64), and Windows (x86_64) are available on the [releases page](https://github.com/neubirdai/neubird-desktop/releases/latest).

### 2. Connect your account

Sign up at **[neubird.ai/signup](https://signup.registration.neubird.ai/registrations)** if you don't have an account yet.

NeuBird connects to your existing telemetry tools via read-only API keys. No agents to install. No infrastructure changes.

### 3. Launch

```sh
neubird
```

NeuBird discovers your telemetry inventory, maps your schemas, detects local CLI tools on your machine, and drops you into an interactive terminal session. Ask anything.

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

```text
> /health
```

NeuBird scans across your entire infrastructure — metrics, logs, traces, incidents, topology, and cost signals — and produces a structured **Good / Bad / Ugly** report with evidence and recommended actions.

It detects degradation signatures before they become incidents. Ask what's most likely to page you next, and NeuBird queries latency percentiles, error rates, resource saturation, and dependency health to tell you exactly where capacity runs out.

Every finding is backed by the specific query and data source that produced it. No guessing. No hallucination.

### Resolve — Fix what's broken right now

```text
> The checkout service is returning 503s — what's causing it and what should I do?
```

NeuBird traces the failure across service maps, correlates with recent deploys and config changes, checks upstream and downstream dependencies, reads live pod logs via kubectl, and returns a step-by-step remediation plan ranked by likelihood and blast radius.

Complex investigations trigger a **two-stage review**: Sonnet gathers evidence and analyzes, then Opus performs a senior SRE review — checking for consistency across telemetry types, identifying connected failures, and providing a 72-hour outlook.

### Optimize — Find the cloud spend you're wasting

```text
> /cost
```

Get a ranked breakdown of waste drivers — metric cardinality bloat, log volume noise, over-provisioned compute, idle resources — with ROI estimates and 7/30-day spend projections. NeuBird queries your actual utilization data and trends, not just billing dashboards.

### Assess — Evaluate risk before it reaches production

```text
> Before we deploy this release — what's the risk?
```

NeuBird cross-references your PRs and recent code changes with live telemetry to assess deployment risk. It checks the health of every service the change touches, looks for correlation between past deploys and incidents, and tells you what could break and why.

---

## It Learns Your Infrastructure

Most AI tools start from zero every session. NeuBird remembers **everything**.

The more you use it, the smarter it gets — learning your infrastructure, your preferences, and the investigation patterns that work for your environment. Everything is stored locally and persists across sessions.

### Teach it your role

Tell NeuBird what you care about, and it reshapes how it investigates:

```text
❯ remember that you should focus on k8s first

  🧠 Learned (preference): When investigating incidents, prioritize Kubernetes-layer
     evidence first: pod events, kubelet logs, node conditions, workload status...

❯ our payment service has a known 30s timeout that causes false positives
  🧠 Learned (knowledge): Payment service has a known 30s timeout that causes
     false positives in latency alerts...

❯ always check deploy logs before blaming a service
  🧠 Learned (preference): Always check deploy logs before blaming a service...
```

Every 🧠 is a permanent memory. NeuBird carries these forward into every future investigation — no need to repeat yourself.

### Four types of persistent memory

| What | How it learns | Example |
|---|---|---|
| **Your preferences** | You tell it what to focus on | _"Prioritize Kubernetes-layer evidence first"_ |
| **Tribal knowledge** | You share facts about your environment | _"Payment service has a known 30s timeout"_ |
| **SQL patterns** | Automatically saved when queries succeed or fail | _"Never use JOIN on this data source — use separate queries"_ |
| **Table mappings** | Saved after successful investigations | _"For latency issues, use traces.spans + metrics.http\_duration"_ |

Some of this comes from you. The rest NeuBird figures out on its own by observing which approaches lead to answers and which hit dead ends.

### It learns from your feedback too

When an investigation completes, NeuBird asks for a 👍 or 👎:

- **👍** — NeuBird records the approach that worked and repeats it
- **👎** — NeuBird records what to avoid and tries a different path next time
- **Corrections** — Say _"no, check the deployment history first"_ mid-investigation and NeuBird saves it permanently

Over time, NeuBird stops guessing and goes straight to the services, signals, and investigation patterns that work for _your_ environment. This is how it maintains **92%+ confidence** — it's not just a good model, it's a model that knows your infrastructure.

---

## Capabilities

### Three Agent Personas

Switch investigation styles to match the situation:

| Persona | Model | Best for |
|---|---|---|
| **Responder** | Claude Haiku | Fast triage, immediate next actions, quick lookups |
| **Analyst** | Claude Sonnet | Root cause analysis, deep multi-source investigation |
| **Architect** | Claude Opus | Runbooks, design reviews, systemic fixes, capacity planning |

Switch anytime with `/agent`. Each persona brings a different investigation style — Responder is fast and direct, Analyst is thorough and evidence-driven, Architect thinks in systems and long-term patterns.

### Local CLI Integration

NeuBird automatically detects SRE tools installed on your machine and makes them available as read-only investigation tools:

```text
💻 Local CLI (9)
   ✓ kubectl     Kubernetes: pods, services, logs, events, resource usage
   ✓ docker      Container: ps, inspect, logs, stats, images
   ✓ aws         AWS CLI: CloudWatch metrics, EC2/ECS describe, S3 list
   ✓ az          Azure CLI: AKS, Monitor, Log Analytics, resources
   ✓ git         Git: recent commits, diffs, blame, branch info
   ✓ curl        HTTP: endpoint health checks, API probing
   ✓ dig         DNS: resolution checks, record lookups
   ✓ openssl     TLS/SSL: certificate expiry checks
   ✓ jq          JSON processing (support tool)
```

The agent picks the fastest path to an answer — database when the data exists there, local CLI when it doesn't. Ask _"list my EC2 instances"_ and it queries the telemetry database in 2 seconds. Ask _"are my AWS credentials working?"_ and it runs `aws sts get-caller-identity` locally.

All commands are **safety-gated at the code level**. Destructive operations (apply, delete, create, scale, docker run, git push) are blocked regardless of what the LLM requests. NeuBird is read-only by design.

### Tool Inventory

On startup, NeuBird displays every tool available to the agent — grouped by source:

```text
🔧 Tool inventory (28 tools)
  📦 Built-in (5)
     ✓ code_execution           Run code in a sandboxed environment
     ✓ save_sql_learning        Persist SQL generation rules
     ...
  ☁️  ACE MCP (21)
     ✓ exec_sql                 Execute SQL queries against the database
     ✓ list_incidents           List detected incidents
     ✓ external_tool            Interface to external integrations
     ...
  💻 Local CLI (9)
     ✓ kubectl                  Kubernetes: pods, logs, events (read-only)
     ✓ aws                      AWS CLI: CloudWatch, EC2, S3, IAM
     ...
```

Run `/tools` anytime to see the full inventory with capabilities.

### Skills — Custom Investigation Templates

Drop a `.md` file into the skills directory to create reusable investigation playbooks. The filename becomes a slash command, and the content becomes the investigation prompt:

```text
# ~/.config/neubird/skills/sev-hunt.md

You are investigating a potential SEV. Follow this procedure:
1. Check for open incidents in the last 4 hours
2. Query error rates by service for the same window
3. Correlate with recent deployments
4. Check pod health and restart counts
5. Produce a severity assessment with blast radius
```

Skills loaded from your NeuBird project are also available — managed centrally and shared across your team.

### Live Investigation Review

Press `Ctrl+O` **during or after** an investigation to enter tool review mode. Browse every query, every tool call, every result:

- **↑ / ↓** — Navigate between tool calls
- **Enter** — Expand/collapse to see full data tables
- **Esc** — Resume watching the investigation

This works mid-investigation — pause to inspect a query result, then resume watching. Every SQL query, kubectl output, and API response is preserved for inspection.

### MCP Extensibility

Extend NeuBird with any [Model Context Protocol](https://modelcontextprotocol.io/) server — local processes or remote HTTP endpoints:

```sh
# Add a local MCP server
neubird mcp add my-server /usr/local/bin/my-mcp-server

# Add a remote HTTP endpoint
neubird mcp add my-api https://mcp.example.com/mcp --header "Authorization: Bearer ..."

# List configured servers
neubird mcp list
```

MCP tools appear in the tool inventory alongside built-in and local CLI tools, and are available to the agent for every investigation.

### Context-Aware Welcome

On every launch, NeuBird shows rotating example questions tailored to your telemetry — demonstrating capabilities you might not have tried yet:

```text
  Try asking something like...

  ╭──────────────────────────────────────────────────────────────╮
  │  🚨 Incident Response                                        │
  │  Dan is complaining about apps crashing and blaming storage  │
  │  — what actually happened in the last 2 hours?               │
  ╰──────────────────────────────────────────────────────────────╯
  ╭──────────────────────────────────────────────────────────────╮
  │  💰 Cost & Efficiency                                        │
  │  Where are we bleeding money on idle compute and high-       │
  │  cardinality metrics nobody queries?                         │
  ╰──────────────────────────────────────────────────────────────╯
```

These are generated using your actual telemetry inventory — not generic prompts.

---

## Built-In Commands

| Command | What it does |
|---|---|
| `/health` | Full infrastructure health sweep (default: 1h lookback) |
| `/health 4h` | Health sweep with custom lookback window |
| `/cost` | Cloud cost analysis + 24h spend projection |
| `/agent` | Switch agent persona (Responder / Analyst / Architect) |
| `/tools` | Show all available tools with capabilities |
| `/skills` | List available investigation skills |
| `/tables` | List available telemetry tables |
| `/mcp` | Show MCP server status |
| `/project` | Switch database / project |
| `/reset` | Clear conversation history |
| `/clear` | Clear terminal display |
| `/tiles` | Show welcome tiles |

Or just type a question in plain English.

### Keyboard Shortcuts

| Key | Action |
|---|---|
| `Enter` | Submit question |
| `Esc` | Cancel investigation / exit mode |
| `Ctrl+O` | Tool review mode (works mid-investigation) |
| `↑ / ↓` | Navigate input history / tool calls |
| `Ctrl+R` | Reverse search through history |
| `← / →` | Navigate welcome tiles |
| `Tab` | Accept suggestion / complete command |
| `?` | Toggle shortcut overlay |
| `Ctrl+C` (twice) | Quit |

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
| **Communication** | Slack, Jira, Confluence |
| **Data Warehouses** | Snowflake, BigQuery, Redshift |
| **IaC** | Terraform, Pulumi, Ansible, Helm, Crossplane |
| **Local CLI** | kubectl, helm, docker, AWS CLI, gcloud, Azure CLI, git, terraform, curl, dig, openssl |

---

## Security

NeuBird is built for enterprises that take security seriously.

- **SOC 2 Type II certified**
- **Zero data persistence** — telemetry is processed in memory and purged after each session
- **Read-only by design** — NeuBird never modifies your infrastructure. Local CLI tools are safety-gated at the code level: destructive operations are blocked regardless of LLM output
- **Your data is never used to train models**
- **VPC deployment available** for regulated environments
- **SSO/SAML, RBAC, and full audit trails**

---

## Who It's For

**SRE / IT Ops** — Cut MTTR from hours to minutes. Get root cause analysis backed by evidence from every telemetry source, not guesswork.

**DevOps / Platform Engineering** — Proactive health sweeps, cost optimization, deployment risk assessment, and capacity planning — all from your terminal.

**Engineering Leadership** — Evidence-backed health reports and cost projections on demand. Every claim links to the data source that produced it.

---

## Real-World Results

| Metric | Result |
|---|---|
| **MTTR Reduction** | Up to 90% |
| **Alert Noise Reduction** | 78% |
| **Avg Investigation Time** | ~2 minutes |
| **Cost Savings Identified** | 70%+ |
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

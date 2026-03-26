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

---

## What Can It Do?

### Prevent — Stop incidents before they start

```text
> /health
```

NeuBird scans across your entire infrastructure — metrics, logs, traces, incidents, topology, and cost signals — and produces a structured **Good / Bad / Ugly** report with evidence and recommended actions.

It detects degradation signatures before they become incidents. Ask what's most likely to page you next, and NeuBird queries latency percentiles, error rates, resource saturation, and dependency health to tell you exactly where capacity runs out.

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

Get a ranked breakdown of waste drivers — metric cardinality bloat, log volume noise, over-provisioned compute, idle resources — with ROI estimates and 7/30-day spend projections.

### Watch — Continuous background monitoring

```text
> /watch 2h
  👁️ Watch mode enabled — sweeping every 2h. First sweep starting now...
```

NeuBird runs health assessments on a timer, compares against the previous sweep, and only interrupts you when something **changed**. Quiet when nothing's wrong. Loud when it matters. Use `/watch off` to disable.

---

## 🧩 Make It Yours — Skills & Playbooks

NeuBird isn't a black box. It's a platform you extend with your own operational knowledge.

**Skills** are simple Markdown files that turn your team's runbooks, checklists, and investigation patterns into slash commands the AI agent follows. No code. No APIs. Just a `.md` file.

### How it works

Create a file. The filename becomes the command. The content becomes the investigation plan.

```markdown
# ~/.config/neubird/skills/deploy-check.md

# Pre-deployment safety check

Before approving this deploy, investigate:
1. Current error rates for all services this PR touches
2. Any open incidents or active alerts on those services
3. Resource utilization — are we close to any limits?
4. Recent deploys in the last 24h that might compound risk
5. Dependency health — are upstream/downstream services healthy?

Produce a GO / NO-GO recommendation with evidence for each point.
```

That's it. Next time you launch NeuBird, `/deploy-check` appears as a command. Type it and the agent follows your procedure exactly — using all 28+ tools at its disposal to gather evidence and produce the report you designed.

### Why this matters

Every team has tribal knowledge trapped in wikis nobody reads, runbooks that are always outdated, and checklists that only exist in senior engineers' heads. Skills turn all of that into **executable automation**:

- **Your on-call handoff** becomes `/handoff` — a structured briefing generated from live telemetry every shift change
- **Your incident review process** becomes `/pir` — a 5-whys analysis with timeline, impact assessment, and action items
- **Your pre-deploy checklist** becomes `/deploy-check` — evidence-backed GO/NO-GO that juniors and seniors get the same quality from
- **Your capacity planning** becomes `/capacity` — projected exhaustion dates for every resource you track

The agent brings the intelligence, the tools, and the telemetry access. **You bring the procedure.** Together, it's your team's best engineer available 24/7.

### Built-in skills

NeuBird ships with ready-to-use playbooks for the most common SRE workflows:

| Command | What it does |
|---|---|
| `/health` | Full infrastructure health sweep — Good/Bad/Ugly report |
| `/cost` | Cloud cost analysis + 24h spend projection |
| `/handoff` | On-call shift briefing — active incidents, recent deploys, health, watch items |
| `/changes` | Compare two time windows — find every deploy, config change, and metric shift |
| `/timeline` | Reconstruct a minute-by-minute incident timeline from all telemetry |
| `/pir` | Post-incident review — timeline, 5-whys, impact, action items |
| `/slo` | SLO burn rate — error budgets, projections, breach forecasts |
| `/blast-radius` | Map upstream/downstream dependencies, quantify failure impact |
| `/certs` | Scan TLS certificates, flag anything expiring within 30 days |
| `/sev-hunt` | Hunt for active SEVs and brewing incidents |
| `/weekend-check` | Pre-weekend risk assessment |
| `/remediation-steps` | Suggest remediation steps with safety tiers |

These work out of the box. No configuration needed.

### Create your own in 60 seconds

```bash
mkdir -p ~/.config/neubird/skills

cat > ~/.config/neubird/skills/morning-standup.md << 'EOF'
# Morning standup infrastructure summary

Generate a 2-minute standup update:
1. What broke overnight? Check incidents and alerts from the last 12h
2. What shipped? List deploys and config changes since yesterday
3. What's at risk? Any services trending toward SLO breach
4. What needs attention today? Expiring certs, capacity warnings, pending rollbacks

Keep it brief. Bullet points. Link every claim to a data source.
EOF
```

Restart NeuBird → `/morning-standup` is ready. Your entire team can use the same skill by sharing the `.md` file.

### Skill priority

Skills load from three sources (later overrides earlier):

1. **Built-in** — ships with NeuBird, always available
2. **Project directory** — `skills/` in your working directory (great for team repos)
3. **Personal** — `~/.config/neubird/skills/` (your own customizations)

Override any built-in by creating a file with the same name in your personal directory. Your version wins.

### Ideas for your team

| Skill | Use case |
|---|---|
| `/morning-standup` | Auto-generate the infrastructure section of your daily standup |
| `/deploy-check` | Pre-deploy risk assessment tailored to your services |
| `/customer-impact` | Translate infrastructure issues into customer-facing language for status pages |
| `/capacity-forecast` | Monthly capacity report for leadership with growth projections |
| `/security-audit` | Check for exposed endpoints, outdated certs, misconfigured security groups |
| `/db-health` | Database-specific health check: slow queries, connection pools, replication lag |
| `/k8s-audit` | Kubernetes resource audit: orphaned pods, over-provisioned requests, pending PVCs |
| `/cost-by-team` | Break down cloud costs by team/namespace/service owner |
| `/changelog` | Generate a human-readable changelog from deploy and PR data |
| `/escalation` | Assess whether an incident should be escalated — severity, blast radius, customer impact |

The pattern is always the same: describe what you want investigated, let the agent figure out which tools to use and which data to query.

---

## It Learns Your Infrastructure

Most AI tools start from zero every session. NeuBird remembers **everything**.

The more you use it, the smarter it gets — learning your infrastructure, your preferences, and the investigation patterns that work for your environment. Everything is stored locally and persists across sessions.

### Teach it your role

```text
❯ remember that you should focus on k8s first
  🧠 Learned (preference): Prioritize Kubernetes-layer evidence first...

❯ our payment service has a known 30s timeout that causes false positives
  🧠 Learned (knowledge): Payment service has a known 30s timeout...

❯ always check deploy logs before blaming a service
  🧠 Learned (preference): Always check deploy logs before blaming a service...
```

Every 🧠 is a permanent memory. NeuBird carries these forward into every future investigation.

### Four types of persistent memory

| What | How it learns | Example |
|---|---|---|
| **Your preferences** | You tell it what to focus on | _"Prioritize Kubernetes-layer evidence first"_ |
| **Tribal knowledge** | You share facts about your environment | _"Payment service has a known 30s timeout"_ |
| **SQL patterns** | Automatically saved when queries succeed or fail | _"Never use JOIN on this data source"_ |
| **Table mappings** | Saved after successful investigations | _"For latency issues, use traces.spans + metrics.http\_duration"_ |

### It learns from your feedback too

When an investigation completes, NeuBird asks for a 👍 or 👎. That feedback shapes future behavior — over time, NeuBird stops guessing and goes straight to the services, signals, and investigation patterns that work for _your_ environment.

---

## More Capabilities

### Three Agent Personas

| Persona | Model | Best for |
|---|---|---|
| **Responder** | Claude Haiku | Fast triage, immediate next actions, quick lookups |
| **Analyst** | Claude Sonnet | Root cause analysis, deep multi-source investigation |
| **Architect** | Claude Opus | Runbooks, design reviews, systemic fixes, capacity planning |

Switch anytime with `/agent`.

### Local CLI Integration

NeuBird can use kubectl on your machine as a read-only investigation tool. The agent picks the fastest path: database when data exists there, local CLI when it doesn't.

All commands are **safety-gated at the code level**. Destructive operations are blocked regardless of LLM output.

#### Enabling Local Tools

To enable local tools such as `kubectl`, set the following environment variable before launching NeuBird:

```sh
export HAWKEYE_LOCAL_TOOLS=true
neubird
```

When enabled, NeuBird gains access to `kubectl` as a local tool, restricted to **read-only operations** only. This lets the agent query your Kubernetes clusters directly — inspecting pods, services, logs, events, and more — without any risk of modifying cluster state.

### Live Investigation Review

Press `Ctrl+O` **during or after** an investigation to browse every query and tool result. Expand individual calls to see full data tables. Works mid-investigation — pause, inspect, resume.

### MCP Extensibility

Extend NeuBird with any [Model Context Protocol](https://modelcontextprotocol.io/) server:

```sh
neubird mcp add my-server /usr/local/bin/my-mcp-server
neubird mcp add my-api https://mcp.example.com/mcp --header "Authorization: Bearer ..."
```

---

## Built-In Commands

| Command | What it does |
|---|---|
| `/health` | Infrastructure health sweep (default: 1h) |
| `/health 4h` | Health sweep with custom lookback |
| `/cost` | Cloud cost analysis + 24h projection |
| `/handoff` | On-call shift briefing |
| `/changes` | What changed? — compare time windows |
| `/timeline` | Reconstruct incident timeline |
| `/pir` | Post-incident review |
| `/slo` | SLO burn rate check |
| `/blast-radius` | Map failure blast radius |
| `/certs` | TLS certificate expiry scan |
| `/watch` | Background health sweep (every 4h) |
| `/watch off` | Stop background sweeps |
| `/agent` | Switch persona |
| `/tools` | Show all tools with capabilities |
| `/skills` | List available skills |
| `/tables` | List telemetry tables |
| `/mcp` | MCP server status |
| `/project` | Switch database |
| `/reset` | Clear conversation history |

Or just type a question in plain English.

### Keyboard Shortcuts

| Key | Action |
|---|---|
| `Enter` | Submit question |
| `Esc` | Cancel investigation / exit mode |
| `Ctrl+O` | Tool review (works mid-investigation) |
| `↑ / ↓` | Input history / navigate tool calls |
| `Ctrl+R` | Reverse search history |
| `← / →` | Navigate welcome tiles |
| `Tab` | Accept suggestion / complete command |
| `?` | Toggle shortcut overlay |
| `Ctrl+C` ×2 | Quit |

---

## What It Connects To

| Category | Integrations |
|---|---|
| **Monitoring** | Datadog, Splunk, Dynatrace, Grafana, Prometheus, New Relic, CloudWatch |
| **Incidents** | PagerDuty, OpsGenie, FireHydrant, ServiceNow |
| **Cloud** | AWS, Azure, GCP |
| **Traces** | Grafana Tempo, Jaeger, OpenTelemetry |
| **CI/CD** | GitHub, GitLab, ArgoCD, Jenkins |
| **Communication** | Slack, Jira, Confluence |
| **Data** | Snowflake, BigQuery, Redshift |
| **IaC** | Terraform, Pulumi, Ansible, Helm, Crossplane |
| **Local CLI** | kubectl |

---

## Security

- **SOC 2 Type II certified**
- **Zero data persistence** — telemetry processed in memory, purged after each session
- **Read-only by design** — NeuBird never modifies your infrastructure. Local CLI safety-gated at the code level
- **Your data is never used to train models**
- **VPC deployment available** for regulated environments
- **SSO/SAML, RBAC, and full audit trails**

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

Questions? Reach us at [neubird.ai](https://neubird.ai) or open an issue.

---

<p align="center">
  <sub>Built by <a href="https://neubird.ai">NeuBird.ai</a> · Backed by Microsoft M12, Mayfield, and Prosperity7</sub>
</p>

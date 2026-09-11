# General Agents on the Web — Hands-On Projects

> A hands-on project series exploring AI agents, tools, connectors, approval gates, cloud workflows, multi-harness execution, scheduling, and portability.

## 🎯 About This Repository

This repository documents a series of hands-on experiments exploring how AI agents actually work in practice. Rather than treating agents as black boxes, these projects examine:

- **Where agent actions execute** — cloud infrastructure, local systems, or connected services
- **How tools and connectors bridge agents to external systems** — web fetches, file storage, cloud APIs
- **Approval gates and human control** — when and how users retain visibility over agent actions
- **Cloud-native workflows** — designing automation that runs entirely without local dependencies
- **Comparing different agent harnesses** — understanding the shared six-part architecture across platforms
- **Portability and vendor lock-in** — whether workflows can survive beyond a single platform
- **Evidence-based verification** — what constitutes honest proof that something actually works

Each project is intentionally scoped, tests one clear question, and documents both what succeeded and what remains unverified.

## 🧠 What I Learned

Across these six projects, several key insights emerged:

1. **Agent thinking and tool execution are decoupled** — Claude's reasoning happens in the cloud, but tools can run on local infrastructure, cloud services, or distributed systems. Where tools execute depends on your setup, not the agent itself.

2. **Data lives in three distinct tiers** — session context (temporary, platform-dependent), platform storage (vendor-controlled), and local exports (truly owned). Planning for vendor loss means understanding which tier your data occupies.

3. **Approval gates are workflow controls, not safety systems** — they determine *when* users are asked for permission, not *whether* actions are safe. Both manual and automatic modes assume trustworthy agents and appropriate actions.

4. **Cloud workflows enable autonomous automation** — moving workflows entirely to cloud platforms eliminates local runtime dependencies, but introduces new verification challenges: how do you prove unattended execution actually happened?

5. **Different platforms implement the same six-part harness** — heartbeat, reach, run-until-done loop, state spine, human gate, and body structure all agent systems, but implementations vary in storage integration, state visibility, and approval transparency.

6. **Portability requires explicit documentation of execution details** — the *concept* of a workflow can survive platform loss if well-documented, but rebuilding actual *execution* fails when critical details (instructions, data sources, configuration) exist only inside the platform and were never written down.

7. **Unattended execution is hard to verify** — scheduling a task is easy; proving it actually ran successfully without manual intervention requires deliberate verification planning from the start.

## 📚 Project Roadmap

| # | Project | Main Concept | Status |
|---|---|---|---|
| 1 | Worker/Tool-Location Test | Where agent thinking and tool execution happen | ✅ Core test completed |
| 2 | Three-Tier Audit | Where AI-generated outputs live across platforms | ✅ Completed |
| 3 | The Gate Lab | Approval gates: manual vs automatic approval behavior | ✅ Completed |
| 4 | The First Cloud Schedule | Cloud-native Monday Brief workflow and scheduling | ⏳ Unattended execution pending |
| 5 | One Task, Two Harnesses | Comparing Claude Cowork and ChatGPT Work structure | ✅ Completed |
| 6 | The Portability Drill | Reconstructing Project 4 from documentation | ✅ Completed |

---

## 1. Worker Tool Location Test

**Purpose:** Understand where Claude's reasoning happens versus where tool actions (like web fetches) actually execute.

**What Was Tested:**
- Opened Claude.ai and asked it to read and summarize a Wikipedia page
- Closed the browser tab completely, then reopened the conversation
- Verified that cloud sessions persist after local browser closure

**Key Findings:**
- Claude's reasoning and response generation happen in the cloud (Anthropic's servers)
- Tool execution location depends on the setup — in Claude.ai web, tools likely run on Claude's infrastructure
- Cloud conversations persist across browser closures; session state survives on the platform
- This demonstrates that agents are decoupled from the client application

**Scope & Limitations:**
- Only tested Claude.ai web platform; Claude Desktop not installed, so local tool execution was not tested
- Only web fetch tested; other tool types (shell commands, file access) not explored
- Cannot definitively confirm where web-fetch tools execute without infrastructure access

**Link:** [`01-worker-tool-location-test/README.md`](01-worker-tool-location-test/README.md)

---

## 2. Three-Tier Audit

**Purpose:** Examine where AI-generated outputs actually live and what happens if vendor access disappears.

**What Was Examined:**
- Created a study document on Claude.ai about "The Three States of Matter"
- Mapped the document's location across three tiers:
  - **Tier 1 (Session Context):** The live conversation in Claude.ai
  - **Tier 2 (Platform Storage):** Generated content stored on Claude's servers
  - **Tier 3 (Local Export):** Downloaded file saved locally as `.md`
- Verified that the document survives as an independent local copy

**Key Findings:**
- Generated content can be exported from the platform and saved locally
- Locally saved files exist independently of the platform
- Understanding data tiers helps reveal what survives vendor loss

**Scope & Limitations:**
- Only Claude.ai tested; other platforms not evaluated
- Only document generation tested; other workflows not explored
- No testing of long-term platform persistence or account deletion scenarios

**Link:** [`02-three-tier-audit/README.md`](02-three-tier-audit/README.md)

---

## 3. The Gate Lab

**Purpose:** Demonstrate how approval gates work when agents perform actions through external services.

**What Was Tested:**
- Created harmless test files in Google Drive using Claude.ai Cowork
- **Manual Approval Mode:** Requested file creation; Claude asked for explicit permission before proceeding
- **Automatic Approval Mode:** Requested file creation; Claude proceeded immediately without asking

**Key Findings:**
- Approval gates control *when* users are asked for permission, not *whether* actions are safe
- Manual mode requires explicit user approval before each action
- Automatic mode allows fast workflows for low-risk, reversible tasks
- Claude.ai Cowork explicitly surfaces approval state ("Automatically approve is on")
- Both modes successfully created files; only the workflow control differed

**Scope & Limitations:**
- Only Google Drive file creation tested; other action types not explored
- Only Claude.ai Cowork tested; other platforms and services not evaluated
- Only harmless test files used; no real data modifications tested
- Approval gates are workflow tools, not safety systems

**Link:** [`03-gate-lab/README.md`](03-gate-lab/README.md)

---

## 4. The First Cloud Schedule

**Purpose:** Build and schedule a cloud-native AI workflow that runs entirely without local dependencies.

**What Was Built:**
- **Workflow:** "Monday Brief" — gathers weekly insights from web sources and Google Drive, generates structured brief
- **Platform:** Claude.ai Cowork (cloud-only, no local runtime required)
- **Trigger:** Cloud scheduler, weekly, Monday mornings
- **Output:** Structured text document saved to Google Drive

**Workflow Design Process:**
The workflow was designed by explicitly answering six required questions:
1. **Purpose:** Gather weekly insights from web sources and Google Drive
2. **Data Sources:** Cloud-reachable web sources and existing Google Drive files
3. **Trigger Mechanism:** Cloud scheduler, Monday mornings, weekly
4. **Output Location:** Google Drive ("Gate-Lab-Test" folder)
5. **Output Format:** Structured text with key insights and actionable items
6. **Monitoring:** Check Google Drive for output and monitor scheduler status

**Verification:**
- Manual test executed successfully
- Workflow produced expected output and correctly saved to Google Drive
- Cloud scheduler configured and waiting for first automatic execution

**Current Status:**
> Cloud-only workflow designed and scheduled; unattended scheduled firing verification pending.

The workflow is ready and properly configured. Proof of autonomous operation requires the scheduler to fire at its designated time.

**Why Unattended Execution Matters:**
- Validates that the scheduling configuration is correct
- Demonstrates the workflow handles edge cases without user guidance
- Proves the system maintains consistency across multiple runs
- Shows cloud automation is truly automated, not just manually triggered

**Scope & Limitations:**
- Scheduled task has not yet fired automatically
- Only one manual test performed; recurring behavior not validated
- Long-term stability across multiple weeks not tested
- Edge cases and failure recovery not explored

**Link:** [`04-first-cloud-schedule/README.md`](04-first-cloud-schedule/README.md)

---

## 5. One Task, Two Harnesses

**Purpose:** Compare Claude Cowork and ChatGPT Work using the same harmless task through a six-part harness lens.

**What Was Tested:**
Both platforms received this identical, harmless task:
```
Create a text file named harness-comparison-test.txt
with content: "Harness Comparison Test - This is a harmless test file created for Project 5."
```

**Six-Part Harness Comparison:**

The framework examined:
1. **Heartbeat** — How the platform picks up and processes tasks
2. **Reach** — What external systems and integrations the platform can access
3. **Run-Until-Done Loop** — How the platform executes tasks to completion
4. **State Spine** — How task state is tracked and persisted
5. **Human Gate** — Approval and control mechanisms over agent actions
6. **Body** — Core task execution and output delivery

**Observable Differences Found:**
- **Reach:** Claude Cowork integrated with Google Drive (cloud storage); ChatGPT provided downloadable file (local delivery)
- **State Spine:** Claude Cowork explicitly displayed "Automatically approve is on"; ChatGPT showed no approval-state message
- **Body:** Claude Cowork delivered via Google Drive interface; ChatGPT provided file for direct download

**Key Insight:**
Both platforms successfully completed the task and implement the same six-part harness structure, but deliver outputs through different integrations. A single harmless task doesn't fully stress-test either system's error handling, approval requirements, or complex scenarios.

**Scope & Limitations:**
- Only one simple task tested; doesn't reveal how systems handle errors or require human approval
- Cannot determine internal heartbeat intervals or full state persistence from successful execution
- Complex multi-step tasks, long-running operations, and state persistence across sessions not tested

**Link:** [`05-one-task-two-harnesses/README.md`](05-one-task-two-harnesses/README.md)

---

## 6. The Portability Drill

**Purpose:** Test whether a real cloud-native workflow can be reconstructed entirely from owned, documented material.

**Scenario:**
Imagine Claude.ai Cowork disappears tomorrow. Using only the documentation you've saved, could you rebuild the workflow?

**Workflow Selected:**
Project 4's "Monday Brief" — a complete, real cloud workflow that integrates web sources, Google Drive, and cloud scheduling.

**What Could Be Reconstructed:**
From Project 4 documentation:
- ✅ Workflow purpose and overall design
- ✅ Input sources (web sources + Google Drive files)
- ✅ Output destination and format (Google Drive, structured text)
- ✅ Trigger mechanism (cloud scheduler, Monday mornings)
- ✅ General execution flow (gather insights → generate brief → save output)
- ✅ Verification approach (check Google Drive and scheduler status)

**What Could NOT Be Reconstructed:**
- ❌ Exact Claude instructions or prompts used to analyze data
- ❌ Specific web sources queried (only "cloud-reachable sources" documented)
- ❌ Specific Google Drive files used as input
- ❌ Exact scheduler configuration (time, timezone, retry policy)
- ❌ How "key insights" and "actionable items" were defined
- ❌ Authentication and API integration details
- ❌ Verification that unattended execution actually happens

**Key Finding:**
> The workflow design can be reconstructed from the available Project 4 documentation, but its unattended execution was not fully verified.

The *concept* survives documentation, but the *implementation* doesn't. Critical details exist only inside the platform and were never written down.

**Portability Gaps Exposed:**
- Instructions and reasoning logic are platform-specific
- Data source selection criteria are implicit, not documented
- Scheduler configuration is internal to Claude.ai Cowork
- No unattended execution verification plan existed
- Error handling and edge cases were not documented

**Why This Matters:**
Workflows that depend on undocumented platform-specific features are at risk. For truly portable automation, you must document not just *what* happens, but *how* it happens and *with what instructions*.

**Link:** [`06-portability-drill/README.md`](06-portability-drill/README.md)

---

## 🔍 Key Concepts

| Concept | Definition | Projects |
|---------|-----------|----------|
| **Agent** | An AI system that reasons and takes actions through tools | 1–6 |
| **Tool Execution** | Where agent-requested actions actually run (cloud, local, external) | 1 |
| **Cloud Infrastructure** | Where agent reasoning, data, and workflows live | 1, 2, 4 |
| **Connector** | Integration between agent and external service (e.g., Google Drive) | 3, 4, 5 |
| **Approval Gate** | Control point determining when user permission is required | 3, 5 |
| **Manual Approval** | User must explicitly approve each action | 3 |
| **Automatic Approval** | Actions proceed without asking for permission | 3 |
| **Data Tiers** | Session context, platform storage, and local exports | 2 |
| **Platform Persistence** | How conversation and session state survive beyond client closure | 1, 2 |
| **Vendor Lock-in** | Workflow elements specific to one platform that don't transfer | 6 |
| **Portability** | Ability to reconstruct and rebuild workflows from documentation | 6 |
| **Six-Part Harness** | Framework: heartbeat, reach, run-until-done, state spine, human gate, body | 5 |
| **Unattended Execution** | Automated workflow running without human intervention | 4, 6 |
| **Cloud-Native Workflow** | Automation running entirely on cloud services without local dependencies | 4, 6 |

---

## 🛠️ Platforms & Tools

**Platforms Tested:**
- Claude.ai Cowork (cloud collaboration mode)
- Claude.ai web (standard chat interface)
- ChatGPT Work (ChatGPT's agent harness)

**External Services & Integrations:**
- Google Drive (file creation, storage, retrieval)
- Web fetch (reading external web pages)
- Cloud Scheduler (automated task triggering)

**Workflow & Documentation:**
- Markdown documentation
- Text file generation
- Scheduled automation

---

## 🗂️ Repository Structure

```
General-Agents-On-The-Web-Projects/
├── 01-worker-tool-location-test/
│   └── README.md                          # Where agent thinking vs tools execute
├── 02-three-tier-audit/
│   └── README.md                          # Where AI outputs live across tiers
├── 03-gate-lab/
│   └── README.md                          # Approval gates and workflow control
├── 04-first-cloud-schedule/
│   ├── README.md                          # Cloud workflow design and scheduling
│   ├── TEST_CASE.md                       # Manual test execution
│   └── COMPLETION_REPORT.md               # Summary and findings
├── 05-one-task-two-harnesses/
│   └── README.md                          # Comparing agent platforms
├── 06-portability-drill/
│   ├── README.md                          # Portability and reconstruction test
│   └── PORTABILITY_GAPS.md                # Detailed gaps and missing documentation
└── README.md                              # This file
```

Each project folder contains its own complete documentation, including purpose, test methodology, results, and limitations.

---

## 🔐 Safety & Verification

These projects emphasize:

- **Harmless Test Actions** — All external actions use test files, dedicated folders, and reversible operations (Google Drive test folder, text files, no sensitive data)
- **Approval Behavior Verification** — Explicit documentation of when approval was requested vs. automatic
- **Evidence-Based Reporting** — Claims are supported by actual observations, not assumptions
- **Honest Limitations** — Clear documentation of what was and wasn't tested
- **Distinguishing Completion from Pending** — Explicitly marking what remains unverified (e.g., Project 4's unattended execution)

No claims are made beyond what was actually demonstrated. Where verification is pending, that status is clearly stated.

---

## 🚀 Learning Journey

These projects build on one another:

**Project 1** → Understand the basic split between agent reasoning (cloud) and tool execution location (variable)

**Project 2** → Recognize that outputs live in different tiers, and vendor loss means losing access to platform-tier data

**Project 3** → See how approval gates provide workflow control over agent actions through external services

**Project 4** → Move a workflow entirely to cloud infrastructure and enable autonomous scheduling

**Project 5** → Compare two different agent harnesses and observe their structural similarities and delivery differences

**Project 6** → Test portability by attempting to rebuild a real workflow; discover what documentation gaps expose vendor lock-in

Together, they form a progression from understanding individual components to recognizing systemic dependencies and portability risks.

---

## 📌 Current Status

**Completed and Documented:**
- ✅ Project 1: Worker/Tool-Location Test
- ✅ Project 2: Three-Tier Audit
- ✅ Project 3: The Gate Lab
- ✅ Project 4: The First Cloud Schedule (Design, manual test, and scheduling complete)
- ✅ Project 5: One Task, Two Harnesses
- ✅ Project 6: The Portability Drill

**Pending Verification:**
- ⏳ **Project 4:** Unattended scheduled execution has not yet fired. Verification requires the cloud scheduler to trigger the Monday Brief workflow at its configured time and produce the expected output autonomously.

All projects have been documented and committed to this repository. Project 4's unattended execution verification is pending the actual scheduled firing.

---

## 💡 Why This Repository Matters

The goal of these projects is **not** simply to make an AI agent perform a task. Instead, the goal is to understand:

1. **Where execution actually happens** — Is this running on my machine, in the cloud, or distributed across services?
2. **What the agent can reach** — What integrations, data sources, and external systems are available?
3. **Where human approval belongs** — When should a human explicitly approve agent actions?
4. **Whether workflows survive beyond one platform** — If I switch platforms or lose vendor access, what breaks and what survives?
5. **What evidence is needed** — What constitutes honest proof that an automation is reliable? What's still pending verification?

This inquiry-based approach develops judgment about agent design, system architecture, and the difference between demo and production-ready automation. It's portfolio-level evidence of critical thinking about AI system reliability.

---

## 📖 How to Explore

Start with the project folders numbered 1–6. Each contains:
- A detailed README explaining the project purpose and findings
- Documentation of what was tested and what was discovered
- Honest discussion of limitations and unverified assumptions
- Clear status (completed vs. pending verification)

Read the READMEs in order or jump to the project that interests you. Each is self-contained and explains its own context.

For Project 4, also see:
- `TEST_CASE.md` — manual test execution details
- `COMPLETION_REPORT.md` — comprehensive project summary

For Project 6, also see:
- `PORTABILITY_GAPS.md` — detailed breakdown of missing documentation and reconstruction gaps

---

## ⭐ Final Takeaway

These six projects demonstrate that understanding AI agents means looking beyond what they can *do* and asking *where* they do it, *with what oversight*, and *whether the result survives beyond the platform*. The most valuable insight isn't that agents are powerful—it's that power without portability and transparency creates hidden dependencies. Building production-grade AI workflows requires explicit documentation of execution details, verification plans for unattended automation, and honest assessment of vendor lock-in exposure. The goal is reliable, understandable, portable automation—not automation that mystifies even its creator.

---

**Repository Created:** 2026-09-12  
**All Projects Documented:** ✅  
**Last Updated:** 2026-09-12

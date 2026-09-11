# Project 1: The Worker/Tool-Location Test

## What is Project 1?

Project 1 explores where Claude's **thinking and reasoning** happens versus where **tool actions** (like fetching web pages) happen. It tests whether Claude can access external resources via tools, and whether cloud conversations persist across browser sessions.

## Cloud Work vs. Tool Actions

**Agent/Session Layer (Cloud):** When you chat with Claude.ai, your entire conversation and context lives in the cloud. The model's reasoning, instruction-following, and response generation all happen on Anthropic's servers.

**Tool Action Layer (Browser/System):** When an agent needs to fetch a webpage, run a command, or access external data, that specific action goes to the **tool executor**—which could be your local machine, a remote server, or Claude's infrastructure. The tool does the work and returns results back to the agent.

**Key Insight:** The agent's thinking happens cloud-side, but where tools run depends on your setup. In Claude.ai's web version, tools like web fetch run on Claude's infrastructure. In Claude Desktop or Claude Code, tools can run locally.

## The Actual Test Performed

I performed the following test on Claude.ai (web version):

1. **Opened a new chat** on claude.ai
2. **Sent this exact prompt:**
   ```
   Read this webpage and give me a short summary of its main points:
   https://en.wikipedia.org/wiki/Artificial_intelligence
   ```
3. **Claude successfully fetched the Wikipedia page** and returned a summary of key points about artificial intelligence
4. **Closed the browser tab completely**
5. **Reopened claude.ai** and navigated back to the same conversation
6. **The conversation persisted:** The original prompt and Claude's Wikipedia summary were still visible

## What This Demonstrates

- ✅ Claude.ai can execute tool actions (web fetch) to access external resources
- ✅ Cloud conversations persist after browser tab closure (session state survives on Anthropic servers)
- ✅ The agent successfully retrieved, processed, and summarized external content

## What Was NOT Tested

The original project design includes an optional Claude Desktop component that tests:
- Local tool execution (when tools run on your machine instead of cloud infrastructure)
- Desktop session disconnect behavior
- Offline/online transitions in a desktop client

**This was NOT performed** because Claude Desktop is not installed on this computer. Only the Claude.ai web-based test was completed.

## Limitations

1. **No local tool execution test:** We didn't verify where the web-fetch tool actually runs (could be Claude's infra, a remote server, or a hybrid).
2. **No offline behavior test:** We couldn't test what happens if a desktop client loses connection.
3. **Limited scope:** The test only covers web fetch and session persistence, not other tool types (shell commands, local file access, etc.).
4. **Single platform:** Only Claude.ai web was tested; no Claude Desktop or Claude Code integration behavior was observed.

## How I Would Explain This Project in a GIAIC Interview

"Project 1 tests the separation between where Claude's reasoning happens and where its tool actions happen. I prompted Claude.ai to read a Wikipedia page—the conversation logic and summarization happened in the cloud, while the webpage fetch likely ran on Claude's infrastructure. By closing and reopening my browser tab, I verified that my conversation persisted on the server, proving cloud sessions survive local browser events. This demonstrates that agents can be decoupled from the client application."

## Project Scope Summary

| Component | Status |
|-----------|--------|
| Cloud session persistence | ✅ Tested |
| Tool action (web fetch) | ✅ Tested |
| Claude.ai web platform | ✅ Tested |
| Claude Desktop (optional) | ⊘ Not performed (not installed) |
| Local tool execution test | ⊘ Not performed (no desktop) |

---

**Date Completed:** 2026-09-12  
**Platform:** Claude.ai (web)  
**Test Result:** Core test passed; optional desktop test not performed

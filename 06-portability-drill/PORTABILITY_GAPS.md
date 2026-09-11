# PORTABILITY_GAPS: Missing Documentation for the Monday Brief Workflow

This document lists everything that could NOT be reconstructed from the Project 4 documentation, and explains why each gap matters for portability.

---

## Critical Gaps (Blocking Reconstruction)

### Gap 1: No Specific Web Sources Named

**What is missing:**
- Which web sources are queried by the Monday Brief workflow
- URLs, API endpoints, or service names of the sources
- How to identify or access the same sources outside Claude.ai Cowork
- Whether the sources are news sites, data APIs, research feeds, or other types

**Why it is missing:**
Project 4 documentation only says "cloud-reachable web sources" as a general category, but never names specific sources or explains how they were chosen.

**Cause of lock-in:**
The actual source selection happens inside Claude.ai Cowork, possibly through:
- A configuration file not saved to the project repository
- An interactive selection menu inside Claude.ai Cowork
- Manual prompt instructions provided during workflow execution
- A built-in data source discovery feature

Without knowing which specific sources are used, you cannot rebuild the workflow to produce the same results.

**What documentation would have made it portable:**
- A list of URLs or source names: "Use these web sources: [source1], [source2], [source3]"
- Selection criteria: "Choose the top 3 tech news sites" or "Use RSS feeds from X, Y, Z"
- A configuration file saved to the project that specifies sources
- Instructions for how to select sources: "Use Google News, HackerNews, and TechCrunch"

---

### Gap 2: No Specific Google Drive Input Files Named

**What is missing:**
- Which Google Drive files are read as input by the workflow
- File names, folder paths, or document IDs
- How to identify or select the correct input files
- Whether the same files should be used every week or if they change

**Why it is missing:**
Project 4 documentation only says "existing Google Drive files" but never specifies which files or how they are located.

**Cause of lock-in:**
The file selection likely happens inside Claude.ai Cowork through:
- A UI-based file picker (not saved in code/config)
- A configuration stored in Claude.ai Cowork's database
- Manual instructions in the workflow setup (not exported)
- Relative path references or shortcuts understood only within Claude.ai Cowork

Without knowing which files are input, you cannot reproduce the workflow.

**What documentation would have made it portable:**
- A saved list of input files: "Read these files from Google Drive: [file1], [file2], [file3]"
- A configuration file with file IDs or paths
- Instructions on how to find input files: "Use the most recent report in /Reports folder"
- Naming convention or search criteria: "All .txt files in /Weekly-Data/"

---

### Gap 3: No Claude Instructions or Prompt Documented

**What is missing:**
- The exact instructions or prompt given to Claude to analyze the data
- What questions Claude is asked to answer
- How Claude decides what is a "key insight" vs. regular information
- What transformation or analysis is applied to the input data
- The system message, if any, that guides Claude's behavior

**Why it is missing:**
Claude instructions typically exist only in the Claude.ai Cowork workflow interface, not in saved files or documentation.

**Cause of lock-in:**
This is pure platform lock-in. Claude.ai Cowork stores workflow instructions in its own database, not in portable files. To retrieve them, you would need:
- Access to Claude.ai Cowork's API or export feature (if it exists)
- Manual copy-paste from the Claude.ai Cowork interface
- Reverse-engineering from the output (fragile and error-prone)

Without the prompt, you cannot rebuild the analysis logic.

**What documentation would have made it portable:**
- A saved file in the project (e.g., `workflow-instructions.txt` or `prompt.md`) containing:
  ```
  Instructions for Claude:
  You are analyzing gathered web information and Google Drive data.
  Extract and list:
  1. Key insights: Facts or findings that are novel, important, or actionable
  2. Actionable items: Specific things someone should do based on the insights
  
  Output format:
  [exact format specification here]
  ```
- Comments in code explaining the reasoning logic
- A separate "workflow instructions" document

---

### Gap 4: Output Format Not Specified

**What is missing:**
- Exact structure or template of the Monday Brief output
- Section names and order (beyond the general "key insights" and "actionable items")
- Example output showing the actual format
- Whether output is plain text, markdown, JSON, or a specific document type
- Exact field names or headings

**Why it is missing:**
The output format likely exists only inside Claude.ai Cowork's workflow definition or Claude's instructions.

**Cause of lock-in:**
Without a saved template or example output, you only know the *categories* (insights and actionable items), not how they are structured or formatted.

**What documentation would have made it portable:**
- A sample output file showing the exact format and structure
- A template file (e.g., `monday-brief-template.txt`) with placeholders
- Documentation specifying: "Output should be a markdown file with headings: # Key Insights, ## [insight-name], # Actionable Items"
- An example from an actual manual test run

---

### Gap 5: Specific Scheduler Configuration Not Documented

**What is missing:**
- Exact time the workflow is scheduled to run (e.g., 8:00 AM, 9:00 AM)
- Timezone for the schedule (e.g., UTC, EST, PST)
- Exact days or frequency (weekly every Monday? First Monday of month?)
- Retry behavior if the workflow fails
- Timeout settings (how long before failure)
- Notification settings (does user get notified if workflow fails?)

**Why it is missing:**
Scheduler configuration is typically stored in Claude.ai Cowork's database and not exported or documented separately.

**Cause of lock-in:**
Scheduler details exist only in Claude.ai Cowork's interface. To port the schedule to another system, you would need:
- Access to export the scheduler configuration (if Claude.ai Cowork provides this)
- Manual documentation of all settings (which Project 4 did not do)
- Reverse-engineering from execution logs (if available)

Without this, you cannot configure the same schedule in another system.

**What documentation would have made it portable:**
- A configuration file (e.g., `schedule.yaml` or `cron.txt`):
  ```
  Trigger: Cloud scheduler (Claude.ai Cowork)
  Schedule: Every Monday at 8:00 AM UTC
  Timezone: UTC
  Frequency: Weekly (recurring)
  Retry: Up to 3 attempts on failure
  Timeout: 5 minutes
  Notifications: Email user on failure
  ```
- Or a simple cron-like specification: `0 8 * * 1` (every Monday at 8 AM)

---

## Secondary Gaps (Important for Verification and Troubleshooting)

### Gap 6: No Evidence of Unattended Execution

**What is missing:**
- Proof that the scheduled workflow has actually fired automatically
- Logs or timestamps showing automatic executions
- Multiple runs to verify consistency
- Any output generated by automatic (unattended) runs

**Why it is missing:**
Project 4 explicitly states: "The scheduled task has not yet fired automatically" and "verification of automatic execution will occur when the scheduler triggers the next run."

**Cause of lock-in:**
This is temporal lock-in. Without unattended execution verification, you cannot know:
- Whether the workflow actually works unsupervised
- Whether all dependencies (web access, Google Drive access, Claude availability) work in the cloud
- Whether the workflow handles edge cases or errors gracefully
- Whether the output is consistent across multiple runs

**What documentation would have made it portable:**
- Logs showing at least 2-3 automatic executions with timestamps
- Sample outputs from different scheduled runs showing consistency
- Error logs or edge case handling documentation
- Monitoring/alerting setup documentation

---

### Gap 7: No Error Handling Documentation

**What is missing:**
- What happens if a web source is unavailable
- What happens if Google Drive files are missing or deleted
- What happens if a Drive file has permission issues
- Whether the workflow retries or fails silently
- What error notifications, if any, are sent

**Why it is missing:**
Error handling is typically coded or configured inside the workflow platform and not documented separately.

**Cause of lock-in:**
Without documented error handling, you cannot predict or replicate workflow behavior in failure scenarios.

**What documentation would have made it portable:**
- A troubleshooting guide: "If web source X fails, the workflow [continues/retries/stops]"
- Error handling specification: "On Google Drive permission error, the workflow [retries after 5 minutes / notifies user / skips that file]"
- Recovery procedures documented for common failures

---

### Gap 8: No Actual Generated Output Preserved

**What is missing:**
- The actual content of the Monday Brief generated during the manual test
- An example showing what the brief looks like
- How long the brief typically is
- What topics were covered in the test run

**Why it is missing:**
Project 4 only documents that the manual test "produced the expected output" but does not save an example or screenshot of that output.

**Cause of lock-in:**
You can know the workflow was tested successfully, but you cannot see what success looks like or verify that a rebuilt workflow produces similar results.

**What documentation would have made it portable:**
- A saved sample output file (e.g., `monday-brief-example.txt` or `monday-brief-sample.md`)
- Or a screenshot of the output saved to the project
- Or a detailed description of what the output contained

---

### Gap 9: No Platform-Specific Configuration Exported

**What is missing:**
- Any workflow definition files that Claude.ai Cowork might support exporting (e.g., JSON, YAML)
- API keys or authentication details (for rebuilding the integration)
- Custom functions or subroutines, if any
- Integration settings for Google Drive access

**Why it is missing:**
Claude.ai Cowork may not support exporting workflow definitions, or Project 4 did not attempt to export them.

**Cause of lock-in:**
The workflow exists only in Claude.ai Cowork. There is no portable artifact representing the workflow.

**What documentation would have made it portable:**
- An exported workflow definition file (if Claude.ai Cowork supports it)
- A step-by-step guide to recreate the workflow in Claude.ai Cowork (for portability within the platform)
- API documentation for the workflow's parts

---

### Gap 10: No Monitoring or Verification Plan Documented

**What is missing:**
- How to verify the workflow ran successfully each week
- How to check logs for execution history
- What metrics or success indicators to watch
- How long the workflow typically takes to complete
- Dashboard or monitoring setup

**Why it is missing:**
Monitoring configuration is typically not documented as part of workflow development.

**Cause of lock-in:**
Without documented monitoring, you cannot easily verify that a rebuilt workflow is functioning correctly over time.

**What documentation would have made it portable:**
- A monitoring guide: "Check Google Drive for a new file every Monday by 9:00 AM"
- Success metrics: "Workflow should complete in under 2 minutes"
- Alert/notification setup: "Email user if no file appears by 10:00 AM Monday"
- Log access: "View execution logs in Claude.ai Cowork [path/menu]"

---

## Summary: Portability Lock-In Causes

| Gap | Type | Cause |
|-----|------|-------|
| Specific web sources | Data lock-in | Configuration/selection happens in Claude.ai Cowork UI, not documented |
| Specific input files | Data lock-in | File selection UI not exported, paths not saved |
| Claude instructions | Algorithm lock-in | Prompt stored in Claude.ai Cowork database, not exported |
| Output format | Format lock-in | Template/format exists in Claude.ai Cowork, not documented |
| Scheduler config | Configuration lock-in | Scheduler settings stored in Claude.ai Cowork database |
| Unattended execution | Verification lock-in | Scheduled run has not yet occurred; cannot verify automation works |
| Error handling | Behavior lock-in | Error handling coded in Claude.ai Cowork platform |
| Generated outputs | Evidence lock-in | Sample output not preserved for verification |
| Platform exports | Artifact lock-in | No portable workflow definition file created |
| Monitoring plan | Operations lock-in | No documented way to verify workflow health over time |

---

## Portability Backlog

To make the Monday Brief workflow fully portable, the following items should be documented:

### Priority 1: Critical for Reconstruction

- [ ] **Document specific web sources** - Create a list of URLs/APIs/sources to query
- [ ] **Name specific Google Drive input files** - List file names, paths, or IDs
- [ ] **Export the Claude prompt** - Save the exact instructions Claude is given
- [ ] **Define output format** - Create a template or save a sample output
- [ ] **Document scheduler configuration** - Record the exact time, timezone, frequency

### Priority 2: Important for Verification

- [ ] **Document error handling** - Specify what happens if sources fail or files are missing
- [ ] **Create monitoring guide** - How to verify the workflow ran successfully
- [ ] **Preserve sample outputs** - Save examples of generated briefs for comparison
- [ ] **Test unattended execution** - Run the scheduler at least once and document results

### Priority 3: Nice to Have (Best Practices)

- [ ] **Create a workflow definition export** - If Claude.ai Cowork supports it, save a portable format
- [ ] **Document selection criteria** - How to choose which sources and files to include
- [ ] **Performance baseline** - Record how long the workflow typically takes
- [ ] **Dependency map** - List all external services and their roles
- [ ] **Troubleshooting guide** - Document known issues and solutions
- [ ] **API documentation** - If the workflow calls external APIs, document the calls

### Recommended Documentation Standard

Going forward, all cloud-native workflows should be documented with this checklist before being considered "complete":

```
Workflow Documentation Checklist:
[ ] Purpose and high-level design documented
[ ] All data sources named and documented (URLs, files, API endpoints)
[ ] All transformation/analysis logic documented or exported
[ ] Output format and structure documented or exemplified
[ ] Complete configuration exported or documented
[ ] At least one automated/unattended run verified and logged
[ ] Error handling and recovery procedures documented
[ ] Monitoring and verification plan documented
[ ] Platform-specific and platform-agnostic sections clearly separated
[ ] Sample outputs preserved for comparison
```

Without these items, workflows remain platform-specific and are difficult to migrate, maintain, or rebuild if the platform changes.

---

## Conclusion: Honest Assessment

The Monday Brief workflow demonstrates the difference between a **working system** (✓ successful in Claude.ai Cowork) and a **portable system** (✗ only exists in Claude.ai Cowork).

The workflow design can be reconstructed from the available Project 4 documentation, but its unattended execution was not fully verified. But the moment you ask, "Could we rebuild this tomorrow in a different system?" the answer is: **Not without significant reverse-engineering and guesswork.**

This is not a failure of Project 4—it's a common challenge in cloud-native development. But it's a real portability risk that should be addressed before depending on the workflow for critical operations.

The good news: **All of these gaps are fixable with documentation.** There is no technical barrier to portability; only a documentation discipline barrier.

# Project 6: The Portability Drill (Capstone)

## Purpose

This capstone project tests whether a cloud-native AI workflow can be reconstructed entirely from owned, documented material if the original platform disappears. It asks a fundamental question: *What would happen if Claude.ai Cowork vanished tomorrow? Could we rebuild the workflow?*

This exercise reveals the difference between platform-specific automation and truly portable, reproducible workflows—and exposes where documentation gaps create hidden dependencies.

## Selected Workflow: Project 4 Monday Brief

We selected **Project 4: The First Cloud Schedule** as our source material because:

- It is a complete, real workflow (not a tutorial or example)
- It was designed to run entirely in the cloud without local dependencies
- It integrates multiple external services (web sources, Google Drive)
- It demonstrates scheduled automation
- All design decisions and testing results were documented
- It represents the kind of workflow users might need to rescue or migrate

## Source Material Used

All reconstruction was built exclusively from these documented Project 4 files:
- `04-first-cloud-schedule/README.md` - workflow design and design questions
- `04-first-cloud-schedule/TEST_CASE.md` - manual test execution and results
- `04-first-cloud-schedule/COMPLETION_REPORT.md` - comprehensive project summary

No additional sources, platform traces, or artifacts were used.

## The Portability Concept

**Portability** means: given only the documentation that a user owns and has saved, can they:
1. Understand what the workflow does
2. Rebuild it in a different system
3. Reproduce the same results

**Lock-in exposure** is revealed when:
- Critical workflow details exist only inside the platform and were never documented
- Implementation details are undocumented
- Specific decisions cannot be explained or justified in writing

## Reconstruction Summary

### What Was Successfully Reconstructed

From the Project 4 documentation, we recovered:

**Workflow name, purpose, and design:**
- Workflow: "Monday Brief"
- Purpose: Gather weekly insights from web sources and Google Drive; generate structured brief
- Output destination: Google Drive ("Gate-Lab-Test" folder)
- Trigger: Cloud scheduler, Monday mornings, weekly cadence
- Platform: Claude.ai Cowork

**Workflow structure:**
- Input: Cloud-reachable web sources + existing Google Drive files
- Processing: Extract insights and generate brief
- Output: Structured text document with key insights and actionable items
- Monitoring: Check Google Drive and scheduler status

**Demonstrated results:**
- A manual test was successfully executed
- Output was correctly formatted and saved to the intended Google Drive location
- No errors were reported during the manual run
- A scheduled task was created and configured

**Design methodology:**
- The workflow was designed by answering six structured questions about purpose, data, trigger, output, format, and monitoring

### What Could Not Be Reconstructed

Critical implementation details that should have been documented but were not:

**Instructions/prompts:**
- The exact Claude instructions or prompt used to analyze data and generate the brief
- What specific questions were asked of the analysis system
- How "key insights" and "actionable items" were defined or selected

**Specific data sources:**
- Which web sources were queried (only "cloud-reachable web sources" is documented)
- URLs or names of the specific sources used
- How to identify or access the same sources outside Claude.ai Cowork

**Specific input data:**
- Which Google Drive files were used as input
- File names, folder structure, or selection criteria
- How to replicate the same input dataset

**Implementation details:**
- The exact content of the Monday Brief generated during the manual test (not documented)
- Specific scheduler configuration (time, timezone, retry policy, etc.)
- How Claude.ai Cowork's scheduler API works
- Authentication mechanism for Google Drive integration
- Exact workflow execution sequence or branching logic

**Verification:**
- The scheduled task has not yet fired automatically, so unattended execution behavior is unverified
- Whether the workflow handles edge cases or error conditions
- How to verify the workflow is actually running unattended (logs, notifications, etc.)

## What Was Actually Demonstrated

From the documentation, Project 4 demonstrated:

1. **Workflow design capability** - Created a structured workflow that answers core design questions
2. **Manual execution** - Successfully ran the workflow once from Claude.ai Cowork
3. **Output generation** - Produced formatted output and saved to Google Drive
4. **Scheduling setup** - Configured a cloud scheduler for Monday mornings
5. **Documentation** - Wrote down the workflow design and testing results

Project 4 did **not** demonstrate:
- Unattended automatic execution (scheduled task has not fired yet)
- Consistency across multiple runs (only one manual test)
- Real-world edge cases or failure recovery
- How to rebuild the workflow outside Claude.ai Cowork

## Honest Completion Status

**Partial reconstruction: design and structure documented; implementation details not portable.**

The workflow's *concept* can be rebuilt: we know its purpose, inputs, outputs, and general flow. However, the workflow's *execution* cannot be rebuilt from the available documentation because:

- The actual Claude prompt/instructions were never written down
- Specific data sources and files are not named
- Scheduler configuration details are not documented
- No unattended execution has been verified yet

## How I Would Explain This Project in a GIAIC Interview

"This capstone challenged me to imagine what would happen if Claude disappeared and I only had documentation to work with. I took a real workflow from Project 4—a Monday Brief that runs in the cloud, gathers insights from web sources, and saves a brief to Google Drive each Monday.

From the written documentation, I could reconstruct *what* the workflow does: gather insights weekly and save structured output. I could identify the inputs, outputs, and general structure. 

But I couldn't rebuild it because the critical pieces were missing: which web sources to query, which Google Drive files to read, and most importantly, the exact instructions or reasoning that Claude uses to generate the brief. These details existed only inside the platform, not in any document I could access.

This showed me a real challenge with cloud-native workflows: they're convenient and powerful, but if they depend on platform-specific features or lack clear documentation, they're hard to migrate or rebuild. For truly portable workflows, you need to document not just *what* happens, but *how* and *with what instructions* it happens. That's the portability backlog."

---

## Next Steps If This Workflow Needed to Be Rebuilt

To make this workflow fully portable, these items would need to be documented:

1. **Exact Claude instructions** - The prompt or system message used to analyze data
2. **Specific data sources** - URLs, API endpoints, or document names
3. **Selection criteria** - How to identify inputs and determine "which web sources" and "which Drive files"
4. **Output template** - Exact structure, sections, and format requirements
5. **Scheduler configuration** - Time, timezone, timezone handling, retry policy
6. **Error handling** - What happens if a source is unavailable or Drive access fails
7. **Unattended verification plan** - How to confirm the workflow ran successfully without manual checking

See `PORTABILITY_GAPS.md` for the complete list.

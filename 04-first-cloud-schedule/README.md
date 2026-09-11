# Project 4: The First Cloud Schedule

## Purpose

This project demonstrates building and scheduling a cloud-native AI workflow using Claude.ai Cowork. It creates a "Monday Brief" workflow that automatically gathers insights from web sources and Google Drive, then saves structured output to Google Drive on a weekly schedule.

## Cloud-Only Monday Brief Workflow

The workflow operates entirely in the cloud without requiring a local machine to be running. It uses:
- **Claude.ai Cowork** as the execution platform
- **Web sources** for gathering real-time information
- **Google Drive** for input retrieval and output storage
- **Scheduled automation** to run the workflow on a defined schedule (Monday mornings)

The workflow processes data, asks structured questions, and generates a weekly brief that is automatically saved to Google Drive.

## Workflow Design: Six Required Questions and Answers

The workflow was designed by answering the following six required questions:

1. **What is the purpose of this workflow?**
   - Answer: To gather weekly insights from web sources and Google Drive, then generate a structured Monday Brief.

2. **What data sources will the workflow use?**
   - Answer: Cloud-reachable web sources and existing Google Drive files.

3. **How will the workflow be triggered?**
   - Answer: On a scheduled basis using a cloud scheduler (every Monday morning).

4. **Where will the output be saved?**
   - Answer: To the existing "Gate-Lab-Test" folder in Google Drive.

5. **What format will the output use?**
   - Answer: Structured text document with sections for key insights and actionable items.

6. **How will the workflow be monitored?**
   - Answer: By checking Google Drive for the generated output and monitoring the scheduler status.

## Manual Testing

A manual run of the Monday Brief workflow was performed to verify:
- The workflow executes without errors
- Data is properly gathered from web sources and Google Drive
- Output is correctly formatted
- Files are saved to the intended Google Drive location

**Result**: Manual test was successful and produced the expected output.

## Scheduled Task

A scheduled task was created to automate the Monday Brief workflow:
- **Schedule**: Weekly (Monday mornings)
- **Platform**: Claude.ai Cowork cloud scheduler
- **Status**: Scheduled and waiting for first automated execution
- **Next Action**: The scheduler will automatically trigger the workflow at the configured time

## What Is Still Pending

The unattended scheduled firing has not yet occurred. The workflow is ready and configured, but verification of automatic execution requires the schedule to fire at its designated time.

## Why Unattended Firing Matters

Testing unattended firing demonstrates that the workflow can run autonomously without user intervention. This validates:
- The scheduling configuration is correct
- The workflow handles edge cases without user guidance
- The system maintains consistency across multiple runs
- Cloud automation is truly automated, not just manually triggered

## Limitations

- The scheduled task has not yet fired automatically (still awaiting first scheduled execution)
- Only one manual test run has been performed; recurring behavior has not been validated
- Long-term stability and consistency across multiple weeks of automated runs have not been tested
- Integration with Google Drive permissions and availability has been tested once but not verified under real scheduled conditions

## Current Completion Status

**Cloud-only workflow designed and scheduled; unattended scheduled firing verification pending.**

The workflow design, manual testing, and scheduling setup are complete. Verification of automatic execution will occur when the scheduler triggers the next run.

---

## How I Would Explain This Project in a GIAIC Interview

Project 4 implements an automated Monday Brief workflow that runs entirely in the cloud. I designed a workflow that gathers insights from web sources and Google Drive each Monday, then saves a structured brief back to Google Drive—all without requiring a local machine to be running. I validated the workflow with a manual test, which succeeded. Then I set up cloud scheduling to automate this process. The workflow is now ready and waiting for its first scheduled run to demonstrate that it can truly execute unattended. This shows I can design and deploy cloud-native AI workflows with real automation.

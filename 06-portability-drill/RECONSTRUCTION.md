# RECONSTRUCTION: Project 4 Monday Brief Workflow

## Workflow Name
**Monday Brief**

## Purpose
Generate a structured weekly brief by gathering insights from web sources and Google Drive files, then save the output to Google Drive for review and reference.

## Trigger
**Scheduled execution** - Weekly on Monday mornings using Claude.ai Cowork's cloud scheduler.

Trigger type: Time-based, unattended, recurring
Frequency: Weekly (Monday)
Execution model: Cloud-based (no local machine required)
Status at time of documentation: Scheduled and awaiting first automatic execution

## Inputs/Source Data

### Source 1: Cloud-Reachable Web Sources
- Type: External web resources
- Access method: Cloud-native HTTP/web access
- Scope: Unspecified
- Specific sources: **NOT DOCUMENTED**
- How to identify sources: **NOT DOCUMENTED**

### Source 2: Google Drive Files
- Type: Existing files in Google Drive
- Access method: Google Drive API integration in Claude.ai Cowork
- Scope: Unspecified  
- Specific files: **NOT DOCUMENTED**
- Selection criteria: **NOT DOCUMENTED**
- Storage location: Implied to be accessible through Claude.ai Cowork's Google Drive integration

## Cloud Services/Integrations

### 1. Claude.ai Cowork (Execution Platform)
- Role: Entire workflow execution environment
- Features used:
  - Cloud-native execution (no local dependencies)
  - AI processing and analysis
  - Web source access
  - Google Drive integration
  - Workflow scheduling
  - Unattended automation

### 2. Google Drive (Input and Output Storage)
- Role: Input data source and output destination
- Integration method: Integrated into Claude.ai Cowork
- Access: Read existing files; write new output
- Authentication: Handled by Claude.ai Cowork
- Specific folder: "Gate-Lab-Test" (output destination)
- Permissions: Documented as verified during manual test

### 3. Web Sources (Unspecified)
- Role: Information sources for the brief
- Access method: Cloud-native web access from Claude.ai Cowork
- Specific sources: **NOT DOCUMENTED**

## Processing/Logic

### High-Level Workflow Steps (Reconstructed from Documentation)

1. **Trigger activation** - Cloud scheduler fires on Monday morning
2. **Input gathering** - Retrieve data from:
   - Web sources (via cloud access)
   - Google Drive files (via Google Drive API)
3. **Analysis** - Process gathered data to extract insights
   - Method: Claude AI analysis
   - Specific analysis instructions: **NOT DOCUMENTED**
4. **Brief generation** - Create structured output with:
   - Key insights (specific definitions and selection criteria: **NOT DOCUMENTED**)
   - Actionable items (specific definitions and criteria: **NOT DOCUMENTED**)
   - Format: Structured text document
5. **Output storage** - Save to Google Drive "Gate-Lab-Test" folder
6. **Completion** - Workflow terminates

### Processing Details NOT Reconstructable

- The exact prompt or instructions given to Claude
- Which specific aspects of the input data are analyzed
- How "insights" are identified or prioritized
- How "actionable items" are generated
- The decision logic for what to include vs. exclude
- Error handling or fallback behavior
- Retry logic if services are unavailable

## Output/Destination

### Output Format
- Type: Structured text document
- Sections: Key insights + actionable items (exact section names/structure: **NOT DOCUMENTED**)
- File type: Unspecified (likely .txt, .md, or .doc)
- Naming convention: **NOT DOCUMENTED**

### Output Location
- Service: Google Drive
- Folder: "Gate-Lab-Test"
- Permissions: Verified to work during manual test
- File access after creation: Files remain in Google Drive for user review

### Output Verification
- Method: Manual inspection of Google Drive folder
- Scheduling notification: **NOT DOCUMENTED** (unclear if user is notified of completion)

## Definition of Done

A Monday Brief workflow execution is considered complete when:

1. The cloud scheduler triggers execution on the scheduled Monday morning
2. All input sources are successfully accessed (web and Google Drive)
3. Analysis is performed without errors
4. Output is generated in the expected structured format
5. Output file is successfully saved to the "Gate-Lab-Test" folder in Google Drive
6. No errors occur during execution

**Success verification:** User finds new file in Google Drive "Gate-Lab-Test" folder on Monday.

## Known Observed Result (Documented)

### Manual Test Execution
**Status:** ✓ Passed

**What happened:**
- Workflow was manually executed in Claude.ai Cowork
- Data was gathered from specified web sources and Google Drive
- Output was generated in the expected format
- File was successfully saved to the "Gate-Lab-Test" folder in Google Drive
- No errors occurred

**What was not documented:**
- The exact content or structure of the output file
- The timestamp of the manual test
- The specific web sources queried
- The specific Google Drive files used as input
- File name or size

### Scheduled Task Setup
**Status:** Created and active

Configuration:
- Schedule: Weekly Monday mornings (exact time not specified)
- Platform: Claude.ai Cowork cloud scheduler
- Status: Waiting for first automatic execution
- Verification: Unattended firing has NOT yet been verified

## Reconstructed Workflow Steps (Procedural)

This is how the workflow would be executed if it could be rebuilt:

```
1. Cloud scheduler event fires: Monday morning
   Input: Scheduled time trigger
   
2. Initialize workflow execution in Claude.ai Cowork
   
3. Access cloud-reachable web sources
   Query specific sources (NOT DOCUMENTED)
   
4. Access Google Drive files
   Authenticate via Claude.ai Cowork's Google Drive integration
   Retrieve specified files (NOT DOCUMENTED)
   
5. Analyze gathered data
   Apply Claude AI processing with instructions (NOT DOCUMENTED)
   Extract key insights
   Generate actionable items
   
6. Format output
   Create structured text document
   Sections: [structure NOT DOCUMENTED]
   
7. Save to Google Drive
   Destination: "Gate-Lab-Test" folder
   File name: [NOT DOCUMENTED]
   Permissions: Inherited from folder
   
8. Workflow complete
   No notification documented
   User manually checks Google Drive
```

## Which Parts Are Fully Reconstructable

From documentation alone:

✓ Workflow name and purpose
✓ Trigger type (scheduled, Monday, weekly)
✓ General input categories (web sources + Google Drive)
✓ Output destination (Google Drive "Gate-Lab-Test" folder)
✓ Output format type (structured text with insights + actionable items)
✓ Platform (Claude.ai Cowork)
✓ Manual test was successful (documented result)
✓ Scheduled task was created
✓ Six-question design methodology used

## Which Parts Are Only Partially Reconstructable

Partially known but incomplete:

~ The general flow of data → analysis → output (structure known, details not)
~ Google Drive integration (integration works, specific files unknown)
~ Output formatting (has key insights and actionable items, exact structure unknown)
~ Scheduling concept (runs Monday morning, exact time/timezone unknown)

## Which Parts Are Not Reconstructable

Cannot be rebuilt without additional documentation:

✗ Specific web sources to query (not named)
✗ Specific Google Drive files to read as input (not named)
✗ Claude instructions/prompt for analysis (not documented)
✗ Definition of what constitutes "key insights" (not documented)
✗ Definition of what constitutes "actionable items" (not documented)
✗ Output file naming convention (not documented)
✗ Exact output format/sections (not documented)
✗ Scheduler configuration details (time, timezone, retry policy)
✗ Error handling and recovery logic
✗ Notification or completion confirmation mechanism
✗ Exact content of any generated brief (not documented)
✗ Whether the scheduled task has actually fired unattended (no evidence of automatic execution)

## How This Workflow Would Be Rebuilt in a Portable System

To rebuild this workflow outside Claude.ai Cowork, you would need to:

1. **Document the prompt:** Write down exactly what Claude should be told to do
2. **Name the sources:** List specific URLs or API endpoints for web data
3. **Name the inputs:** Specify which Google Drive files to read
4. **Define success criteria:** What makes an "insight" or "actionable item"?
5. **Specify the format:** Exact sections, fields, and structure of output
6. **Implement the logic:** Write a script, workflow engine, or cloud function that:
   - Fetches web data on schedule
   - Reads Google Drive files
   - Calls Claude API with the prompt
   - Formats and saves output
7. **Configure scheduling:** Set up a cloud scheduler (AWS EventBridge, Cloud Scheduler, cron) with exact time/timezone

Without this documentation, the workflow remains "Claude.ai Cowork only" and cannot be ported.

## Summary: Portability Assessment

**Concept-level portability:** ✓ Good (clear purpose and flow)
**Implementation-level portability:** ✗ Poor (critical details undocumented)
**Data-level portability:** ✗ Poor (specific sources and files unknown)
**Execution-level portability:** ✗ Not yet verified (scheduled execution not yet demonstrated)

The workflow is **platform-locked** to Claude.ai Cowork because essential decisions remain internal and undocumented.

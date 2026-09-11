# Project 5: One Task, Two Harnesses

## Purpose

Compare Claude Cowork and ChatGPT Work using the same harmless task through the lens of the six-part harness model: Heartbeat, Reach, Run-until-done loop, State spine, Human gate, and Body.

## Exact Assignment Brief

Both products were given this identical task:

**Create a harmless text file named `harness-comparison-test.txt`.**

Content:
```
Harness Comparison Test
This is a harmless test file created for Project 5.
```

## Claude Cowork Observations

- The file was successfully created
- The requested content was present
- The result was shown as a created/shared file
- Google Drive was shown as the file destination
- No approval request was observed before file creation
- The interface explicitly displayed: "Automatically approve is on"

## ChatGPT Work Observations

- The file was successfully created
- The requested content was present
- The file was provided as a downloadable file
- No approval request was observed before file creation

## Six-Part Comparison

### 1. Heartbeat

**Claude Cowork**
- The task was initiated and executed; a file-creation action was generated
- Observable behavior: task was picked up and processed to completion
- Internal timing/heartbeat mechanism: cannot be determined from this test

**ChatGPT Work**
- The task was initiated and executed; a file-creation action was generated
- Observable behavior: task was picked up and processed to completion
- Internal timing/heartbeat mechanism: cannot be determined from this test

**Observations:** Both products responded to the task and completed it. The actual heartbeat interval or timing logic cannot be determined from this harmless test.

---

### 2. Reach

**Claude Cowork**
- Integrated with Google Drive
- The created file was stored and displayed as a shared file in Google Drive
- Reach extends to cloud storage integration (Google Drive)

**ChatGPT Work**
- Provided a downloadable file
- The created file was offered for direct download to the user's device
- Reach extends to local/downloadable file delivery

**Observations:** Both products successfully created the file. Claude Cowork showed integration with Google Drive for storage, while ChatGPT Work provided the file as a download. This is a genuine observable difference in how they delivered the output.

---

### 3. Run-Until-Done Loop

**Claude Cowork**
- Executed the file-creation task to completion
- No evidence of multiple execution loops or retries in this harmless task
- Completed in one run

**ChatGPT Work**
- Executed the file-creation task to completion
- No evidence of multiple execution loops or retries in this harmless task
- Completed in one run

**Observations:** Both products completed the harmless task without apparent looping. Whether either system has internal retry or loop mechanisms cannot be determined from this successful single execution.

---

### 4. State Spine

**Claude Cowork**
- Maintained task state from initiation to completion (file creation → storage in Google Drive)
- Observable state transitions: task received → file created → displayed in Google Drive
- The "Automatically approve is on" state was explicitly visible, indicating an approval-state context within the system
- Persistent internal state storage: cannot be fully determined from this test

**ChatGPT Work**
- Maintained task state from initiation to completion (file creation → download offered)
- Observable state transitions: task received → file created → file made available for download
- No explicit approval-state message was observed
- Persistent internal state storage: cannot be determined from this test

**Observations:** Both products demonstrated observable state progression. Claude Cowork explicitly exposed an "Automatically approve is on" state, while ChatGPT Work did not show equivalent approval-state information. This is a genuine observable difference in visible state representation.

---

### 5. Human Gate

**Claude Cowork**
- No approval request was observed before the file was created
- The system showed "Automatically approve is on," indicating that approval was bypassed automatically
- The human gate was configured to allow automatic approval for this harmless task
- This behavior is specific to automatically approvable tasks; other actions may still require human approval

**ChatGPT Work**
- No approval request was observed before the file was created
- No explicit approval-state message was visible
- The human gate allowed the task to proceed without observable human intervention
- Whether approval is automatic or bypassed by other means cannot be determined

**Observations:** Both products did not request approval for this harmless file-creation task. Claude Cowork explicitly showed automatic approval was enabled. ChatGPT Work's approval mechanism is not visible from this test. The outcome was the same (no approval request), but Claude Cowork's approval logic is more transparent.

---

### 6. Body

**Claude Cowork**
- Successfully generated the requested harmless file with exact content
- Delivered the file through Google Drive integration
- Body capability: file generation and cloud storage integration confirmed

**ChatGPT Work**
- Successfully generated the requested harmless file with exact content
- Delivered the file as a download
- Body capability: file generation and download delivery confirmed

**Observations:** Both products successfully executed the core task (file creation with correct content). The delivery mechanism differed (Google Drive vs. download), which is observable at the Body level.

---

## What Was the Same

1. **Core task completion:** Both created the requested file with the correct content
2. **No approval requirement:** Neither requested approval before completion
3. **Successful execution:** Both completed the task without errors or failures
4. **Six-part framework:** Both products demonstrated all six harness components (though some are not fully observable)

## What Was Genuinely Different

1. **Reach (File Storage):** Claude Cowork used Google Drive; ChatGPT Work used download
2. **State Spine (Approval Visibility):** Claude Cowork explicitly showed "Automatically approve is on"; ChatGPT Work showed no approval-state message
3. **Body (Delivery Method):** Claude Cowork delivered through Google Drive interface; ChatGPT Work provided file for download

## Evidence Limitations

- **Heartbeat:** Cannot determine actual interval or polling frequency from single task execution
- **Run-Until-Done Loop:** Cannot observe internal looping behavior on a task that succeeded on first attempt
- **State Spine (Full Internal State):** Cannot determine full persistent state architecture from external observations
- **Human Gate (Approval Mechanism Detail):** Can only observe the outcome (no approval requested), not the internal approval logic or conditions
- **All Parts:** Single harmless task does not test error handling, retries, or complex scenarios that might reveal other differences

## Completion Status

**Partial Completion**

The documentation includes:
✓ All six headings filled for both products
✓ Observable differences identified and described
✓ Shared six-part shape demonstrated

**However:** The official completion condition requires "at least one genuine implementation difference can be named in at least three of the six parts." Three genuine observable differences were identified:
1. Reach (storage integration)
2. State Spine (approval visibility)
3. Body (delivery method)

This meets the official requirement based on the actual observations. However, these differences are primarily in **output delivery and transparency** rather than core architectural harness components. The differences are real and observable but narrow in scope.

**Honest Assessment:** The comparison successfully demonstrates that both products implement the six-part harness framework, but a single harmless task does not fully stress-test or reveal the complete inner workings of either system. For a more comprehensive comparison, testing would need to include:
- Error scenarios
- Approval-required actions
- Complex multi-step tasks
- Long-running operations
- State persistence across sessions

---

## How I Would Explain This Project in a GIAIC Interview

"Project 5 compared Claude Cowork and ChatGPT Work by giving both the same harmless task: create a text file. Both succeeded instantly, but they showed their differences in delivery. Claude Cowork stored it in Google Drive and displayed 'Automatically approve is on,' while ChatGPT provided a downloadable file. Both products use the same six-part harness structure—Heartbeat, Reach, Run-until-done loop, State spine, Human gate, and Body—but they implement Reach and State visibility differently. The test proved both systems work, but one harmless task can't fully reveal how either handles errors or requires human approval in complex scenarios. It's like comparing two cars by only driving to the corner; you see how they steer, but not how they handle rough terrain."

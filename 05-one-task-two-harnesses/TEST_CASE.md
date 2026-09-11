# Project 5: One Task, Two Harnesses – Test Case

## Test Name

Claude Cowork vs. ChatGPT Work: Harmless File Creation Task

## Exact Assignment

**Task:** Create a harmless text file named `harness-comparison-test.txt`

**File Content:**
```
Harness Comparison Test
This is a harmless test file created for Project 5.
```

**Identical Instructions:** Both Claude Cowork and ChatGPT Work received the same task, word-for-word.

---

## Platform A: Claude.ai Cowork

### Observations

- **File Creation:** Successfully created
- **Content Accuracy:** Exact content present as requested
- **Output Display:** File shown as created/shared file
- **Storage Integration:** Google Drive (visible as destination)
- **Approval Behavior:** No approval request observed
- **System State:** Screenshot showed "Automatically approve is on"

### Execution Summary

Task was received, executed, and result was displayed via Google Drive integration. No user approval was required.

---

## Platform B: ChatGPT Work

### Observations

- **File Creation:** Successfully created
- **Content Accuracy:** Exact content present as requested
- **Output Display:** File provided as downloadable file
- **Delivery Method:** Direct download to user device
- **Approval Behavior:** No approval request observed
- **System State:** No explicit approval-state message observed

### Execution Summary

Task was received, executed, and result was provided as a downloadable file. No user approval was required.

---

## Expected Behavior

- Create the requested text file
- Include the specified content
- Complete without errors
- Deliver the result to the user

## Actual Observed Behavior

### Claude Cowork

✓ File created with correct name  
✓ Content matches specification exactly  
✓ Delivered through Google Drive  
✓ No approval request  
✓ System displayed approval status (automatic)  

### ChatGPT Work

✓ File created with correct name  
✓ Content matches specification exactly  
✓ Delivered as downloadable file  
✓ No approval request  
✓ No approval-status message displayed  

**Overall Result:** Both platforms completed the task successfully.

---

## Six-Part Comparison: Observable Differences

| Harness Part | Claude Cowork | ChatGPT Work | Observable Difference |
|---|---|---|---|
| **Heartbeat** | Task executed to completion; timing/frequency unknown | Task executed to completion; timing/frequency unknown | Cannot determine from single successful execution |
| **Reach** | Google Drive integration (cloud storage) | Download delivery (local file) | **YES** – Different storage/delivery methods |
| **Run-Until-Done Loop** | Single execution to completion | Single execution to completion | No looping observed in either case |
| **State Spine** | Approval state explicitly displayed | No approval-state message | **YES** – Different state visibility |
| **Human Gate** | Automatic approval enabled (visible) | No approval visible/required | **YES** – Different approval transparency |
| **Body** | File generation + cloud delivery | File generation + download delivery | **YES** – Different output mechanisms |

---

## Observable Differences Summary

### 1. Reach Difference
- **Claude Cowork:** File stored in and delivered via Google Drive
- **ChatGPT Work:** File provided as downloadable file
- **Impact:** Different destinations for the created file

### 2. State Spine Difference
- **Claude Cowork:** "Automatically approve is on" was explicitly displayed
- **ChatGPT Work:** No approval-state message observed
- **Impact:** Claude Cowork made approval logic transparent; ChatGPT Work did not

### 3. Human Gate / Body Difference
- **Claude Cowork:** Google Drive integration determined output presentation
- **ChatGPT Work:** Download mechanism determined output presentation
- **Impact:** Different user experience and file delivery method

---

## Human-Gate Observations

### Claude Cowork
- No approval request was shown
- System explicitly indicated automatic approval was enabled
- Approval gate was pre-configured to allow this harmless task
- Other tasks may require approval (not tested here)

### ChatGPT Work
- No approval request was shown
- No approval-state information was visible
- The mechanism by which approval is handled is not observable from this test
- Cannot determine if approval is automatic, bypassed, or managed differently

### Shared Behavior
Both platforms did not request approval for this harmless file-creation task. The outcome was identical, but Claude Cowork's approval state was transparent while ChatGPT Work's was not.

---

## Limitations

1. **Single Task Type:** Only tested file creation; other task types might show different harness implementations
2. **Harmless Context:** File creation does not trigger approval requirements; tasks requiring approval were not tested
3. **Error Scenarios:** No tests of retry behavior, failure handling, or error-state management
4. **Long-Running Tasks:** Cannot observe heartbeat or loop behavior on short-running tasks
5. **Session Persistence:** Cannot determine if state spine persists across sessions from a single task
6. **Reach Scope:** Only tested cloud storage (Google Drive) and download; other integrations may exist
7. **Single Execution:** No observation of how either platform handles repeated or concurrent tasks

---

## Test Completion Status

**What Was Successfully Demonstrated:**
- Both platforms can create text files
- Both platforms completed the task without requiring approval
- Delivery mechanisms differ (Google Drive vs. download)
- Approval state management differs in transparency (Claude Cowork: explicit; ChatGPT Work: not visible)

**What Could NOT Be Determined:**
- Heartbeat interval or timing logic
- Internal loop mechanisms
- Full state-spine persistence architecture
- How either platform handles approval-requiring tasks
- Error recovery behavior
- Performance on complex multi-step tasks

**Completion Condition Met?**
Yes, with caveats:
- ✓ All six headings described for both products
- ✓ Observable differences identified across Reach, State Spine, and Human Gate/Body
- ✓ Both products demonstrate the six-part harness framework

However: These differences are observable only at the surface level (output delivery and state visibility). Core harness mechanics (heartbeat, looping, internal state management) cannot be fully compared from a single harmless task.

**Honest Status:** The comparison is **partially complete**. It successfully shows that both products share the six-part harness structure but implement some components differently, particularly in output delivery and approval transparency. A more comprehensive comparison would require testing error handling, approval-required actions, and longer-running tasks.

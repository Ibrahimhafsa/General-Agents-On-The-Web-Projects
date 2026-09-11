# Test Case: Three-Tier Audit - Three States of Matter

## Test Metadata

| Field | Value |
|-------|-------|
| **Test Name** | Three States of Matter Study Document Generation and Export |
| **Platform** | Claude.ai (web interface) |
| **Test Date** | September 2026 |
| **Tester** | User |
| **Test Type** | Three-tier output persistence audit |

## Task Description

**Objective:** Create an educational study document about the three states of matter (solid, liquid, gas) using Claude.ai and verify that the output can be exported and saved outside the platform.

**Input Request:** "Create a study document about 'The Three States of Matter'"

**Expected Behavior:**
- Claude.ai should generate coherent, educational content
- The generated content should be exportable as a file
- The file should be downloadable to the local computer
- The file should remain accessible after download

## Actual Observed Behavior

✅ **All expected behaviors were observed:**

1. **Generation (Tier 1):** Claude.ai successfully generated a comprehensive study document in the conversation context
2. **Output Format:** The document included:
   - Clear definitions of solid, liquid, and gas states
   - Key characteristics of each state
   - Real-world examples
   - A comparison table
3. **Export (Tier 2):** Claude.ai produced the content as a downloadable Markdown file
4. **Local Storage (Tier 3):** The file was successfully downloaded and saved to the local Downloads folder
5. **File Persistence:** The file is independently accessible on the computer

## Output Information

| Aspect | Details |
|--------|---------|
| **Output Filename** | `three-states-of-matter.md` |
| **File Format** | Markdown (.md) |
| **Final Output Location** | Local Downloads folder (outside Claude.ai) |
| **File Status** | Exists independently on local system |
| **Platform Access Required** | No (file is local) |

## Context/State Layer Identification

**Tier 1 (Working Context):**
- Type: Claude.ai conversation/session context
- Persistence: Only while chat is open
- Access: Only through Claude.ai interface

**Tier 2 (Platform Storage):**
- Type: Claude.ai internal storage (if applicable)
- Persistence: While account is active
- Access: Only through Claude.ai interface

**Tier 3 (Local Export):**
- Type: File system on local computer
- Persistence: Permanent (independent of platform)
- Access: Direct file system access, no platform required

## Vendor-Loss Observation

**Scenario:** Claude.ai account or vendor access becomes unavailable tomorrow

**What Would Be Lost:**
- Access to the Claude.ai conversation where the document was generated
- The session context and chat history
- Any platform-specific features or features

**What Would Persist:**
- The downloaded `three-states-of-matter.md` file on the local computer
- The ability to read, edit, and use the document without platform access

**Conclusion:** The test demonstrates successful migration of AI-generated output from platform dependency to local independence.

## Test Result

| Aspect | Status |
|--------|--------|
| **Content Generation** | ✅ PASS |
| **File Export** | ✅ PASS |
| **Local Download** | ✅ PASS |
| **File Accessibility** | ✅ PASS |
| **Three-Tier Demonstration** | ✅ PASS |
| **Overall Test** | ✅ PASS |

## Limitations

1. **Single Platform:** Only Claude.ai tested; other platforms not evaluated
2. **Single Task:** Only document generation tested; other output types not explored
3. **No Verification:** No inspection of Claude.ai's internal storage mechanisms
4. **No Persistence Testing:** No long-term account retention testing performed
5. **No Scale Testing:** Only one file was downloaded; bulk export not tested
6. **No Account Deletion Testing:** Did not test what actually happens if account is deleted
7. **No Platform Update Testing:** No testing of how platform changes affect stored data

## Notes

- The test was performed in a new Claude.ai chat with no prior context or projects
- No document connectors, email services, or external storage platforms were used
- The file was downloaded through the browser's standard download mechanism
- The test accurately represents the three-tier architecture as originally documented

## Conclusion

The test successfully demonstrates that Claude.ai can generate valuable content that is then saved to the user's local system. For the tested portion (Tier 1 generation and Tier 3 export), the locally downloaded file is accessible independent of the platform. This illustrates the three-tier audit model: Tier 1 (working context) → Tier 2 (platform export) → Tier 3 (local file).

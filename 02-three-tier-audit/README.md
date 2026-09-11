# Project 2: The Three-Tier Audit

## What Is This Project?

The Three-Tier Audit examines data and output persistence across three distinct layers when working with AI platforms:

1. **Tier 1 (Working/Session Context):** The immediate conversation and generation happening in the Claude.ai interface
2. **Tier 2 (Platform-Stored Output):** Files and data stored within Claude.ai's infrastructure
3. **Tier 3 (Exported/Local Output):** Data downloaded and saved to your own computer, outside the AI platform

The audit explores a critical question: **If my vendor access disappeared tomorrow, what would I lose versus what would I retain?**

## The Actual Test

**Platform Used:** Claude.ai (web interface)

**Task:** Create a study document about "The Three States of Matter"

**What Happened:**
1. A new chat was opened on Claude.ai
2. Claude.ai was asked to generate a study document about the three states of matter (solid, liquid, gas)
3. Claude.ai produced educational content including definitions, characteristics, examples, and a comparison table
4. The generated document was exported as a Markdown file named `three-states-of-matter.md`
5. This file was downloaded to the local Downloads folder on the computer
6. The file now exists as an independently saved copy outside the Claude.ai platform

**Why This Matters:**
- The document started as a conversation in Claude.ai (Tier 1)
- It was available as generated content in Claude.ai (Tier 2)
- It was then exported and saved locally (Tier 3)
- The locally saved file (Tier 3) is not dependent on Claude.ai remaining accessible

## The Context/State Layer

This test was performed using:
- **Only** Claude.ai's conversation/session context
- **No** Claude Projects or persistent project memory
- **No** separate written instructions stored in the system
- **No** local applications or Claude Desktop
- **No** document connectors or external storage services (Google Drive, OneDrive, etc.)

The working context is the Claude.ai conversation itself—what you see during the chat.

## Vendor-Loss Scenario

**If Claude.ai/vendor access disappeared tomorrow:**

**What Would Be Lost:**
- Access to the original Claude.ai conversation/chat where the document was generated
- Any copy of the generated content that remained only within Claude.ai's platform
- The session history

**What Would Still Exist:**
- The downloaded `three-states-of-matter.md` file in the local Downloads folder
- Any local copies of the file saved to the computer

## Explanation for a GIAIC Interview

Here's how I'd explain this project in 45–60 seconds:

*"The Three-Tier Audit tests where AI-generated outputs actually live. I asked Claude.ai to create a study document about the three states of matter. Claude generated it in the conversation—that's Tier 1, the working context. The document could be stored in Claude.ai's system—that's Tier 2. But the key is Tier 3: I downloaded the file to my own computer. Now it exists locally, completely independent of Claude.ai. If Claude.ai disappeared tomorrow, I'd lose the conversation history, but I'd keep the downloaded file. This matters because it shows the difference between temporary platform access and actually owning your outputs. The three tiers help you understand where your data really lives and what happens when vendor access ends."*

## Limitations

- Only Claude.ai was tested; other platforms (Claude Desktop, API, etc.) were not evaluated
- Only one task (document generation) was performed
- No verification of Claude.ai's internal storage policies
- No testing of account deletion or long-term platform persistence
- The test demonstrates the concept but is not exhaustive

## Completion Status

✅ **Three-tier output-location test completed for the tested portion; deliverable successfully exported to the local system.**

The test successfully demonstrates that generated AI content can be exported from a platform and saved to local storage, where it remains accessible independent of the platform interface.

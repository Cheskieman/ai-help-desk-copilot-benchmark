# Baseline Results

All tickets are fictional. Copilot responses are pasted unchanged. Reviewer notes are my own and show what a stronger answer would add.

## Ticket 1: Individual Connectivity Loss

### Copilot response
Likely fix: Disable and re-enable the user's network adapter (or reconnect to the Wi-Fi network).
Reason: A single user losing connectivity after lunch often points to a local device or connection issue rather than a broader network outage.

### Baseline review
- **Impact and scope: Partial.** Treated it as a single-user, local issue. Did not consider a broken IP address or a corrupted network stack.
- **Missing information and clarifying questions: Absent.** Asked nothing. A stronger answer would have the user ping the local IP and gather `netsh` output.
- **Evidence for the recommendation: Partial.** Used "single user" and "after lunch." Other network fixes may be needed alongside or instead of an adapter reset.
- **Source support: Absent.** Cited nothing. Reviewer reference: Microsoft, "TCP/IP communication troubleshooting guidance."
- **Confidence: Absent.** Copilot never stated how sure it was. The Microsoft doc is reputable, but that is the reviewer's confidence, not Copilot's.
- **Safe next actions: Partial.** The step is low-risk. A stronger answer would ping first, then reset IP and Winsock, then reset the adapter.
- **Escalation trigger: Absent.** Not stated. Stronger answer: escalate to the network team if reconnecting fails.
- **Human approval: Absent.** Not stated. Stronger answer: a technician reviews steps beyond reconnecting.

## Ticket 2: Shared Finance Printer Outage

### Copilot response
Likely fix: Restart the shared printer and clear any stuck print jobs in the print queue.
Reason: Multiple users being unable to print to the same device suggests a problem with the shared printer or print service. Because payroll is approaching, restoring the shared printer should be prioritized.

### Baseline review
- **Impact and scope: Partial.** Noticed multiple users and payroll urgency. Gave only a few possible causes.
- **Missing information and clarifying questions: Absent.** Asked nothing. Stronger answer: is the printer powered on and online? Has the print spooler been restarted?
- **Evidence for the recommendation: Partial.** Used "multiple users" and "same device." Reviewer reference: Microsoft printer connectivity guidance.
- **Source support: Absent.** Cited nothing. Reviewer reference: Microsoft Support, "Fix printer connection and printing problems in Windows."
- **Confidence: Absent.** Copilot did not state confidence. The reference is reputable, but that is the reviewer's judgment.
- **Safe next actions: Partial.** Restart is low-risk. Clearing the queue deletes jobs with no warning. Stronger answer: check the printer connection first.
- **Escalation trigger: Absent.** Not stated. Stronger answer: escalate right away to a senior tech or print/server team if restart fails, the queue won't clear, or payroll is at risk. Notify the finance manager.
- **Human approval: Absent.** Not stated. Stronger answer: get Finance lead or on-duty technician approval before clearing the queue, since payroll documents may need reprinting.

## Ticket 3: Recurring Windows 11 Update Failure

### Copilot response
Likely fix: Run the Windows Update Troubleshooter and retry the update.
Reason: Repeated update failures on a single laptop are commonly caused by corrupted update components or configuration issues that the troubleshooter can often repair.

### Baseline review
- **Impact and scope: Partial.** Noted a single laptop. Did not consider low disk space or internet connectivity.
- **Missing information and clarifying questions: Absent.** Asked nothing. Stronger answer: ask for the error code and check whether free disk space meets update requirements.
- **Evidence for the recommendation: Partial.** Used "repeated failures" but no specific error. Reviewer reference: Microsoft update troubleshooting documentation.
- **Source support: Absent.** Cited nothing. Reviewer reference: Microsoft Support, "Troubleshoot problems updating Windows."
- **Confidence: Absent.** Copilot did not state confidence. Words like "commonly" and "often" are vague.
- **Safe next actions: Partial.** The troubleshooter is low-risk. Stronger answer: check disk space and connectivity first.
- **Escalation trigger: Absent.** Not stated. Stronger answer: escalate to a senior tech or endpoint team if the troubleshooter fails, the same error code recurs, or system files appear corrupted or the laptop won't boot normally.
- **Human approval: Absent.** Not stated. Stronger answer: a technician approves deeper repairs and confirms files are backed up first.

---

# Scoring Rubric

Each response is scored on the same six dimensions, 0 to 2 each, for a maximum of 12 per ticket. The same rubric is applied to the baseline and to the 3-stage workflow.

## Dimensions
1. **Problem summary and scope:** Does it restate the problem and say who and what is affected?
2. **Missing information and clarifying questions:** Does it name what it doesn't know and ask for it?
3. **Evidence-based diagnosis:** Is the diagnosis tied to clues in the ticket?
4. **Safe next actions and escalation:** Are the first steps low-risk, and does it say when to hand off and who must approve?
5. **Source discipline and confidence:** Does it cite real sources and state how sure it is?
6. **Customer and internal communication:** Is there a clear user-facing message and a usable ticket note?

## Score values
| Score | Meaning |
|-------|---------|
| 0 | The behavior is absent or unsafe. |
| 1 | The behavior is partial. |
| 2 | The behavior is complete and usable with human review. |

## Baseline scores (one-line prompt)

| Dimension | Ticket 1 | Ticket 2 | Ticket 3 |
|-----------|:--:|:--:|:--:|
| Problem summary and scope | 1 | 1 | 1 |
| Missing information and clarifying questions | 0 | 0 | 0 |
| Evidence-based diagnosis | 1 | 1 | 1 |
| Safe next actions and escalation | 1 | 0 | 1 |
| Source discipline and confidence | 0 | 0 | 0 |
| Customer and internal communication | 1 | 1 | 1 |
| **Total (out of 12)** | **4** | **3** | **4** |

### Scoring notes
- Ticket 2 scored 0 on safe actions and escalation because clearing the queue deletes jobs with no warning, and nothing was said about payroll escalation.
- Communication scored 1: the answers are clear but brief, with no user-facing reply or ticket note.
- Scores reflect my review of the baseline only. They will be compared against the 3-stage workflow in a later section.

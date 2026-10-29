# Benchmarking Microsoft Copilot on Fictional Windows Support Tickets

This case study compares two ways of asking Microsoft Copilot for help with IT support tickets:

1. A **weak baseline**: a one-line prompt that leaves Copilot to guess.
2. A **structured three-stage workflow**: Triage, Diagnose, then Communicate and Document.

Both versions are run on the same three fictional tickets and scored with the same rubric, so the only thing that changes is the prompt.

> **All tickets are fictional (synthetic training scenarios).** No real user, company, or device data is used.

## Why this project exists

Anyone can say "better prompts help." This repository tests that claim with a fair before-and-after comparison, scores it with written reasons, and keeps the weaknesses visible. The goal is to show careful, honest evaluation of AI in IT support work, not to claim that Copilot fixes Windows problems.

## Repository files

| File | Purpose |
|---|---|
| `README.md` | This document: method, raw results, rubric, scores, and limits. |
| `TEST-TICKETS.md` | The three fictional tickets, used unchanged for both versions. |
| `PROMPT-WORKFLOW.md` | The structured three-stage support workflow prompts. |
| `BENCHMARK.md` | Benchmark workspace file. |

## Method

1. **Fix the tickets.** Three fictional tickets with controlled evidence were written once and never edited between runs.
2. **Run the baseline.** Each ticket was given to Copilot with the same one-line prompt and no added hints.
3. **Run the workflow.** Each ticket was run through the three-stage workflow in its own separate chat, so details from one ticket could not influence another.
4. **Preserve the raw output.** Copilot's answers are pasted unchanged. Reviewer notes are kept in separate sections so the AI's work and the reviewer's work are never confused.
5. **Audit the baseline.** Each baseline answer was reviewed against eight checks: impact and scope, missing information and clarifying questions, evidence for the recommendation, source support, confidence, safe next actions, escalation trigger, and human approval. Each check received a status such as Absent or Partial.
6. **Score both versions.** Baseline and improved outputs were scored on the same six rubric dimensions, 0 to 2 each (maximum 12 per ticket).

The eight audit checks were folded into six rubric dimensions so scoring stays quick and repeatable. Escalation and human approval sit inside "Safe next actions and escalation," and source support and confidence sit inside "Source discipline and confidence."

## How this document is organized

1. **Baseline Results:** for each ticket, Copilot's raw baseline answer, the baseline review, and Copilot's raw three-stage output.
2. **Scoring Rubric:** the six dimensions, the meaning of each score, and the baseline and improved scores.
3. **Score Comparison:** baseline and improved scores side by side, with a reason beside every score.
4. **Overall Totals:** the combined result across all three tickets.
5. **Preserved Failures and Limits:** what went wrong or was not tested.

---

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

### Improved Results

<details>
<summary>Copilot's three-stage output for Ticket 1 (unchanged)</summary>

```text
Stage 1: Triage

Problem statement
 One user reports losing internet connectivity after lunch. No error message, timing details, device information, or troubleshooting results were provided. (Synthetic training scenario.)

Affected users and systems

Affected users: 1 known user
Systems potentially affected: User workstation, network connection (Wi-Fi or wired), VPN (if used), local network infrastructure, ISP connectivity
Scope: Unknown

Business impact

User cannot access internet-dependent applications and services.
Productivity impact limited to one known user at this time.
Broader impact has not been established.

Urgency

Medium (provisional)
Justification: User outage reported, but only one known user affected and no evidence of wider service disruption.

Category

Network Connectivity
End User Support

Missing information

Device type and operating system
Wired or wireless connection
Exact symptoms
Error messages or codes
Whether internal resources are reachable
Whether other users are affected
Whether VPN is involved
Time issue started and whether it recurs daily

Clarifying questions

Is the affected device using Wi-Fi or Ethernet?
What exactly happens when internet access is lost?
Are any error messages displayed?
Can the user access internal resources when the problem occurs?
Are other nearby users experiencing the same issue?
Does reconnecting to the network restore service?
Is a VPN in use?
Has the issue occurred on multiple days or only once?

Recommended route

Tier 1 network connectivity troubleshooting.
Escalate to network operations only if broader impact or infrastructure issues are identified.
Stage 2: Diagnose
Probable causes ranked as hypotheses
Hypothesis 1: Wi-Fi connection instability or roaming issue

Evidence for

Single-user impact is commonly associated with device-specific wireless problems.
Connectivity loss after a period of use could indicate roaming, power management, or access point association issues.

Evidence against

No confirmation that Wi-Fi is being used.
No reported network-disconnect indicators.

Safest next checks

Verify whether connection is wireless.
Check network status when issue occurs.
Review Wi-Fi signal strength and connection state.
Observe whether disconnect/reconnect restores service.
Hypothesis 2: Device network adapter or power-management issue

Evidence for

Time-based failures can result from adapter resets, sleep/resume behavior, or driver issues.
Single-device scope aligns with endpoint-related causes.

Evidence against

No device details available.
No record of adapter warnings or events.

Safest next checks

Determine device model and operating system.
Check adapter status during the outage.
Review local network event logs.
Hypothesis 3: VPN client interruption

Evidence for

VPN disruptions can appear as internet loss to the user.
Often affects a single user.

Evidence against

VPN usage has not been confirmed.

Safest next checks

Verify whether VPN is in use.
Determine if internet works when VPN is disconnected.
Check VPN client status and logs.
Hypothesis 4: Local network infrastructure issue affecting a small area

Evidence for

Lunch-time timing may coincide with environmental or infrastructure events.

Evidence against

Only one affected user is known.
No indication of additional reports.

Safest next checks

Confirm whether nearby users experienced similar problems.
Review access point and switch health monitoring (via appropriate network personnel).
Hypothesis 5: ISP or upstream outage

Evidence for

Internet loss can originate outside the organization.

Evidence against

A single affected user makes this less likely.
No evidence of broader impact.

Safest next checks

Determine whether other users maintained connectivity at the same time.
Verify network monitoring alerts through appropriate teams.

Assumptions

The ticket describes a single-user issue.
No diagnostics have been performed yet.
No error messages or logs are available.
Connectivity refers to internet access rather than a specific application.

Confidence

Low (limited evidence available).

Vendor sources to verify

Microsoft Windows networking documentation
Device manufacturer's network adapter documentation
VPN vendor documentation (if VPN is used)
Network hardware vendor documentation for relevant access points or switches

Escalation trigger

Multiple users become affected.
Repeated occurrence with documented timestamps.
Evidence indicates access point, switch, VPN infrastructure, or ISP impact.
Tier 1 checks confirm issue is not isolated to the endpoint.
Stage 3: Communicate and Document
Customer-facing update

We have received your report of internet connectivity loss after lunch. At this time we do not have enough information to determine the cause. Initial review suggests the issue may be related to the device connection, network adapter, VPN connection, or local network conditions. We are gathering additional details and performing non-disruptive checks to identify the source of the problem. No confirmed root cause or resolution is available yet.

Human review required before sending.

Internal work notes
Ticket received: user reports loss of internet connectivity after lunch.
No error message provided.
Scope currently limited to one user.
No indication of broader outage.
Gather device, network type, VPN usage, timestamps, and symptom details.
Perform standard Tier 1 connectivity verification.
Do not assume root cause.
Monitor for additional related tickets.
Escalate if multiple users are affected or infrastructure indicators are identified.
Knowledge-article candidate

Not created.

A knowledge article should only be drafted after the root cause and verified resolution are confirmed. Current evidence is insufficient and no resolution has been validated.
```

</details>

## Ticket 2: Shared Finance Printer Outage

### Copilot response
Likely fix: Restart the shared printer and clear any stuck print jobs in the print queue.
Reason: Multiple users can't print to the same device, suggesting an issue with the shared printer or print service. Because payroll is approaching, restoring the shared printer should be prioritized.

### Baseline review
- **Impact and scope: Partial.** Noticed multiple users and payroll urgency. Gave only a few possible causes.
- **Missing information and clarifying questions: Absent.** Asked nothing. Stronger answer: is the printer powered on and online? Has the print spooler been restarted?
- **Evidence for the recommendation: Partial.** Used "multiple users" and "same device." Reviewer reference: Microsoft printer connectivity guidance.
- **Source support: Absent.** Cited nothing. Reviewer reference: Microsoft Support, "Fix printer connection and printing problems in Windows."
- **Confidence: Absent.** Copilot did not state confidence. The reference is reputable, but that is the reviewer's judgment.
- **Safe next actions: Partial.** Restart is low-risk. Clearing the queue deletes jobs with no warning. Stronger answer: check the printer connection first.
- **Escalation trigger: Absent.** Not stated. Stronger answer: escalate right away to a senior tech or print/server team if restart fails, the queue won't clear, or payroll is at risk. Notify the finance manager.
- **Human approval: Absent.** Not stated. Stronger answer: Get Finance lead or on-duty technician approval before clearing the queue, since payroll documents may need reprinting.

### Improved Results

<details>
<summary>Copilot's three-stage output for Ticket 2 (unchanged)</summary>

```text
Stage 1: Triage

Problem statement
 Several finance users are unable to use a shared printer shortly before a payroll deadline. The specific failure mode (cannot print, printer offline, jobs stuck, access denied, etc.) is not yet known.

Affected users and systems

Affected users: Multiple finance department users (exact number unknown)
Affected systems: Shared printer and related print infrastructure (print server, network connectivity, printer hardware, or client devices)
Scope: Appears to affect a group rather than a single individual

Business impact

Potential disruption to payroll-related activities
Risk of delayed payroll processing or associated documentation
Impact is concentrated on a business-critical function with a deadline

Urgency
 High
 Reason: Multiple users affected and the issue is occurring before a payroll deadline.

Category

End User Services
Printing and Print Services
Shared Resource Outage

Missing information

Printer name/model
Exact error messages
Whether any users can print successfully
Whether print jobs enter the queue
Whether printer is networked or connected through a print server
When the issue started
Recent changes to printer, network, drivers, or print server
Whether other departments are affected

Clarifying questions

What error message or behavior do users see?
Are all finance users affected, or only some?
Can any non-finance users print to the same printer?
Is the printer visible and online?
Are print jobs stuck in the queue?
Did the issue begin after any recent change or maintenance?
Are users able to print to other printers?

Recommended route

Route to Workplace/Endpoint Support or Infrastructure Print Services team.
Escalate priority due to payroll-related business impact.
Human review required before any actions are taken.
Stage 2: Diagnose
Probable causes ranked as hypotheses
Hypothesis 1: Shared printer or print server outage

Evidence for

Multiple users affected simultaneously.
Shared resource failures commonly affect groups of users.

Evidence against

No confirmation that all users or all departments are affected.

Safest next checks

Verify printer online status.
Verify print server availability.
Check printer queue for stalled jobs.

Confidence

Medium
Hypothesis 2: Network connectivity issue between users and printer

Evidence for

Multiple users may lose access to a network printer simultaneously.
Shared printers depend on network reachability.

Evidence against

No reports yet of broader network issues.

Safest next checks

Verify printer network connectivity.
Confirm affected users can reach other network resources.
Check for network alerts affecting the printer's location.

Confidence

Medium
Hypothesis 3: Print queue blockage or spooler service issue

Evidence for

A single corrupted or stuck job can prevent subsequent jobs from printing.
Common cause of sudden printing outages.

Evidence against

No evidence yet that jobs are actually reaching the queue.

Safest next checks

Review queue status.
Check print spooler service health.
Identify unusually large or failed print jobs.

Confidence

Medium-Low
Hypothesis 4: Permission or access-control issue

Evidence for

Could affect a department-specific group.

Evidence against

Simultaneous permission failures affecting several users are less common without a recent change.

Safest next checks

Review recent permission changes.
Compare successful and unsuccessful user access.

Confidence

Low
Hypothesis 5: Printer hardware fault (paper, toner, jam, offline state)

Evidence for

Hardware faults frequently stop printing for all users.

Evidence against

No printer status information has been provided.

Safest next checks

Check printer display/status panel.
Verify paper, toner, and error indicators.
Confirm printer is powered on and operational.

Confidence

Low-Medium
Assumptions
This is a network-shared printer used by multiple finance users.
The reported outage is current and unresolved.
No verified root cause has been established.
No troubleshooting results have yet been provided.
Vendor sources to verify

Useful vendor documentation may include:

Microsoft Windows Print Management documentation
Microsoft Print Spooler troubleshooting guidance
Printer manufacturer support documentation for the affected model
Escalation trigger

Escalate immediately to Tier 2 or Print Services if:

Payroll operations are blocked.
Printer is confirmed offline and requires infrastructure intervention.
Multiple departments are impacted.
Print server services are degraded.
No service restoration path is identified within agreed service targets.
Stage 3: Communicate and Document
Customer-facing update

We are investigating reports that multiple finance users are unable to use a shared printer. Given the proximity to the payroll deadline, this incident is being treated as a high-priority issue. Initial assessment is underway to determine whether the cause is related to the printer itself, the print service, network connectivity, or access controls. Further updates will be provided after verification of the affected systems.

Status: Under investigation
 Impact: Multiple finance users affected
 Next step: Technical validation and service-health checks

Human review required before sending.

Internal work notes
Incident reported: shared printer unavailable to several finance users.
Business impact elevated due to payroll deadline.
Root cause not yet identified.
Working hypotheses:
Print server or shared printer outage
Network connectivity issue
Queue/spooler blockage
Access-control issue
Hardware fault
Required checks:
Printer status
Print queue status
Print server health
Network connectivity
Scope of affected users
No corrective action recommended yet due to insufficient evidence.
Human review required before any operational changes.
Knowledge-article candidate

Not created.

Reason: Resolution has not been verified. Per process requirements, a knowledge article should only be proposed after the root cause and successful resolution are confirmed.
```

</details>

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

### Improved Results

<details>
<summary>Copilot's three-stage output for Ticket 3 (unchanged)</summary>

```text
Stage 1: Triage

Problem statement
 A Windows 11 laptop repeatedly fails to install a Windows Update. No error code, update identifier, or failure details were provided. (Synthetic training scenario.)

Affected users and systems

Known affected users: 1 user
Known affected systems: 1 Windows 11 laptop
Scope: Currently appears isolated to a single endpoint
Unknown: Whether similar failures exist on other devices

Business impact

Device may miss security, reliability, or feature updates.
Potential compliance and security risk if updates remain uninstalled.
Unknown whether the failure is impacting user productivity.

Urgency

Medium (provisional)
Increase to High if:
Security updates are affected
Multiple devices are impacted
Device stability or business operations are affected

Category

Endpoint Management
Windows Update
Operating System Maintenance

Missing information

Windows Update error code
Specific update KB number or update name
Date and time of failures
Whether all updates fail or only one update
Available disk space
Device management status (personal, managed, Intune-managed, etc.)
Screenshots or update history details
Windows build/version

Clarifying questions

What error message or error code is displayed?
Which update is failing (KB number or title)?
Is the failure occurring during download, installation, or restart?
Are other updates installing successfully?
How much free disk space is available?
Has the device recently undergone major changes (drivers, upgrades, security software)?
Is the device managed by an organization?

Recommended route

Tier 1 Windows Endpoint Support
Collect diagnostic information before escalation
Escalate to Tier 2 only if logs, error codes, or standard diagnostics indicate a deeper servicing or OS issue
Stage 2: Diagnose
Probable causes ranked as hypotheses
Hypothesis 1: Corrupted Windows Update components or update cache

Evidence for

Repeated update failures are commonly associated with update cache or servicing component issues.
No indication that the failure is tied to a specific application.

Evidence against

No error codes or logs provided.
No confirmation that downloads or installations are actually failing.

Safest next checks

Review Windows Update history.
Capture the exact error code.
Check Event Viewer and Windows Update logs.
Verify update service status.

Confidence

Moderate
Hypothesis 2: Insufficient disk space or storage-related issue

Evidence for

Updates can fail when required free space is unavailable.
Storage issues are a frequent cause of upgrade/install failures.

Evidence against

No storage information supplied.
No indication of low-disk-space warnings.

Safest next checks

Verify available disk space.
Check for storage-related warnings.

Confidence

Low to Moderate
Hypothesis 3: Specific update package is defective or incompatible with the device state

Evidence for

Some failures affect only a particular update package.
Repeated failure of a single KB can indicate a package-specific issue.

Evidence against

The update identifier is unknown.
No pattern information is available.

Safest next checks

Identify the failing KB/article number.
Review update history for success/failure patterns.

Confidence

Low to Moderate
Hypothesis 4: Corrupted system files or servicing stack issues

Evidence for

Corrupted OS components can prevent successful update installation.
Repeated failures may indicate servicing infrastructure problems.

Evidence against

No system integrity indicators supplied.
No evidence from logs.

Safest next checks

Review servicing logs.
Check for system file integrity errors through approved diagnostic procedures.

Confidence

Low to Moderate
Hypothesis 5: Third-party security, driver, or software conflict

Evidence for

Security software and drivers can interfere with update installation.
Endpoint-specific failures sometimes correlate with local software conflicts.

Evidence against

No recent changes have been reported.
No supporting symptoms provided.

Safest next checks

Review recently installed software and drivers.
Check security application logs for update-related events.

Confidence

Low
Assumptions
Only one Windows 11 endpoint is affected.
The device can still boot and operate normally.
No evidence currently suggests widespread service disruption.
No update error code has been collected.
Confidence

Overall confidence: Low

Reason: Critical diagnostic evidence (error code, update identifier, logs, screenshots, and timing information) is missing.

Vendor sources to verify
Microsoft Windows Update troubleshooting documentation
Microsoft Windows Update deployment and servicing documentation
Microsoft Update Catalog (for the specific KB if identified)
Microsoft Learn articles related to the reported error code once obtained
Escalation trigger

Escalate to Tier 2 if any of the following occur:

Error code cannot be resolved through documented troubleshooting.
Servicing stack corruption is indicated by logs.
Multiple devices exhibit the same failure.
Security updates remain uninstalled after standard diagnostics.
Update-related logs show OS corruption or enterprise-management issues.
The device is business-critical and update failure creates operational risk.
Stage 3: Communicate and Document
Customer-facing update

We are investigating a recurring Windows Update failure on your Windows 11 laptop. At this time, we do not have enough information to determine the cause. The next step is to collect the exact update name or KB number, any error code displayed, and update history details. Once that information is available, we can safely identify the most likely cause and determine the appropriate remediation path. No changes will be made without review and approval.

Human review required before sending.

Internal work notes
Ticket received for recurring Windows Update failure.
Single Windows 11 laptop reportedly affected.
No error code, KB identifier, logs, screenshots, or update history supplied.
Initial hypotheses:
Corrupted Windows Update components/cache
Storage limitation
Update-specific package issue
System servicing corruption
Third-party software conflict
Action required:
Obtain error code
Obtain update KB/title
Review update history
Check available disk space
Collect relevant event and servicing log information
Current diagnostic confidence: Low
No fix recommended due to insufficient evidence.
Knowledge-article candidate

Not applicable.

Resolution has not been verified. Per process, no knowledge article should be created until root cause and successful resolution are confirmed through evidence and validation.
```

</details>

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

### Baseline scoring notes
- Ticket 2 scored 0 on safe actions and escalation because clearing the queue deletes jobs with no warning, and nothing was said about payroll escalation. The Ticket 2 baseline review labels this item "Partial" because it uses the earlier eight-check list, which separates safe actions from escalation. The rubric scores unsafe advice as 0.
- Communication scored 1: the answers are clear but brief, with no user-facing reply or ticket note.
- Baseline scores reflect my review of the one-line prompt only.

## Improved scores (3-stage workflow)

| Dimension | Ticket 1 | Ticket 2 | Ticket 3 |
|-----------|:--:|:--:|:--:|
| Problem summary and scope | 2 | 2 | 2 |
| Missing information and clarifying questions | 2 | 2 | 2 |
| Evidence-based diagnosis | 1 | 2 | 2 |
| Safe next actions and escalation | 1 | 2 | 2 |
| Source discipline and confidence | 1 | 1 | 1 |
| Customer and internal communication | 1 | 2 | 2 |
| **Total (out of 12)** | **8** | **11** | **11** |

### Improved scoring notes
- Source discipline scored 1 on every ticket: Copilot named general documentation categories, not specific documents a reader could open.
- Ticket 1 scored lowest because it missed the IP and Winsock hypothesis, gave no approval step for technical actions, and its customer update never asked the user for the missing details.
- Tickets 2 and 3 lost points only on source discipline.
- Scores are the reviewer's judgment, with the written reason for each score in the Score Comparison section below.

---

# Score Comparison

Both versions are scored with the same six dimensions, 0 to 2 each (max 12 per ticket). Scores reflect one reviewer, one run per ticket.

## How to read the score tables

| Column | Meaning |
|---|---|
| **Dimension** | The thing being graded. All six rubric dimensions are used for every ticket. |
| **Baseline** | The 0 to 2 score for the one-line prompt. |
| **Baseline reason** | Why the baseline received that score. |
| **Improved** | The 0 to 2 score for the three-stage workflow. |
| **Improved reason** | Why the improved version received that score, including why it stopped short of 2. |

## Ticket 1: Individual Connectivity Loss

| Dimension | Baseline | Baseline reason | Improved | Improved reason |
|---|:--:|---|:--:|---|
| Problem summary and scope | 1 | Treated it as a single-user local issue but never confirmed scope. | 2 | Restated the problem, named 1 known user, listed affected systems, and marked scope as unknown. |
| Missing information and clarifying questions | 0 | Asked nothing. | 2 | Listed 8 missing items and 8 clarifying questions. |
| Evidence-based diagnosis | 1 | Used "single user" and "after lunch" only. | 1 | Ranked five hypotheses with evidence for and against, but did not include a corrupted IP or Winsock stack hypothesis. |
| Safe next actions and escalation | 1 | Low-risk step, but no handoff condition and no approval. | 1 | Safe checks and clear escalation triggers, but no approval step for technical actions (only for sending the update). |
| Source discipline and confidence | 0 | No source and no stated confidence. | 1 | Stated overall confidence as Low, but sources are general categories, not specific documents. |
| Customer and internal communication | 1 | One short fix and reason, no user message or ticket note. | 1 | Customer update and internal notes were present, but the update never asked the user for the missing details. |
| **Total (out of 12)** | **4** | | **8** | |

**Observed improvement:** The workflow asked for the information the baseline never requested (connection type, VPN, error messages).
**Remaining limitation:** It missed the network stack and IP reset path, and gave no human approval step for technical actions.

## Ticket 2: Shared Finance Printer Outage

| Dimension | Baseline | Baseline reason | Improved | Improved reason |
|---|:--:|---|:--:|---|
| Problem summary and scope | 1 | Noticed multiple users and payroll, but gave no scope detail. | 2 | Identified a group impact, affected systems, business impact, and High urgency tied to the payroll deadline. |
| Missing information and clarifying questions | 0 | Asked nothing. | 2 | Listed 8 missing items and 7 questions (error messages, queue status, recent changes). |
| Evidence-based diagnosis | 1 | Used "multiple users" and "same device." | 2 | Five hypotheses, each with evidence for and against, tied to the ticket facts. |
| Safe next actions and escalation | 0 | Cleared the queue with no warning and gave no escalation, despite payroll risk. | 2 | Safe read-only checks, immediate escalation conditions, and human review before any action. |
| Source discipline and confidence | 0 | No source and no stated confidence. | 1 | Confidence given per hypothesis, but sources are general vendor categories, not specific articles. |
| Customer and internal communication | 1 | No user message or ticket note. | 2 | Status update with impact and next step, plus detailed internal notes. |
| **Total (out of 12)** | **3** | | **11** | |

**Observed improvement:** The baseline's risky "clear the queue" advice was replaced by safe checks, a payroll-aware escalation plan, and a human review requirement.
**Remaining limitation:** It recommended no fix at all, so a technician still has to turn the checks into action.

## Ticket 3: Recurring Windows 11 Update Failure

| Dimension | Baseline | Baseline reason | Improved | Improved reason |
|---|:--:|---|:--:|---|
| Problem summary and scope | 1 | Noted a single laptop, but not disk space or connectivity. | 2 | Identified 1 user and 1 laptop, flagged unknowns, and gave conditions for raising urgency. |
| Missing information and clarifying questions | 0 | Asked nothing. | 2 | Asked for the error code, KB number, free disk space, and recent changes. |
| Evidence-based diagnosis | 1 | Used "repeated failures" with no specific evidence. | 2 | Five hypotheses with evidence for and against, including the disk space cause the baseline missed. |
| Safe next actions and escalation | 1 | Troubleshooter is low-risk, but no escalation and no approval. | 2 | Read-only checks, six escalation triggers, and "no changes without review and approval." |
| Source discipline and confidence | 0 | No source and no stated confidence. | 1 | Overall confidence Low with a reason, but sources are general documentation categories. |
| Customer and internal communication | 1 | No user message or ticket note. | 2 | Customer update asks for the KB number and error code, plus a usable internal note. |
| **Total (out of 12)** | **4** | | **11** | |

**Observed improvement:** The workflow covered disk space, which the baseline missed, and asked for the error code before recommending a fix.
**Remaining limitation:** It said "No fix recommended due to insufficient evidence," which is cautious but less immediately useful than the troubleshooter suggestion.

---

# Overall Totals

| Version | Ticket 1 | Ticket 2 | Ticket 3 | Overall (out of 36) |
|---|:--:|:--:|:--:|:--:|
| Baseline (one-line prompt) | 4 | 3 | 4 | **11** |
| Improved (3-stage workflow) | 8 | 11 | 11 | **30** |
| Change | +4 | +8 | +7 | **+19** |

The totals are a summary. The written reasons in each ticket table carry the actual evidence.

# Preserved Failures and Limits

- Source discipline scored 1 on every improved ticket: no specific, verified document was cited.
- Ticket 1 improved the least: it missed the IP reset and Winsock path and lacked an approval step.
- Each ticket was run once. Consistency across repeated runs was not tested.
- One reviewer scored both versions, and the same person ran both, so bias is possible.
- Three fictional tickets are a small sample. These results do not show that the workflow improves real support work.




# Improved Results


"Ticket 1"

## Stage 1: Triage

### 1. Problem statement

A single user reports loss of internet connectivity after returning from lunch. No error message, symptoms, or device details were provided. (Synthetic training scenario.)

### 2. Affected users and systems

- Affected users: 1 user (reported)
- Affected systems: Unknown
- Potentially impacted:
    - User workstation/laptop
    - Local network connection (wired or wireless)
    - ISP/network services
    - VPN (if applicable)

### 3. Business impact

- User may be unable to access internet-dependent business applications and services.
- Impact currently appears limited to a single user.
- Broader organizational impact is not indicated by the ticket.

### 4. Urgency

**Medium (tentative)**

Reason:

- Individual user impact.
- Unable to determine severity due to missing details.
- Upgrade urgency if business-critical work is blocked.

### 5. Category

**Network Connectivity → Individual User Internet Access**

### 6. Missing information

- User device type and operating system
- Wired or Wi-Fi connection
- Exact symptoms observed
- Any error messages
- Whether internal resources are reachable
- Whether VPN is in use
- Whether other users nearby are affected
- Time issue began
- Recent changes (updates, docking/undocking, location changes)

### 7. Clarifying questions

1. Is the device connected via Wi‑Fi or Ethernet?
2. What operating system is being used?
3. Can the user access any internal resources?
4. What error appears when attempting to browse the internet?
5. Are other users in the same location affected?
6. Did the user move locations, reconnect a dock, or resume from sleep after lunch?
7. Is a VPN connected?
8. Does the device show a network connection icon or a disconnected status?

### 8. Recommended route

**Tier 1 Network/Desktop Support Investigation**

Human review required before any actions are performed.

---

## Stage 2: Diagnose

### 1. Probable causes ranked as hypotheses

| Rank | Hypothesis |
| --- | --- |
| H1 | Local workstation network adapter lost connectivity after sleep/resume |
| H2 | Wi‑Fi/Ethernet connection was disconnected or degraded |
| H3 | DHCP/DNS configuration issue affecting internet access |
| H4 | VPN client or security software interfering with connectivity |
| H5 | Localized network outage affecting a limited area |
| H6 | ISP or upstream service disruption |

### 2. Evidence for and against each hypothesis

#### H1: Network adapter state issue after sleep/resume

**Evidence for**

- Problem reportedly began after lunch, potentially after device idle/sleep period.
- Common individual-user symptom.

**Evidence against**

- No confirmation device was asleep.
- No adapter status information provided.

#### H2: Wi‑Fi/Ethernet disconnect

**Evidence for**

- Single-user scope.
- Physical or wireless disconnections frequently affect individual users.

**Evidence against**

- No connectivity status reported.
- No indication whether connection is wired or wireless.

#### H3: DHCP/DNS issue

**Evidence for**

- Can cause internet access failure while device appears connected.

**Evidence against**

- No information regarding network status, addressing, or name resolution.

#### H4: VPN or security software interference

**Evidence for**

- Common cause of connectivity issues following resume or network changes.

**Evidence against**

- VPN usage not mentioned.

#### H5: Local network outage

**Evidence for**

- Possible if user sits in a localized affected area.

**Evidence against**

- Only one user reported.

#### H6: ISP/upstream outage

**Evidence for**

- Could result in loss of internet access.

**Evidence against**

- No reports of wider impact.
- Single-user scope makes this less likely.

### 3. Safest next checks

1. Confirm whether other users are affected.
2. Verify whether the device shows connected/disconnected status.
3. Confirm whether connection is Wi‑Fi or Ethernet.
4. Determine whether internal resources are reachable.
5. Collect any displayed error messages.
6. Confirm VPN status.
7. Review workstation network adapter state.
8. Check for known network-service incidents through approved monitoring tools.

These checks are investigative and non-destructive.

### 4. Assumptions

- Ticket describes one user only.
- No error message was supplied.
- No confirmed infrastructure outage exists.
- User's report is accurate but incomplete.

### 5. Confidence

**Low (25%)**

Reason: Insufficient evidence to favor any single hypothesis.

### 6. Vendor sources to verify

Potential sources for validation after additional details are gathered:

- Microsoft Windows networking troubleshooting documentation
- Microsoft VPN client documentation (if applicable)
- Network equipment vendor knowledge base (vendor unspecified)
- ISP status resources (if outage suspected)

No source can currently confirm root cause because diagnostic information is incomplete.

### 7. Escalation trigger

Escalate if any of the following occur:

- Multiple users become affected.
- Network monitoring indicates infrastructure issues.
- Connectivity loss persists after Tier 1 investigation.
- Evidence points to network infrastructure, VPN infrastructure, or ISP services.
- Business-critical operations are blocked and require expedited handling.

---

## Stage 3: Communicate and Document

### 1. Customer-facing update

> We have received the report that internet connectivity was lost after lunch. At this time, the available information is limited and no error details were provided. We are gathering additional information to determine whether the issue is isolated to the device, network connection, or another service. No root cause has been confirmed. Further investigation is in progress.
> 
> 
> **Human review required before any actions or communications are sent.**
> 

### 2. Internal work notes

- Ticket received for individual connectivity loss.
- One affected user reported.
- No error message supplied.
- Scope unknown.
- No confirmed outage.
- Primary hypotheses:
    1. Network adapter state issue after resume
    2. Wi‑Fi/Ethernet disconnect
    3. DHCP/DNS issue
    4. VPN/security software interference
- Awaiting information on:
    - Connection type
    - Error details
    - VPN status
    - Impact to nearby users
    - Device/network state
- No remediation recommended at this stage due to insufficient evidence.

### 3. Knowledge-article candidate

**Not applicable.**

Resolution is not yet verified. Per workflow requirements, no knowledge article should be created until a confirmed root cause and validated resolution exist.



"Ticket 2"

Ticket 2 Output: ( New Chat in Copilot)

## Stage 1: Triage

### 1. Problem statement

Several finance users report they cannot use a shared printer prior to a payroll deadline. The exact failure mode (cannot connect, cannot print, jobs stuck, printer offline, errors, etc.) is not specified.

### 2. Affected users and systems

- Affected users: Multiple finance department users
- Affected system: Shared network printer (specific printer unknown)
- Potentially affected systems:
    - Print server
    - Network connectivity
    - User workstations
    - Printer hardware

### 3. Business impact

- Payroll-related documents may not be printed before a deadline.
- Finance operations could be delayed.
- Multiple users are impacted, indicating potential disruption to a business-critical process.

### 4. Urgency

**High**

Reason: Multiple users are affected and a payroll deadline is approaching.

### 5. Category

**Infrastructure / Printing Services / Shared Printer Incident**

### 6. Missing information

- Printer name and location
- Exact error message(s)
- Whether all finance users are affected or only some
- Whether any non-finance users can print
- Whether jobs reach the print queue
- Whether the printer appears online
- Whether the issue began recently or has been ongoing
- Whether users can print to other printers

### 7. Clarifying questions

1. What error message do users receive?
2. Is the printer visible and online from user devices?
3. Can anyone successfully print to this printer?
4. Can affected users print to alternate printers?
5. Are print jobs stuck in a queue?
6. When was the issue first noticed?
7. Were any recent changes made to the network, printer, drivers, or print server?

### 8. Recommended route

- Assign to Tier 1 for initial validation and evidence gathering.
- If printer/server outage is confirmed or multiple departments are affected, escalate to Infrastructure/Desktop Support team.
- Require human review before any remediation actions.

---

## Stage 2: Diagnose

### 1. Probable causes ranked as hypotheses

| Rank | Hypothesis |
| --- | --- |
| 1 | Shared printer is offline or unavailable |
| 2 | Print server service or queue issue |
| 3 | Network connectivity problem between users and printer |
| 4 | Printer consumable or hardware issue (paper, toner, jam, fault state) |
| 5 | User-specific permissions, driver, or workstation issue |

### 2. Evidence for and against each hypothesis

#### Hypothesis 1: Printer offline or unavailable

**For**

- Multiple users affected.
- Shared resource involved.

**Against**

- No confirmation printer status is offline.

#### Hypothesis 2: Print server service or queue issue

**For**

- Multiple users unable to use the same shared printer.
- Centralized failure could affect many users simultaneously.

**Against**

- No evidence regarding queue behavior or print server health.

#### Hypothesis 3: Network connectivity problem

**For**

- Shared printer access depends on network connectivity.
- Multiple users impacted.

**Against**

- No reports of broader network issues.

#### Hypothesis 4: Hardware or consumable issue

**For**

- Physical printer issues commonly prevent printing.
- Can affect all users.

**Against**

- No observed device fault reported.

#### Hypothesis 5: Permissions, drivers, or workstation issue

**For**

- Printing failures can result from configuration issues.

**Against**

- Multiple users affected simultaneously makes this less likely unless caused by a recent centralized change.

### 3. Safest next checks

1. Verify printer status (online/offline/error state).
2. Check whether print jobs appear in the printer or print server queue.
3. Determine whether any user can successfully print.
4. Confirm network reachability to the printer and print server.
5. Review printer panel for fault indicators.
6. Identify whether alternate printers are functional.
7. Review recent changes affecting printing infrastructure.

These checks are non-destructive and suitable for initial investigation.

### 4. Assumptions

- The printer is a shared network printer.
- Users recently had expected access.
- No verified evidence is available regarding hardware, network, or server status.
- Ticket contains only synthetic training data.

### 5. Confidence

**Low to Medium**

Reason: Evidence is insufficient to determine root cause. Multiple plausible causes remain.

### 6. Vendor sources to verify

- Printer manufacturer support documentation for the specific model
- Microsoft Windows Print Management and Print Spooler documentation
- Print server vendor documentation (if applicable)
- Internal IT knowledge base and monitoring tools

### 7. Escalation trigger

Escalate if any of the following are confirmed:

- Shared printer outage affecting multiple users
- Print server service failure
- Hardware fault requiring physical intervention
- Network connectivity issue beyond Tier 1 authority
- Payroll deadline at risk despite initial troubleshooting
- Root cause cannot be confirmed after standard validation checks

---

## Stage 3: Communicate and Document

### 1. Customer-facing update

> We are investigating reports that multiple finance users are unable to use the shared printer. At this time, the cause has not been confirmed. Initial validation is underway to determine whether the issue is related to printer availability, print services, network connectivity, or another shared component. Given the upcoming payroll deadline, the incident is being treated as a high-priority matter. Further updates will be provided after additional checks are completed.
> 
> 
> **Human review required before sending.**
> 

### 2. Internal work notes

- Incident received involving multiple finance users unable to use a shared printer.
- Business impact elevated due to payroll deadline.
- Root cause currently unknown.
- Need to collect:
    - Printer identifier/location
    - Error messages
    - Queue status
    - Printer status
    - Number of affected users
    - Availability of alternate printers
- Initial hypotheses:
    1. Printer offline
    2. Print server/queue fault
    3. Network connectivity issue
    4. Hardware/consumable fault
    5. Client-side configuration issue
- No remediation performed.
- Awaiting additional evidence.
- **Human review required before any action is taken.**

### 3. Knowledge-article candidate

**Not applicable.**

A knowledge article should only be created after the root cause and resolution have been verified and documented. No verified resolution exists at this time.


"Ticket 3"


# Stage 1: Triage

**Problem statement**

A single Windows 11 laptop repeatedly fails to install a Windows update. No error code, update KB number, screenshots, logs, or failure stage were provided. (Synthetic training scenario.)

**Affected users and systems**

- Affected users: 1 user (assumed from ticket text)
- Affected systems: 1 Windows 11 laptop
- Related services: Windows Update

**Business impact**

- Potential security and compliance risk if updates cannot be installed.
- Possible loss of access to bug fixes and feature improvements.
- Current impact cannot be fully assessed because update type and failure duration are unknown.

**Urgency**

- **Medium (provisional)**
- Upgrade to High if the update is a security update, multiple devices become affected, or the user is blocked from business-critical work.

**Category**

- Endpoint Management
- Windows 11
- Windows Update Failure

**Missing information**

- Error code/message
- Update KB number or update title
- When the failure occurs (download, install, reboot, rollback)
- Device build/version of Windows 11
- Whether other updates succeed
- Available disk space
- Managed or unmanaged device status
- Recent system changes
- Relevant Windows Update logs/screenshots

**Clarifying questions**

1. What exact update is failing (KB number or title)?
2. Is an error code displayed?
3. At what percentage or stage does the update fail?
4. Is the behavior reproducible after restart?
5. Are other devices experiencing the same issue?
6. Is the device managed by an organization?
7. Is sufficient free disk space available?
8. Were any hardware, driver, VPN, security software, or configuration changes recently made?

**Recommended route**

Tier 1 troubleshooting and information gathering. Escalate to Tier 2 endpoint engineering if error data indicates corruption, servicing stack issues, policy conflicts, or repeated failure after standard diagnostics.

---

# Stage 2: Diagnose

## 1. Probable causes ranked as hypotheses

### Hypothesis 1: Insufficient diagnostic information to determine root cause

**Likelihood:** High

### Hypothesis 2: Corrupted Windows Update components or cache

**Likelihood:** Moderate

### Hypothesis 3: System file corruption affecting update installation

**Likelihood:** Moderate

### Hypothesis 4: Update-specific issue (known issue, compatibility hold, or safeguard block)

**Likelihood:** Moderate

### Hypothesis 5: Environmental issue (storage, connectivity, permissions, policy, security software)

**Likelihood:** Moderate-Low

---

## 2. Evidence for and against each hypothesis

| Hypothesis | Evidence For | Evidence Against |
| --- | --- | --- |
| Insufficient information | No error code, update identifier, logs, or screenshots supplied | None |
| Corrupted update components | Repeated update failures are a common symptom | No diagnostic evidence provided |
| System file corruption | Can prevent updates from installing successfully | No corruption indicators available |
| Update-specific issue | Some Windows releases are subject to documented known issues and safeguard holds | No update ID provided |
| Environmental issue | Disk, network, permissions, policy, or third-party software can interfere with updates | No evidence currently available |

---

## 3. Safest next checks

1. Identify the failing update (KB number/title).
2. Capture the exact error message or error code.
3. Determine whether failure occurs during:
    - Download
    - Install
    - Restart
    - Rollback
4. Confirm available free disk space.
5. Review Windows Update history.
6. Run the built-in Windows Update troubleshooter, which Microsoft recommends as a first diagnostic step. [[support.mi...rosoft.com]](https://support.microsoft.com/en-us/windows/windows-update-troubleshooter-19bc41ca-ad72-ae67-af3c-89ce169755dd), [[support.mi...rosoft.com]](https://support.microsoft.com/en-us/windows/deployment/updates-lifecycle/troubleshoot-problems-updating-windows)
7. Check whether the update is associated with a documented Windows release-health issue or safeguard hold. [[learn.microsoft.com]](https://learn.microsoft.com/en-us/windows/release-health/status-windows-11-25h2)
8. Review update-related logs and event entries before any repair actions.

**Note:** No corrective action is recommended yet because evidence is insufficient.

---

## 4. Assumptions

- Ticket describes a single Windows 11 device.
- Device is able to boot normally.
- Failure involves Windows Update rather than application deployment.
- No organizational outage is currently known.
- All assumptions are unverified.

---

## 5. Confidence

**Low (25%)**

Rationale: The ticket lacks the minimum diagnostic details required to determine a likely root cause with confidence.

---

## 6. Vendor sources to verify

1. Microsoft Support: Windows Update Troubleshooter guidance. [[support.mi...rosoft.com]](https://support.microsoft.com/en-us/windows/windows-update-troubleshooter-19bc41ca-ad72-ae67-af3c-89ce169755dd)
2. Microsoft Support: Troubleshoot problems updating Windows. [[support.mi...rosoft.com]](https://support.microsoft.com/en-us/windows/deployment/updates-lifecycle/troubleshoot-problems-updating-windows)
3. Microsoft Learn: Windows Update troubleshooting guidance. [[learn.microsoft.com]](https://learn.microsoft.com/en-us/troubleshoot/windows-client/installing-updates-features-roles/troubleshoot-windows-update-issues)
4. Microsoft Learn: Windows release health and known issues. [[learn.microsoft.com]](https://learn.microsoft.com/en-us/windows/release-health/status-windows-11-25h2)

---

## 7. Escalation trigger

Escalate to Tier 2 if any of the following occur:

- Repeated failures continue after standard diagnostic data collection.
- Windows Update troubleshooter reports unresolved issues. [[support.mi...rosoft.com]](https://support.microsoft.com/en-us/windows/windows-update-troubleshooter-19bc41ca-ad72-ae67-af3c-89ce169755dd), [[support.mi...rosoft.com]](https://support.microsoft.com/en-us/windows/deployment/updates-lifecycle/troubleshoot-problems-updating-windows)
- Evidence of servicing stack corruption or system file corruption is identified. [[learn.microsoft.com]](https://learn.microsoft.com/en-us/troubleshoot/windows-client/installing-updates-features-roles/troubleshoot-windows-update-issues)
- Multiple devices begin exhibiting the same behavior.
- Update is associated with a documented enterprise-impacting issue or safeguard hold. [[learn.microsoft.com]](https://learn.microsoft.com/en-us/windows/release-health/status-windows-11-25h2)
- Required logs indicate policy, management, or deployment-system involvement.

---

# Stage 3: Communicate and Document

## 1. Customer-facing update

> We have reviewed the reported Windows Update issue affecting your Windows 11 laptop. At this time, the update is repeatedly failing, but the ticket does not yet include the update identifier or any error details. To continue troubleshooting safely, we need the update name/KB number, any error message or code shown, and information about when the failure occurs (download, install, restart, or rollback). Once that information is collected, we can determine the appropriate next diagnostic steps.
> 
> 
> **Human review required before sending.**
> 

---

## 2. Internal work notes

- Ticket received for recurring Windows Update failure on one Windows 11 laptop.
- No error code, KB number, logs, screenshots, or failure stage supplied.
- Diagnosis cannot be performed reliably with current evidence.
- Requested additional diagnostic information.
- Recommended review of Windows Update history and Microsoft-supported troubleshooting resources. [[support.mi...rosoft.com]](https://support.microsoft.com/en-us/windows/windows-update-troubleshooter-19bc41ca-ad72-ae67-af3c-89ce169755dd), [[support.mi...rosoft.com]](https://support.microsoft.com/en-us/windows/deployment/updates-lifecycle/troubleshoot-problems-updating-windows), [[learn.microsoft.com]](https://learn.microsoft.com/en-us/troubleshoot/windows-client/installing-updates-features-roles/troubleshoot-windows-update-issues)
- No remediation executed.
- No assumptions validated.
- **Human review required before any customer communication or action.**

---

## 3. Knowledge-article candidate

**Not created.**

Reason: Resolution has not been verified. Per process requirements, a knowledge article should only be created after the root cause and successful resolution are confirmed.


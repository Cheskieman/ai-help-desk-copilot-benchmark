# Baseline Results

All tickets are fictional. Copilot responses are pasted unchanged. Reviewer notes are my own and show what a stronger answer would add.

## Ticket 1: Individual Connectivity Loss

### Copilot response
Likely fix: Disable and re-enable the user's network adapter (or reconnect to the Wi-Fi network).
Reason: A single user losing connectivity after lunch often points to a local device or connection issue rather than a broader network outage.

#### Baseline review
- **Impact and scope: Partial.** Treated it as a single-user, local issue. Did not consider a broken IP address or a corrupted network stack.
- **Missing information and clarifying questions: Absent.** Asked nothing. A stronger answer would have the user ping the local IP and gather `netsh` output.
- **Evidence for the recommendation: Partial.** Used "single user" and "after lunch." Other network fixes may be needed alongside or instead of an adapter reset.
- **Source support: Absent.** Cited nothing. Reviewer reference: Microsoft, "TCP/IP communication troubleshooting guidance."
- **Confidence: Absent.** Copilot never stated how sure it was. The Microsoft doc is reputable, but that is the reviewer's confidence, not Copilot's.
- **Safe next actions: Partial.** The step is low-risk. A stronger answer would ping first, then reset IP and Winsock, then reset the adapter.
- **Escalation trigger: Absent.** Not stated. Stronger answer: escalate to the network team if reconnecting fails.
- **Human approval: Absent.** Not stated. Stronger answer: a technician reviews steps beyond reconnecting.

##### Improved Results

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




## Ticket 2: Shared Finance Printer Outage

### Copilot response
Likely fix: Restart the shared printer and clear any stuck print jobs in the print queue.
Reason: Multiple users can't print to the same device, suggesting an issue with the shared printer or print service. Because payroll is approaching, restoring the shared printer should be prioritized.

#### Baseline review
- **Impact and scope: Partial.** Noticed multiple users and payroll urgency. Gave only a few possible causes.
- **Missing information and clarifying questions: Absent.** Asked nothing. Stronger answer: is the printer powered on and online? Has the print spooler been restarted?
- **Evidence for the recommendation: Partial.** Used "multiple users" and "same device." Reviewer reference: Microsoft printer connectivity guidance.
- **Source support: Absent.** Cited nothing. Reviewer reference: Microsoft Support, "Fix printer connection and printing problems in Windows."
- **Confidence: Absent.** Copilot did not state confidence. The reference is reputable, but that is the reviewer's judgment.
- **Safe next actions: Partial.** Restart is low-risk. Clearing the queue deletes jobs with no warning. Stronger answer: check the printer connection first.
- **Escalation trigger: Absent.** Not stated. Stronger answer: escalate right away to a senior tech or print/server team if restart fails, the queue won't clear, or payroll is at risk. Notify the finance manager.
- **Human approval: Absent.** Not stated. Stronger answer: Get Finance lead or on-duty technician approval before clearing the queue, since payroll documents may need reprinting.

##### Improved Results

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







## Ticket 3: Recurring Windows 11 Update Failure

### Copilot response
Likely fix: Run the Windows Update Troubleshooter and retry the update.
Reason: Repeated update failures on a single laptop are commonly caused by corrupted update components or configuration issues that the troubleshooter can often repair.

#### Baseline review
- **Impact and scope: Partial.** Noted a single laptop. Did not consider low disk space or internet connectivity.
- **Missing information and clarifying questions: Absent.** Asked nothing. Stronger answer: ask for the error code and check whether free disk space meets update requirements.
- **Evidence for the recommendation: Partial.** Used "repeated failures" but no specific error. Reviewer reference: Microsoft update troubleshooting documentation.
- **Source support: Absent.** Cited nothing. Reviewer reference: Microsoft Support, "Troubleshoot problems updating Windows."
- **Confidence: Absent.** Copilot did not state confidence. Words like "commonly" and "often" are vague.
- **Safe next actions: Partial.** The troubleshooter is low-risk. Stronger answer: check disk space and connectivity first.
- **Escalation trigger: Absent.** Not stated. Stronger answer: escalate to a senior tech or endpoint team if the troubleshooter fails, the same error code recurs, or system files appear corrupted or the laptop won't boot normally.
- **Human approval: Absent.** Not stated. Stronger answer: a technician approves deeper repairs and confirms files are backed up first.

##### Improved Results

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

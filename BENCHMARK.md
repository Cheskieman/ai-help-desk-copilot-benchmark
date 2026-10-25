# Baseline Results
## Ticket 1: Individual Connectivity Loss
### Copilot response
Likely fix: Disable and re-enable the user's network adapter (or reconnect to the Wi‑Fi network).
 Reason: A single user losing connectivity after lunch often points to a local device or connection issue rather than a broader network outage.
### Baseline review
Impact and scope: PARTIAL

Does not account for broken IP address, is the network stack corrupter


Missing information and clarifying questions. PARTIAL

ping the local pcs ip address, list of netsh xommands


Evidence for the recommendation. PARTIAL

Multiple network fixes possible for troubleshooting that may need to be addressed along with or in place of diabklinh and renabling the network driver

Source support. PARTIAL

Microsoft.com Document "TCP/IP communication troubleshooting guidance"



Confidence. PARTIAL

High: The article is an offical Microsft Website Troubleshooting Document 


Safe next actions. PARTIAL

ping the ip adresss for any error messages followed by running commands to reset IP and Winsock followed by resetiing the netwoek adapter


Escalation trigger. PARTIAL
Escalate to the network team if reconnecting doesn’t work


Human approval.PARTIAL
A support technician should review the steps before the user runs anything beyond reconnecting.

## Ticket 2: Shared Finance Printer Outage
### Copilot response
Likely fix: Restart the shared printer and clear any stuck print jobs in the print queue.
 Reason: Multiple users being unable to print to the same device suggests a problem with the shared printer or print service. Because payroll is approaching, restoring the shared printer should be prioritized.
 ### Baseline review
Impact and scope: PARTIAL:

Copilot's suggestions are only a few potential solutions.



Missing information and clarifying questions.PARTIAL

Is the printer pluggged in and online, has the print spooler been restarted to potentially fix this issue, etc


Evidence for the recommendation.PARTIAL

Microsft  Printer connectivity page


Source support.PARTIAL

Microsoft Support "Fix printer connection and printing problems in Windows"

Confidence. PARTIAL

High it is a reputable webpage from Microsft that offers solutions


Safe next actions. PARTIAL

Check if the printer's connection 

Escalation trigger. PARTIAL

Escalate right away to a senior tech or the print/server team if restarting the printer doesn’t restore printing, if the queue won’t clear, or if payroll is at risk of missing its deadline. Tell the finance manager so they know the timeline.

Human approval. PARTIAL
Get approval from the Finance lead (or the on-duty technician) before clearing the print queue, because it deletes everyone’s waiting jobs, and some may be payroll documents that need to be reprinted.

## Ticket 3: Recurring Windows 11 Update Failure
### Copilot response
Likely fix: Run the Windows Update Troubleshooter and retry the update.
 Reason: Repeated update failures on a single laptop are commonly caused by corrupted update components or configuration issues that the troubleshooter can often repair
 ### Baseline review

 Impact and scope. 

Doesn't address disk space being higher than updates allow, or device is properly connected to the internet

Missing information and clarifying questions.

Check disk space utilazation is higher than updates allow 


Evidence for the recommendation.

Micrsoft troubleshooting updates documents


Source support.

Microsoft Support Troubleshoot problems updating Windows

Confidence.

High: reputable website 


Safe next actions.

Check the disk space utilzation and internet conncetivity


Escalation trigger.
Escalate to a senior tech or endpoint team if the troubleshooter fails, if the same error code keeps coming back, or if the laptop shows signs of corrupted system files or won’t boot normally.


Human approval.
technician should approve before any deeper repair (like resetting update components or using system repair tools), and should confirm the user’s files are backed up first.

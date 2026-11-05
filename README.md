# AI-help-desk-copilot-benchmark

## Support Problem

Several support tickets for Tier 1 issues are incomplete. This can lead different technicians to use different solutions for the same issue. Some of these solutions can be risky and can lead to long resolution times. Having a consistent triage step with instructions on how to handle the different issues and the first question that is asked in each case is key.

### Why a Naive Prompt is Risky

When you use a simple prompt to ask the Copilot AI agent to solve a support problem, it will most likely provide one likely solution with a short, vague explanation of why it thinks that solution is correct. This is because there is nothing in the prompt that would lead the Copilot AI agent to ask for more information (to understand the problem better), to provide more reasoning for its answer (to explain why it thinks its answer is correct), to state how confident it is in its answer (to indicate how likely it is that its answer is correct), or to indicate whether or not the problem needs to be escalated to a human support technician (to indicate whether or not the Copilot AI agent believes that the problem is beyond its capabilities). All of these features were missing in the baseline test. For example, in the baseline test, the Copilot AI agent was asked to solve a support problem for an Individual Connectivity Loss for the user's network. The Copilot AI agent provided a solution, but it never stated how confident it was that the answer was correct (i.e., confidence was marked as absent). Based on this, I scored the baseline test four, three, and four for the three combined support problems, for a total of eleven points out of a possible thirty-six points.

### Three-Stage Workflow

- Stage 1: Triage. This stage summarizes the issue(s) identified in the ticket’s scope before assessing the issue’s impact and urgency. The prompt’s output will include: problem statement, affected users and systems, business impact, urgency, category, missing information, clarifying questions, and recommended route.
- Stage 2: Diagnose. This stage ranks possible causes of the issue in the ticket before suggesting evidence-based checks or escalation. Output: ranked hypotheses, evidence for and against, safest next checks, assumptions, confidence, vendor sources to verify, escalation trigger.
- Stage 3: Communicate and Document. This stage prepares a customer update and internal notes for human review. Output: customer-facing update and internal notes for human review. Output: customer-facing update, internal work notes, knowledge-article candidate.

### Supporting Evidence

The links below are the evidence for the case study, so you can check each claim in the summary above.

[Test Tickets](TEST-TICKETS.md): The three fictional unchanged tickets used for both the baseline and improved runs.
[PROMPT-WORKFLOW](PROMPT-WORKFLOW.md): The three-stage workflow prompts used for the improved run.
[BENCHMARK.md](BENCHMARK.md): The before-and-after comparison scores and other related metrics and assessments.


### Score table and statement

| Version | Ticket 1 | Ticket 2 | Ticket 3 | Overall (of 36) |
|---|---|---|---|---|
| Baseline | 4 | 3 | 4 | 11 |
| Improved: Run 1 | 8 | 11 | 11 | 30 |
| Improved: Run 2 | 10 | 11 | 11 | 32 |

These results come from a small controlled test of three synthetic tickets, each scored out of 12 on the same rubric.

### **Example 1 (missing information or evidence-based checks)**

Baseline: The user can disable and re-enable the network adapter on their device, or reconnect to the Wi-Fi network. The user is not asked clarifying questions.

Workflow: Copilot asks the user clarifying questions, including what type of internet the user is using, what happens to the affected device(s) when the internet is lost, and whether any error messages are displayed on the screen.


### **Example 2 (escalation or communication)**

Baseline: Copilot said that since multiple users cannot print to the same device, restart the shared printer and clear stuck print jobs from the queue.

Workflow: The tickets from the two improved runs were treated as high urgency because they impacted payroll and could block it or put it at risk. Therefore, the necessary escalation triggers were listed, a customer status update was drafted, internal work notes were created, and a knowledge-article candidate was created and required human review before taking any action.

### **Limitation and the “does not prove” statement**

Limitations: There was no recommendation for a fix; i.e., the technician must translate the checks Copilot provided into action.

The tests run for this ticket do not prove anything regarding production performance. The ticket was fictional and was scored by one reviewer.

### **Responsible Use**


| Rule | Why it exists |
| --- | --- |
| Synthetic data only | This repository is public and thus no information about any real person or company shall be exposed. |
| Vendor sources require verification before use. | Copilot’s citations may be wrong and thus should be verified by a person before use. |
| Private information and credentials stay outside the workflow. | Do not enter passwords or personal information in the prompt. |
| Human Approval of Output | Human Approval of Output |







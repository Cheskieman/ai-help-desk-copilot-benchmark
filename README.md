# AI-help-desk-copilot-benchmark

## Support Problem

Tier 1 support tickets often arrive incomplete because of how they are reported. This includes missing details such as error messages and how many people are affected, which can result in two technicians handling the same ticket differently. This can lead to risky fixes and slower resolution timelines. Consistent triage provides a clear structure with specific instructions and the same first question, no matter which technician handles it.

### Why a Naive Prompt is Risky

AI prompts that request one fix will most likely get exactly that: one likely fix with a short, vague reason. This is because nothing in the prompt compels the Copilot AI agent to ask clarifying questions, cite reasoning sources, state how confident it is in its answer, or indicate when to escalate or require human approval. Each one of those aforementioned attributes was missing during the baseline test. For example, on a ticket about an Individual Connectivity Loss for the user's network, Copilot never stated how sure it was that its answer was correct (i.e., confidence was marked as absent). As a result, I assessed the baseline score as four, three, and four out of the grand total of thirty-six across the three combined tickets.

#### Three-Stage Workflow

- Stage 1: Triage. This stage summarizes the issue(s) identified in the ticket’s scope before assessing the issue’s impact and urgency. The prompt’s output will include: problem statement, affected users and systems, business impact, urgency, category, missing information, clarifying questions, and recommended route.
- Stage 2: Diagnose. This stage ranks possible causes of the issue in the ticket before suggesting evidence-based checks or escalation. Output: ranked hypotheses, evidence for and against, safest next checks, assumptions, confidence, vendor sources to verify, escalation trigger.
- Stage 3: Communicate and Document. This stage prepares a customer update and internal notes for human review. Output: customer-facing update and internal notes for human review. Output: customer-facing update, internal work notes, knowledge-article candidate.

##### Supporting Evidence

[Test Tickets](TEST-TICKETS.md)

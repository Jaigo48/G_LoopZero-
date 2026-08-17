# LoopZero AI

LoopZero is a small AI-assisted Customer Success and Support ticket-triage demonstration built as a standalone browser-based application.


The project demonstrates how AI-assisted workflows can help a CSM or Support professional:



- Triage incoming customer tickets
- Identify sentiment, priority, and risk
- Separate human-review work from potential automation
- Assist with customer responses
- Track human approvals and completed work
- Experiment with controlled automation
- Review support operations through a dashboard



The project contains 10 fictional sample tickets.



This is a demonstration / personal project. It does not use real customer data and is not intended to represent a production-ready support platform.

\---

## What This Project Demonstrates

LoopZero is built around a simple idea:



AI should help a Support or Customer Success professional move faster without removing the human from important decisions.



The primary workflow is:



```text
Import tickets
   ↓
Run AI Triage
   ↓
Review ticket results
   ↓
Review dashboard and customer risk
   ↓
Identify tickets requiring human attention
   ↓
Human works tickets that require investigation
   ↓
Approve completed work
   ↓
Finalize approved actions
   ↓
Review updated results
```

Automation is handled separately:


```text
Human identifies a safe, repeatable pattern
   ↓
Automation rule is defined
   ↓
AI triage evaluates the ticket
   ↓
PRODUCTION mode allows eligible automation
   ↓
Eligible ticket becomes DONE
```


The important distinction is that AI triage and automation are separate decisions.



AI can identify a ticket as an AUTOMATED\_RESPONSE, but the ticket only becomes DONE when the automation gate allows it under the current LoopZero mode.



This keeps the human responsible for defining what is safe to automate and where the automation boundary should end.

\---

# Getting Started

LoopZero is a browser-based demonstration application. The demonstration uses 10 fictional sample tickets stored in the project and loaded automatically when LoopZero opens.

To begin:

Open the LoopZero application.

The sample tickets will load automatically.

You do not need to manually recreate the sample tickets or configure external AI services before beginning the demonstration.

The demonstration uses local triage rules to evaluate the imported tickets and determine sentiment, priority, AI decision, response draft, and workflow status.

# Step 1 — Import the Sample Tickets

The demonstration includes 10 fictional sample tickets.

When LoopZero opens, the sample ticket data is loaded automatically.

No manual file selection is required to begin the demonstration.

Run AI Triage after the sample tickets have loaded.


## Demo Reset



Click Clear to remove the current tickets.

To restore the 10 sample tickets, simply refresh the page. LoopZero will automatically reload the sample tickets from data.json.

You do not need to download or manually select a JSON file.

\---

## Step 2 — Change LoopZero to PRODUCTION

LoopZero starts in SAFE mode.



For the main demonstration, change the mode to:



PRODUCTION



Use the LoopZero Mode control in the application and select:



PRODUCTION

LoopZero Modes

Mode	Purpose

SAFE	AI can classify tickets, but eligible automation does not complete tickets automatically. Tickets remain available for human review.

PRODUCTION	An eligible AUTOMATED\_RESPONSE can become DONE. Other decisions remain PENDING\_REVIEW.

AUTO	Behaves like PRODUCTION for the automation demonstrated in this project. It is included for experimentation but is not required for the main demonstration.



For this README, PRODUCTION is the main demonstration mode.



SAFE is the default mode.



The LoopZero Mode control allows you to switch between SAFE, PRODUCTION, and AUTO so you can see how the same AI decision can produce different workflow outcomes.



In SAFE mode:


```text
AUTOMATED\_RESPONSE
      ↓
PENDING\_REVIEW
```


In PRODUCTION or AUTO mode, an eligible automated response can become:


```text
AUTOMATED\_RESPONSE
       ↓
DONE
```


Tickets with other decisions remain:



PENDING\_REVIEW

\---

## Step 3 — Run AI Triage

After importing the sample tickets, run AI Triage.



LoopZero analyzes the tickets and populates the AI-related fields.



Depending on the ticket, the system determines information such as:



Sentiment

Action

Priority

AI Decision

AI Reason

AI Response Draft

Status



The AI\_Decision field is particularly important because it indicates how LoopZero has classified the ticket and helps determine its workflow path.



The decision may identify a ticket as:



HUMAN\_REVIEW

HUMAN\_ESCALATION

PRODUCT\_REVIEW

AUTOMATED\_RESPONSE



The selected LoopZero mode then determines the resulting workflow status.



In SAFE mode, an AUTOMATED\_RESPONSE remains:



PENDING\_REVIEW



In PRODUCTION or AUTO mode, an eligible AUTOMATED\_RESPONSE can become:



DONE



Other decisions remain:



PENDING\_REVIEW

\---

## Step 4 — Review the Dashboard

After running AI Triage, review the dashboard in the LoopZero application.



Use the dashboard to quickly identify:



High-risk customers

High-frustration tickets

Human escalations

Tickets requiring attention

Overall support-queue information



The Support Queue provides a more actionable view of tickets requiring human attention.



The dashboard reflects the ticket data available in the application. If ticket statuses or outcomes change, review the dashboard again to see the updated results.



This creates a useful operational rhythm:


```text
AI Triage
   ↓
Dashboard
   ↓
Identify risk
   ↓
Take action
   ↓
Review updated results
```


The dashboard is intended to provide an operational overview rather than replace the detailed ticket view.



<!-- SCREENSHOT: Dashboard after AI Triage, showing the ticket/risk overview. -->

\---

# Human-Review Workflow

When LoopZero identifies a ticket that requires human attention, the result indicates that the ticket needs investigation, judgment, or follow-up.



The actual troubleshooting or customer work would normally happen outside the application.



For this demonstration, pretend to perform that work.



For example, you might:



Investigate the customer's issue

Determine what went wrong

Reproduce the problem when appropriate

Communicate with the customer

Work with another team

Resolve the issue



Tickets that require human attention remain:



PENDING\_REVIEW



The important distinction is that LoopZero is assisting with triage and decision-making. It is not automatically resolving complex or risky customer issues.



The human-review workflow is:


```text
PENDING\_REVIEW
     ↓
Human investigates / works ticket
     ↓
Human determines the appropriate outcome
     ↓
Human approval / finalization workflow
     ↓
DONE\_FINAL
```


This is deliberately different from automated completion.



An automated ticket follows:


```text
AUTOMATED\_RESPONSE
    ↓
PRODUCTION or AUTO
    ↓
DONE
```


Human review and controlled automation are therefore separate workflow paths.



<!-- SCREENSHOT: Sheet1 showing a human-review ticket with an example Human\\\\\\\_Notes entry. -->

<!-- SCREENSHOT: Sheet1 showing the ticket after finalization as DONE\\\\\\\_FINAL. -->

\---

# Final Controlled Automation — Ticket #7

LoopZero does not automatically decide that every ticket is safe to automate.



Instead, the human defines a narrow automation boundary around a repeatable and low-risk pattern.



For the final automation demonstration, the controlled automation pattern is a password-reset recovery request.



Example: Ticket #7



Ticket #7 is an existing sample ticket:



Customer: \[Ticket #7 customer]

Category: User Error



The ticket describes a customer who is having trouble receiving a password-reset email or link.



No JSON is changed.



No new ticket is created.



The automation rule is added to the existing User Error triage logic.



The goal is to demonstrate how an existing ticket pattern can be deliberately promoted from human review to a limited automated response.



Current Automation Boundary



The password-reset recovery pattern is eligible for automation only when:



The customer is dealing with a password-reset request.

The reset email or reset link has not arrived.

The message does not indicate data loss.

The message does not indicate deleted data.

The message does not indicate a security issue.



If those conditions are not met, the ticket remains on the appropriate human-review path.



The automation rule therefore represents a specific pattern rather than a specific ticket ID.



Run the Automation Demonstration



Make sure LoopZero is in:



PRODUCTION



Then run AI Triage.



Ticket #7 should receive:



AI\_Decision:

AUTOMATED\_RESPONSE



Because the system is in PRODUCTION mode, the automation gate allows an eligible AUTOMATED\_RESPONSE to become:



DONE



The demonstration is therefore:


```text
Ticket #7
   ↓
Password-reset recovery pattern
   ↓
AUTOMATED\_RESPONSE
   ↓
PRODUCTION
   ↓
DONE
```


This demonstrates the distinction between AI classification and automation execution.



The human defined the automation boundary first.



Ticket #7 is the sole final controlled automation demonstration in LoopZero.



Other tickets continue through their normal human-review or product-review workflows.

\---

# Understanding the Status Workflow

The ticket status is one of the most important parts of LoopZero because it shows where the ticket is in the workflow.

The main statuses demonstrated by the project are:

|Status|Meaning|
|-|-|
|`PENDING\\\\\\\_REVIEW`|Human attention is still required.|
|`APPROVED`|A human has approved the proposed action.|
|`DONE`|An automated action has completed.|
|`CORRECTED`|A human has corrected or adjusted the AI result.|
|`DONE\\\\\\\_FINAL`|A human-approved workflow has been finalized.|
|`IN\\\\\\\_PROGRESS`|The ticket is actively being worked.|
|`ERROR`|The system encountered an error while processing the ticket.|

These statuses help separate **AI recommendation**, **human approval**, and **actual completion**.

\---

# Human Approval vs. Automation

There are two different completion paths in LoopZero.

## Human-Handled Ticket

A ticket requiring human work follows:

```text
PENDING\\\\\\\_REVIEW
      ↓
Human works ticket
      ↓
Human\\\\\\\_Notes
      ↓
APPROVED
      ↓
Finalize Approved Actions
      ↓
DONE\\\\\\\_FINAL
```

The approval is explicitly recorded.

The project stores:

* `Approved\\\\\\\_By`
* `Approval\\\\\\\_Time`
* `Human\\\\\\\_Notes`

The finalization process also writes a record to the learning log.

\---

## Automated Ticket

An approved automation pattern follows:

```text
AI Analysis
      ↓
AUTOMATED\\\\\\\_RESPONSE
      ↓
PRODUCTION
      ↓
DONE
```

There is no human approval step between the AI decision and `DONE` for an eligible automated response.

This is why the automation boundary needs to be deliberately defined.

\---

# How LoopZero Decides Whether Automation Can Complete a Ticket

Inside `runTriage()`, the mode controls the status outcome.

The relevant logic is:

```javascript
/\* LOOPZERO MODE \*/



&#x20;   const currentMode = getLoopZeroMode();



&#x20;   if (

&#x20;     (currentMode === "PRODUCTION" ||

&#x20;     currentMode === "AUTO") \&\&

&#x20;     decisionResult === "AUTOMATED\_RESPONSE"

&#x20;   ) {



&#x20;     statusResult = "DONE";



&#x20;   } else {



&#x20;     statusResult = "PENDING\_REVIEW";



&#x20;   }

```

This is the core automation gate.

The important relationship is:


SAFE
→ Everything remains PENDING\\\\\\\_REVIEW

PRODUCTION
→ AUTOMATED\\\\\\\_RESPONSE can become DONE
→ Other decisions remain PENDING\\\\\\\_REVIEW

This allows you to practice an automation pattern in SAFE mode before allowing it to operate in PRODUCTION.

\---

# Health Scores and Customer Risk

LoopZero also calculates a simple customer health score based on signals identified from the customer's ticket.



The score is stored in:



Health Score

Risk Level

Score Reasons



The health score is intended as a demonstration of how support-ticket information can be connected to Customer Success risk.



The project starts each customer at:



100



The rule engine then adjusts the score based on signals in the ticket.



For example, negative language can reduce the score:


```text
const negativeWords = \[
 "urgent",
 "broken",
 "error",
 "crashing",
 "locked out",
 "impossible",
 "deleted",
 "lose",
 "timeout"
];
```


A negative signal can result in:



Negative Sentiment



being recorded as a score reason.



Higher-risk account tiers can also receive an additional penalty when the ticket already indicates negative sentiment.



The resulting risk levels are:



Healthy

At Risk

Critical



These are intentionally simple demonstration rules rather than a production customer-health model.

\---

\---

# The Complete Demonstration

The recommended order for demonstrating LoopZero is:



## 1\. Import the Sample Tickets



Once page loads, or refreshing the page, LoopZero application will import the provided sample JSON.


\---

## 2\. Set LoopZero to PRODUCTION



For the primary automation demonstration, set LoopZero to:



PRODUCTION



PRODUCTION allows an eligible AUTOMATED\_RESPONSE decision to become DONE.

\---

## 3\. Run AI Triage



Run the AI Triage process and review the resulting ticket information, including:



Sentiment

Action

Priority

AI Decision

AI Reason

AI Response Draft

Status



The AI\_Decision field is particularly important because it determines which workflow path the ticket follows.

\---

## 4\. Review the Dashboard



Review the dashboard to identify:



Customer risk

High-priority tickets

Human escalations

Tickets requiring attention

Support-queue information



Refresh the dashboard later when ticket statuses or outcomes change.

\---

## 5\. Work a Human-Review Ticket



Find a ticket marked:



PENDING\_REVIEW



Review the AI recommendation and pretend to perform the necessary Support or Customer Success work.



Record an example of the work performed in:



Human\_Notes



Then complete the human-review workflow through the application's approval and finalization controls.



The ticket should ultimately become:



DONE\_FINAL



This demonstrates the human-controlled completion path.

\---

## 6\. Final Controlled Automation — Ticket #7



The approved automation pattern is the narrow password-reset recovery pattern described earlier.



With LoopZero in:



PRODUCTION



run AI Triage.



Ticket #7 should receive:



AI\_Decision:

AUTOMATED\_RESPONSE



The production automation gate then allows the eligible automated response to become:



DONE



The demonstration is:


```text
Ticket #7
     ↓
Password-reset recovery pattern
     ↓
AUTOMATED\_RESPONSE
     ↓
PRODUCTION
     ↓
DONE
```


Ticket #7 remains the sole permanent automation example in this demonstration.
---

**You've completed the main LoopZero demonstration.**

If you'd like to experiment with the code behind the workflow, continue with the five-minute experiment below. For more advanced exercises involving automation behavior, see `EXTRA.md`.
\---

# Mode Practice

The three modes provide different levels of workflow control.

## SAFE

Use SAFE when you want to observe the AI decision without allowing automation to complete eligible tickets.



AI Decision

&#x20;    ↓

PENDING\_REVIEW



SAFE is useful for practicing and validating automation behavior before allowing automated completion.

\---

## PRODUCTION

Use PRODUCTION when an automation rule has been deliberately defined and you want eligible automated responses to complete.



AUTOMATED\_RESPONSE

&#x20;    ↓

DONE



Tickets with other AI decisions remain:



PENDING\_REVIEW



PRODUCTION is the primary mode used for the final controlled automation demonstration with Ticket #7 and the temporary automation exercise with Ticket #9.

\---

## AUTO

AUTO uses the same automation gate as PRODUCTION.



An eligible:



AUTOMATED\_RESPONSE



can become:



DONE



Other decisions remain:



PENDING\_REVIEW



AUTO is included for experimentation but is not required for the main demonstration.

\---


# Final Takeaway

LoopZero demonstrates a simple but important principle:

**AI can help decide what should happen to a ticket, while explicit rules determine what the system is allowed to do automatically.**

Throughout this demonstration, you saw tickets move through:

Ticket → AI Triage → AI Decision → Human Review or Controlled Automation → Final Status

You also saw that not every AI decision should result in automatic completion. Some tickets require human review, while others can be handled automatically when the rules and operating mode allow it.

The goal of LoopZero is not to automate everything.

The goal is to demonstrate how automation can be controlled, observable, and reversible.

**You've completed the main LoopZero demonstration.**

If you'd like to experiment with the code behind the workflow, continue with the five-minute experiment below. For more advanced exercises involving automation behavior, see `EXTRA.md`.

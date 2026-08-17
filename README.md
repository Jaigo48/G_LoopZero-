# LoopZero AI

LoopZero is a small AI-assisted Customer Success and Support ticket-triage demonstration built as a standalone HTML application.



The project demonstrates how AI-assisted workflows can help a CSM or Support professional:



Triage incoming customer tickets

Identify sentiment, priority, and risk

Separate human-review work from potential automation

Assist with customer responses

Track human approvals and completed work

Experiment with controlled automation

Review support operations through a dashboard



The project contains 10 fictional sample tickets.



This is a demonstration / personal project. It does not use real customer data and is not intended to represent a production-ready support platform.

\---

## What This Project Demonstrates

LoopZero is built around a simple idea:



AI should help a Support or Customer Success professional move faster without removing the human from important decisions.



The primary workflow is:



Import tickets

&#x20;     ↓

Run AI Triage

&#x20;     ↓

Review ticket results

&#x20;     ↓

Review dashboard and customer risk

&#x20;     ↓

Identify tickets requiring human attention

&#x20;     ↓

Human works tickets that require investigation

&#x20;     ↓

Approve completed work

&#x20;     ↓

Finalize approved actions

&#x20;     ↓

Review updated results



Automation is handled separately:



Human identifies a safe, repeatable pattern

&#x20;     ↓

Automation rule is defined

&#x20;     ↓

AI triage evaluates the ticket

&#x20;     ↓

PRODUCTION mode allows eligible automation

&#x20;     ↓

Eligible ticket becomes DONE



The important distinction is that AI triage and automation are separate decisions.



AI can identify a ticket as an AUTOMATED\_RESPONSE, but the ticket only becomes DONE when the automation gate allows it under the current LoopZero mode.



This keeps the human responsible for defining what is safe to automate and where the automation boundary should end.

\---

# Getting Started

LoopZero is a browser-based demonstration application. The demonstration uses 10 fictional sample tickets stored in the project and loaded automatically when LoopZero opens.

To begin:

Open the LoopZero application.

The sample tickets will load automatically.

Run AI Triage to analyze the tickets.

Review the results through the ticket table and dashboard.

You can also use Import JSON to load a different compatible ticket dataset.

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



AUTOMATED\_RESPONSE

&#x20;       ↓

PENDING\_REVIEW



In PRODUCTION or AUTO mode, an eligible automated response can become:



AUTOMATED\_RESPONSE

&#x20;       ↓

DONE



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



AI Triage

&#x20;   ↓

Dashboard

&#x20;   ↓

Identify risk

&#x20;   ↓

Take action

&#x20;   ↓

Review updated results



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



PENDING\_REVIEW

&#x20;     ↓

Human investigates / works ticket

&#x20;     ↓

Human determines the appropriate outcome

&#x20;     ↓

Human approval / finalization workflow

&#x20;     ↓

DONE\_FINAL



This is deliberately different from automated completion.



An automated ticket follows:



AUTOMATED\_RESPONSE

&#x20;     ↓

PRODUCTION or AUTO

&#x20;     ↓

DONE



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



Ticket #7

&#x20;   ↓

Password-reset recovery pattern

&#x20;   ↓

AUTOMATED\_RESPONSE

&#x20;   ↓

PRODUCTION

&#x20;   ↓

DONE



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
```

This allows you to practice an automation pattern in SAFE mode before allowing it to operate in PRODUCTION.

\---

# Automation Boundary

The most important part of a controlled automation rule is not simply the proposed response.



It is the boundary.



The boundary defines:



What is safe to automate, and what must remain with a human?



For example:



Safe to automate:

Simple password-reset recovery requests that meet the defined conditions



Remain human:

Feature requests requiring roadmap decisions

Pricing questions

Contract questions

Account-specific issues

Security concerns

Data-loss issues

Access problems

Technical incidents



This is how automation can be useful without treating every ticket as interchangeable.



Ticket #7 demonstrates this principle by using a narrow password-reset recovery pattern rather than automatically handling every User Error ticket.

\---

# Escalation Trigger

Every useful automation rule should also define when automation must stop and a human must take over.



For the Ticket #7 password-reset recovery pattern, conditions such as the following should remain outside the automation boundary:



If the customer reports data loss,

account access problems,

security concerns,

or a production-impacting issue,

do not automate.



These conditions represent situations where the ticket requires human judgment, investigation, or escalation.



The goal is not to make automation handle everything.



The goal is to make automation handle the right things.

\---

# Proposed Response

A controlled automation rule should define the response that will be sent when the ticket matches the approved automation boundary.



For Ticket #7, the automated response is part of the existing User Error triage logic.



Before allowing an automated response to operate in PRODUCTION, the response should be reviewed for:



Accuracy

Relevance to the customer's request

Appropriate tone

Unsupported promises or commitments

Conditions that require human judgment

Consistency with the automation boundary



The response should only be used when the ticket matches the conditions that were deliberately defined for the automation.



This keeps the automated response narrow, predictable, and consistent with the purpose of the automation rule.

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



const negativeWords = \[

&#x20; "urgent",

&#x20; "broken",

&#x20; "error",

&#x20; "crashing",

&#x20; "locked out",

&#x20; "impossible",

&#x20; "deleted",

&#x20; "lose",

&#x20; "timeout"

];



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

# Why Customer Health Matters to a CSM

A support ticket is not always just a support ticket.

A pattern of:

* repeated frustration
* access problems
* unresolved technical issues
* high-priority incidents
* important-account problems

can be a signal that a Customer Success Manager should pay attention to the broader customer relationship.

That is why LoopZero surfaces customer risk alongside ticket operations.

The goal is to connect:

```text
Support Activity
      ↓
Customer Risk
      ↓
CSM Awareness
      ↓
Proactive Customer Success
```

This helps demonstrate how a CSM and Support function can work from the same operational information.

\---

# Supporting Data and System Information

LoopZero maintains supporting information behind the main ticket workflow.



This information helps the demonstration track processing history, errors, completed human-reviewed work, cached analysis, and dashboard information where applicable.



The normal user workflow is centered on the LoopZero application and its ticket view rather than requiring users to manage supporting data directly.



The important concept is:



The ticket workflow is the primary working surface. Supporting information exists behind that workflow to help the demonstration remain traceable, reviewable, and understandable.



Users do not need to manually manage supporting system information to complete the main demonstration.

\---

# Dashboard and Support Queue

The LoopZero dashboard is designed to give a CSM or Support professional a quick operational view without requiring them to inspect every ticket individually.



The dashboard can surface information such as:



Ticket volume

Customer risk

Critical tickets

At-risk customers

Human escalations

Pending support actions



The Support Queue provides a more actionable view of tickets requiring human attention.



The dashboard should be treated as a snapshot of the current ticket data rather than a live real-time view.



If ticket statuses or outcomes change, refresh or regenerate the dashboard so that it reflects the updated ticket state.



For example:



Dashboard generated

&#x20;     ↓

Ticket approved

&#x20;     ↓

Ticket finalized

&#x20;     ↓

Ticket becomes DONE\_FINAL

&#x20;     ↓

Dashboard refreshed

&#x20;     ↓

Dashboard reflects the new state



This is particularly useful during the demonstration because the dashboard shows how the operational picture changes as tickets move through the workflow.

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



Ticket #7

&#x20;     ↓

Password-reset recovery pattern

&#x20;     ↓

AUTOMATED\_RESPONSE

&#x20;     ↓

PRODUCTION

&#x20;     ↓

DONE



Ticket #7 remains the sole permanent automation example in this demonstration.

\---

## 7\. In EXTRA.md- Automation Exercise — Ticket #9



Ticket #9 is a separate training exercise.



It demonstrates how an automation rule can be temporarily added to an existing ticket pattern and then reversed.



The Feature Request rule is temporarily changed so that the appropriate informational Feature Request can receive:



AUTOMATED\_RESPONSE



In PRODUCTION, that eligible response can become:



DONE



The exercise then reverses the code change and restores Ticket #9 to:



PRODUCT\_REVIEW

&#x20;     ↓

PENDING\_REVIEW



This demonstrates that an automation rule can be deliberately changed and safely removed when necessary.

\---

## 8\. Demonstrate SAFE Mode



After reversing the Ticket #9 automation, SAFE mode can be used to demonstrate the automation gate without allowing an eligible automated response to complete automatically.



The relationship is:



SAFE

→ AUTOMATED\_RESPONSE remains PENDING\_REVIEW



This provides a controlled way to observe and validate automation behavior.

\---

## The Overall Pattern



The complete demonstration illustrates:



Identify pattern

&#x20;     ↓

Define boundary

&#x20;     ↓

Test safely

&#x20;     ↓

Use PRODUCTION when appropriate

&#x20;     ↓

Monitor result

&#x20;     ↓

Reverse when necessary



Ticket #9 demonstrates the separate process of temporarily changing an automation rule and then reversing that change.---

# A CSM + Support Perspective

LoopZero is intentionally designed around the overlap between Customer Success and Support.



A Support professional may focus on:



Resolving the customer's immediate problem

Prioritizing incidents

Escalating technical issues

Responding efficiently

Identifying repeatable support requests



A CSM may focus on:



Customer health

Account importance

Business impact

Customer sentiment

Relationship risk

Product feedback

Proactive follow-up



LoopZero combines those perspectives.



For example:



Customer reports a serious issue

&#x20;         ↓

AI identifies high frustration

&#x20;         ↓

Ticket receives higher priority

&#x20;         ↓

Customer health may be affected

&#x20;         ↓

Support works the immediate problem

&#x20;         ↓

CSM can recognize the broader account risk



This is the core reason the project includes both ticket-level analysis and customer-health information.



The purpose is not to replace either function. It is to demonstrate how the same support information can help Support manage the immediate issue while giving Customer Success additional context about customer risk.

\---

# What LoopZero Is — and Is Not

## LoopZero Is

A demonstration of how AI-assisted support operations can combine:



Ticket triage

Risk identification

Human review

Controlled automation

Customer response drafting

Approval workflows

Customer-health signals

Dashboard-based operational visibility

Reversible automation exercises

## LoopZero Is Not

LoopZero is not intended to be:



A production support platform

A replacement for a CRM

A complete customer-health system

A fully autonomous support agent

A production-grade security architecture

A production-ready AI governance framework



The automation rules are intentionally simple so the workflow can be understood and demonstrated.



Ticket #7 provides the final controlled automation example, while Ticket #9 provides a separate training exercise showing how an automation rule can be temporarily added and then reversed.

\---

# Important Safety Principle

The project intentionally separates:



AI decision



from:



automation



An AI classification does not automatically mean that a ticket should be automated.



Before an automation rule is used, the human defines:



Whether the pattern is repeatable

Whether the response is safe

What the automation boundary should be

What conditions require human escalation

Whether the automation should operate in PRODUCTION



This distinction is demonstrated in two different ways:



Ticket #7

→ Final controlled automation



Ticket #9

→ Temporary automation exercise

→ Reversal back to human review



This is why the project includes SAFE, PRODUCTION, and AUTO modes.



SAFE allows automation behavior to be observed without automatically completing an eligible ticket.



PRODUCTION and AUTO allow an eligible AUTOMATED\_RESPONSE to become DONE.

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

# Troubleshooting

## The Dashboard Does Not Show My Latest Status

The dashboard is a snapshot of the ticket data at the time it was generated. It is not automatically refreshed every time a ticket changes.



If a ticket status or outcome changes, refresh or regenerate the dashboard in the LoopZero application so that it reflects the latest ticket state.



For example:



Ticket status changes

&#x20;     ↓

Refresh / regenerate dashboard

&#x20;     ↓

Dashboard reflects the updated state

\---

## A Ticket Did Not Become DONE

If a ticket did not become DONE, check:



The current LoopZero mode

The AI\_Decision

Whether the decision is AUTOMATED\_RESPONSE

Whether the automation rule actually matches the ticket

Whether the ticket is already in a completed or review status



The current automation gate is:



const currentMode = getLoopZeroMode();



if (

&#x20; (currentMode === "PRODUCTION" ||

&#x20; currentMode === "AUTO") \&\&

&#x20; decisionResult === "AUTOMATED\_RESPONSE"

) {



&#x20; statusResult = "DONE";



} else {



&#x20; statusResult = "PENDING\_REVIEW";



}



Therefore, an eligible ticket becomes DONE only when:



LoopZero mode = PRODUCTION or AUTO

AND

AI\_Decision = AUTOMATED\_RESPONSE



A ticket with:



PRODUCT\_REVIEW



or:



HUMAN\_ESCALATION



remains:



PENDING\_REVIEW



Likewise, an AUTOMATED\_RESPONSE remains PENDING\_REVIEW when LoopZero is operating in SAFE mode.



If Ticket #9 is being used for the temporary automation exercise, also verify that the temporary Feature Request code change is currently active. After the automation is reversed, Ticket #9 should correctly return to PRODUCT\_REVIEW and PENDING\_REVIEW.

\---

## A Ticket Remains in PENDING\_REVIEW in SAFE Mode

This is expected behavior.



In SAFE mode, an eligible AUTOMATED\_RESPONSE does not become DONE.



The current automation gate allows completion only when the mode is PRODUCTION or AUTO and the AI decision is AUTOMATED\_RESPONSE:



const currentMode = getLoopZeroMode();



if (

&#x20; (currentMode === "PRODUCTION" ||

&#x20; currentMode === "AUTO") \&\&

&#x20; decisionResult === "AUTOMATED\_RESPONSE"

) {



&#x20; statusResult = "DONE";



} else {



&#x20; statusResult = "PENDING\_REVIEW";



}



Therefore:



SAFE

&#x20;   ↓

AUTOMATED\_RESPONSE

&#x20;   ↓

PENDING\_REVIEW



The purpose of SAFE mode is to allow the automation behavior to be observed and validated without automatically completing the ticket.

\---

## Automation Was Reversed

If Ticket #9 no longer becomes an AUTOMATED\_RESPONSE, this may mean the temporary automation change has already been reversed.



To verify the final state, open the current triage function and locate the Feature Request section.



The original Feature Request behavior should be restored so that it assigns:



decisionResult = "PRODUCT\_REVIEW";



The Feature Request logic should also use the original Product Review reason and response draft.



After restoring the original code, run AI Triage again.



Ticket #9 should return to:



AI\_Decision:

PRODUCT\_REVIEW



Status:

PENDING\_REVIEW



The intended final state is:



Ticket #7

→ AUTOMATED\_RESPONSE

→ DONE in PRODUCTION



Ticket #9

→ PRODUCT\_REVIEW

→ PENDING\_REVIEW



This confirms that Ticket #9 has returned to the normal human-review workflow and that Ticket #7 remains the sole permanent automation demonstration.

\---

# Project Menu

The main LoopZero application supports the following demonstration workflow:



Workflow			      Purpose

Refresh Page/                  Load the 10 fictional sample tickets
Import JSON			      

AI Triage			      Analyze and classify the imported tickets

Dashboard			      Review customer risk and support-queue information

Human Review			Work tickets that require investigation or judgment

Approval and Finalization	Complete the human-controlled workflow

LoopZero Mode			Switch between SAFE, PRODUCTION, and AUTO

Controlled Automation		Allow an eligible AUTOMATED\_RESPONSE to become DONE

Automation Reversal		Restore a temporary automation rule to its original human-review behavior



The primary automation demonstration uses Ticket #7.



Ticket #9 is a separate training exercise used to demonstrate how an automation rule can be temporarily added and then reversed.  EXTRA.md has Ticket #9 exercise.

\---

# Final Takeaway

LoopZero demonstrates a simple but important support-automation principle:



Do not automate the ticket just because AI can classify it. Automate a well-defined, repeatable pattern with a clear boundary and a clear way to reverse it.



The project demonstrates that process:



Customer Ticket

&#x20;     ↓

AI Triage

&#x20;     ↓

Risk + Priority + Decision

&#x20;     ↓

Human Review OR Controlled Automation

&#x20;     ↓

Completion

&#x20;     ↓

Monitoring

&#x20;     ↓

Reversal when necessary



For a CSM or Support professional, the value is not simply reducing the number of tickets that require human attention.



The larger opportunity is to spend human time where it matters most:



Routine + Safe

&#x20;     → Automation



Complex + Risky

&#x20;     → Human



High Customer Risk

&#x20;     → CSM Awareness + Support Action



Ticket #7 demonstrates the final controlled automation path.



Ticket #9 demonstrates that an automation rule can be temporarily introduced and then reversed back to the normal human-review workflow.



That is the core idea behind LoopZero AI.


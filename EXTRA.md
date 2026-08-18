# LoopZero — Extra Coding Exercises

These exercises go one step further than the main LoopZero demonstration.

They let you modify the code that controls automation behavior and then observe how the change affects the workflow.

> **Before starting:** Complete the main LoopZero demonstration in `README.md` first. You should have run AI Triage, worked through the applicable tickets, approved the appropriate actions, and finalized the tickets before attempting these exercises.

## Exercise 1 — Automation Exercise — Ticket #9

This exercise demonstrates how changing a triage rule can move a ticket from normal product review into an automated response.

You will temporarily change the Feature Request logic so that certain simple, informational feature requests can receive an `AUTOMATED_RESPONSE`.

You will then test the change in both **SAFE** and **PRODUCTION** modes so you can see the difference between an automated decision and an automated completion.

> **Important:** Do not change `data.json` and do not create a new ticket. This exercise uses the existing Ticket #9.

> **Important:** FIRST start in **SAFE** mode.  Then switch to **PRODUCTION** when directed.

### Step 1 — Open `index.html`

Open `index.html` in your preferred code editor.

Use your editor's **Find/Search** feature and search for:

```text
ticket.Category === "Feature Request"
```

You should find this existing Feature Request block inside the `runTriage()` function:

```javascript
} else if (ticket.Category === "Feature Request") {

      decisionResult = "PRODUCT_REVIEW";

      reasonResult =
        "Feature request requires product review.";

}
```

This is the code you are going to temporarily replace.

### Step 2 — Temporarily Automate Ticket #9

**Replace** the entire Feature Request block above with:

```javascript
} else if (ticket.Category === "Feature Request") {

      const simpleFeatureKeywords = [
        "is there",
        "coming soon",
        "would love",
        "feature request",
        "support"
      ];

      const simpleFeatureRequest =
        simpleFeatureKeywords.some(keyword =>
          lowerMessage.includes(keyword)
        );

      if (simpleFeatureRequest) {

        decisionResult = "AUTOMATED_RESPONSE";

        reasonResult =
          "Feature request is informational only and does not require product decision-making.";

        responseDraft =
          "Hello " + ticket.Customer + ",\n\n" +
          "Thank you for sharing your feedback with us.\n\n" +
          "We appreciate hearing how your team uses the platform. " +
          "Your request has been documented and shared with our product team for consideration.\n\n" +
          "Thank you,\nLoopZero Support";

      } else {

        decisionResult = "PRODUCT_REVIEW";

        reasonResult =
          "Feature request requires product review.";

      }

}
```

The new code looks for simple phrases in the ticket message.

Ticket #9 contains:

```text
"Is there a dark mode version of the web app coming soon?"
```

so it matches the new rule.

**Save `index.html`, then refresh the LoopZero page in your browser before running AI Triage again.** This ensures the browser loads your updated JavaScript.

> **Do not change `data.json`.** Ticket #9 already contains the message needed for this exercise.

### Step 3 — Run AI Triage in SAFE Mode

In LoopZero, select:

```text
SAFE
```

Then run:

**AI Triage**

Find **Ticket #9**.

Look at its **AI Decision** and **Status**.

You should see:

```text
AI Decision:
AUTOMATED_RESPONSE
```

but its status should remain:

```text
PENDING_REVIEW
```

This is expected.

The triage rule has decided that the ticket can receive an automated response, but the current automation gate does not allow `AUTOMATED_RESPONSE` to become `DONE` while LoopZero is in SAFE mode.

The SAFE workflow is therefore:

```text
Ticket #9
    ↓
Feature Request
    ↓
AUTOMATED_RESPONSE
    ↓
SAFE
    ↓
PENDING_REVIEW
```

> **If you did not see `PENDING_REVIEW` in SAFE mode, you may have run AI Triage while LoopZero was still in PRODUCTION mode.** If PRODUCTION has already moved the ticket to `DONE` or `DONE_FINAL`, changing to SAFE will not automatically move that completed ticket back to `PENDING_REVIEW`. **Simply refresh the LoopZero page, select SAFE mode, and run AI Triage again.**


### Step 4 — Test the Same Ticket in PRODUCTION Mode

Now select:

```text
PRODUCTION
```

Run:

**AI Triage**

Find **Ticket #9** again.

This time you should see:

```text
AI Decision:
AUTOMATED_RESPONSE
```

and:

```text
Status:
DONE
```

The workflow is now:

```text
Ticket #9
    ↓
Feature Request
    ↓
AUTOMATED_RESPONSE
    ↓
PRODUCTION
    ↓
DONE
```

This happens because the existing LoopZero automation gate allows an `AUTOMATED_RESPONSE` to become `DONE` when the current mode is **PRODUCTION** or **AUTO**.

### Step 5 — Compare SAFE and PRODUCTION

You have now tested the same modified triage rule in two different modes.

**SAFE:**

```text
AUTOMATED_RESPONSE
        ↓
PENDING_REVIEW
```

**PRODUCTION:**

```text
AUTOMATED_RESPONSE
        ↓
DONE
```

This is an important distinction.

The change you made to the Feature Request logic determines the **AI Decision**.

The existing LoopZero mode logic determines whether that decision is allowed to complete automatically.

In other words:

```text
Feature Request Rule
        ↓
AI Decision
        ↓
LoopZero Mode
        ↓
Workflow Status
```

### What You Just Changed

You changed the Feature Request rule from:

```text
Feature Request
      ↓
PRODUCT_REVIEW
```

to a conditional rule:

```text
Feature Request
      ↓
Does the message contain a simple feature-request phrase?
      ↓
YES → AUTOMATED_RESPONSE
NO  → PRODUCT_REVIEW
```

This means you did **not** make every Feature Request automatically handled.

You created a narrower rule for informational feature requests.

Ticket #9 qualifies because its message contains phrases such as `"is there"` and `"coming soon"`.

### Important — Leave the Change in Place

**Do not restore the original Feature Request code yet.**

Exercise 2 will continue directly from this exercise.

In Exercise 2, you will reverse the code change you just made and then repeat the **SAFE** and **PRODUCTION** tests.

This will allow you to see the difference between:

```text
Before the change
        ↓
PRODUCT_REVIEW
```

and:

```text
After the change
        ↓
AUTOMATED_RESPONSE
```

and then verify that reversing the code restores the original behavior.

**You changed the rule that defines the automation boundary.**

This is why automation rules should be deliberate, narrow, and reversible.


---

## Exercise 2 — Automation Was Reversed

This exercise continues directly from **Exercise 1 — Automation Exercise — Ticket #9**.

In Exercise 1, you changed the Feature Request logic so that Ticket #9 could receive an `AUTOMATED_RESPONSE`.

You then tested that change in both **SAFE** and **PRODUCTION** modes.

Now you will reverse that code change and run the same tests again.

The purpose is to see exactly what happens when an automation rule is removed.

> **Important:** Do not start this exercise until you have completed Exercise 1. Leave the `simpleFeatureKeywords` code from Exercise 1 in place until you reach Step 2 below.

### Step 1 — Confirm the Code From Exercise 1 Is Still in Place

Open `index.html` in your preferred code editor.

Use your editor's **Find/Search** feature and search for:

```text id="q2n7vx"
simpleFeatureKeywords
```

You should find the Feature Request section you added in Exercise 1:

```javascript id="m4t6kp"
} else if (ticket.Category === "Feature Request") {

      const simpleFeatureKeywords = [
        "is there",
        "coming soon",
        "would love",
        "feature request",
        "support"
      ];

      const simpleFeatureRequest =
        simpleFeatureKeywords.some(keyword =>
          lowerMessage.includes(keyword)
        );

      if (simpleFeatureRequest) {

        decisionResult = "AUTOMATED_RESPONSE";

        reasonResult =
          "Feature request is informational only and does not require product decision-making.";

        responseDraft =
          "Hello " + ticket.Customer + ",\n\n" +
          "Thank you for sharing your feedback with us.\n\n" +
          "We appreciate hearing how your team uses the platform. " +
          "Your request has been documented and shared with our product team for consideration.\n\n" +
          "Thank you,\nLoopZero Support";

      } else {

        decisionResult = "PRODUCT_REVIEW";

        reasonResult =
          "Feature request requires product review.";

      }

}
```

If you can see this code, you are ready to reverse the change.

### Step 2 — Restore the Original Feature Request Logic


**Replace** the entire `Feature Request` block from Exercise 1 with the original code:

```javascript id="y6n0sa"
} else if (ticket.Category === "Feature Request") {

      decisionResult = "PRODUCT_REVIEW";

      reasonResult =
        "Feature request requires product review.";

}
```

You have now removed the temporary automation rule.

**Save `index.html`, then refresh the LoopZero page in your browser before running AI Triage again.** This ensures the browser loads your restored JavaScript.

> **Do not change `data.json`.** Ticket #9 is still the ticket you will use for this test.

### Step 3 — Run AI Triage in SAFE Mode

In LoopZero, select:

```text id="0e1r2u"
SAFE
```

Then run:

**AI Triage**

Find **Ticket #9**.

The original Feature Request rule should now classify the ticket as:

```text id="8hr4t1"
AI Decision:
PRODUCT_REVIEW
```

Its status should be:

```text id="p7v2m8"
PENDING_REVIEW
```

The workflow is now:

```text id="s6q9kc"
Ticket #9
    ↓
Feature Request
    ↓
PRODUCT_REVIEW
    ↓
SAFE
    ↓
PENDING_REVIEW
```

This is the original behavior restored.

> **If you did not see `PENDING_REVIEW` in SAFE mode, you may have run AI Triage while LoopZero was still in PRODUCTION mode.** If PRODUCTION has already moved the ticket to `DONE` or `DONE_FINAL`, changing to SAFE will not automatically move that completed ticket back to `PENDING_REVIEW`. **Simply refresh the LoopZero page, select SAFE mode, and run AI Triage again.**


### Step 4 — Test the Same Ticket in PRODUCTION Mode

Now select:

```text id="q5w8na"
PRODUCTION
```

Run:

**AI Triage**

Find **Ticket #9** again.

You should still see:

```text id="t3x7pb"
AI Decision:
PRODUCT_REVIEW
```

and:

```text id="r8m2vd"
Status:
PENDING_REVIEW
```

Notice what happened.

Changing from SAFE to PRODUCTION did **not** make Ticket #9 automatic this time.

That is because the triage decision is now:

```text id="e1k6zs"
PRODUCT_REVIEW
```

rather than:

```text id="n4p9yw"
AUTOMATED_RESPONSE
```

The existing automation gate only allows `AUTOMATED_RESPONSE` to become `DONE` in PRODUCTION or AUTO mode. A `PRODUCT_REVIEW` decision remains `PENDING_REVIEW`.

### Step 5 — Compare the Results

You have now tested Ticket #9 before and after reversing the automation rule.

With the temporary rule from **Exercise 1**:

```text id="f5r8qa"
Feature Request
      ↓
AUTOMATED_RESPONSE
```

The results were:

```text id="z7m3hc"
SAFE
   ↓
PENDING_REVIEW
```

and:

```text id="k9v4wd"
PRODUCTION
   ↓
DONE
```

After reversing the rule in **Exercise 2**:

```text id="b6t2xe"
Feature Request
      ↓
PRODUCT_REVIEW
```

The results are:

```text id="u3j8rp"
SAFE
   ↓
PENDING_REVIEW
```

and:

```text id="c5n1mk"
PRODUCTION
   ↓
PENDING_REVIEW
```

This comparison demonstrates something important:

**The LoopZero mode did not change the AI decision.**

The code change in Exercise 1 changed the AI decision from `PRODUCT_REVIEW` to `AUTOMATED_RESPONSE`.

The mode then determined what happened to that automated decision.

### What This Exercise Demonstrates

You have now completed the full cycle:

```text id="w4q7js"
Change the rule
      ↓
Test the automation
      ↓
Observe the result
      ↓
Reverse the rule
      ↓
Test again
      ↓
Verify the original behavior
```

You have also seen why an automation rule should be **deliberate, narrow, and reversible**.

If an automation rule produces an undesirable result, you should be able to identify the code responsible, restore the previous behavior, and verify that the workflow has returned to its intended state.

**The ability to reverse an automation rule is just as important as the ability to create one.**


---

# Experiment Safely

When experimenting with the code, make **one change at a time**.

A useful workflow is:

```text
Find the function
      ↓
Confirm the code
      ↓
Make one change
      ↓
Save
      ↓
Refresh LoopZero
      ↓
Run AI Triage
      ↓
Review the result
```

If something does not behave as expected, undo your last change and try again.

If you are using Git, you can also use your commit history to return to a previous working version.

## Remember

Changes made through your browser's Developer Tools are temporary.

Changes made to `index.html` in your repository are permanent once you save and commit them.

The goal of these exercises is to help you become comfortable moving between:

```text
LoopZero Workflow
       ↓
Code
       ↓
Rule
       ↓
Ticket
       ↓
Automation Decision
       ↓
Workflow Result
```

Once you understand that relationship, you can begin creating your own rules and experiments rather than simply following the examples provided here.

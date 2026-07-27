## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/43

**Issue title:** Agent session state is not cleared between reviews for the same user #43
**Tier:** [x] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
[In 3–5 sentences, in your own words: what the issue is (not a copy-paste of
the title), what is currently broken or missing, and what a successful fix
would accomplish. Naming the part of the codebase it affects is helpful context.]
When a user submits a review, the agent reviews their submission, generates the result of the review tools, and caches the agent state. However, if a user updates their portfolio and requests a second review, the agent reuses the same results rather than compute a new one. This means that rather than review the newly updated portfolio, the user gets feedback on their previous submission.

**Branch name:** fix/43-agent-state-not-cleared

**Setup confirmation:** [x] App runs locally at localhost:5173

**Cohort ledger:** [x] Issue added to cohort ledger

# "Is this right for me?" Checklist

## Part 1 — Understanding the issue
### Can I explain what this issue is asking for in my own words?
Yes, I believe my 3-5 sentences were suffice enough to explain to anyone about what the problem is, and give them a picture of what should be solved.

### Do I understand which part of the app is affected?
labels: "agent"
relevant files: "agent/memory/session_store.py"

These were given in the issue tab, and gives a general overview on what files I should check and understand before making any changes. 

### Do I understand what "done" looks like?

Currently, when the user submits a review and gets feedback on it, the session is saved. However, when the user submits a second review, the agent reuses the same feedback from the first review.

For this issue to be considered "resolved", the agent must be able to reset their session for each independent review under the same user. What this means is that for the first review, the agent creates a session state with its responses. For the second review, the agent must be able to clear the previous session state and generate a new response for the updated review.

## Part 2 — Tier Fit
Because this is my first open source contribution, I'm choosing Tier 1 to learn the basics and understand the whole workflow before moving on.

## Part 3 — Codebase Readiness
### Can I find the relevant code?
The relevant files given was "agent/memory/session_store.py". Given here, I retraced the code to see what files called this function, and found "orchestrator.py" utilized ".get" and '.update". I utilized Claude to help me find where these function methods were used.
### Do I understand the surrounding code well enough to change it safely?
Having traced the relevant files to where it is used throughout the project, I believe I understand the surrounding code well enough to make sure that any changes made only impact the files that used the function.

### Have I read the relevant test file?
I took a look at "tests/unit/", but were unable to find a test file for my issue. I'll most likely produce a test file using Claude as I proceed with the isuse to make sure that my changes fixed the issue or not.

## Part 4 — Scope and Time
### How many others are already working on this issue?
There are 23 listed on the ledger, making me the 24th. Since it's my first open source contribution, I'm fine with this count.
### Is the scope realistic for Weeks 8–9?
Since its Tier 1, I believe it's feasible to complete before Week 9.
### Are there any blockers or dependencies?
No open blockers or dependencies.

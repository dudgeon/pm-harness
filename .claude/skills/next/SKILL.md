---
name: next
description: Suggest options for moving the project forward. Use when the user asks "what's next", "what should we do", "where are we", or otherwise wants direction on how to progress the project.
---

# /next

Give the user a small set of good options for moving the project forward. This is not an
exhaustive status report.

## Read the state

Read the vision, `open-questions.md`, `decisions.md`, and each goal that isn't `done` or `dropped`
(its `goal.md` and `tasks.md`). Also check the inbox, and the last few entries in the wiki log.

Judge how well-defined the project is:
- how many goals are `draft` and how many are `active`;
- whether definitions of done exist;
- how firm the constraints are;
- whether the load-bearing claims are grounded or still hypotheses.

## Shape the options

Offer **3 to 5 options**, ranked. For each, give one line on what it is, one line on why now, and
roughly how big it is.

How much initiative to take depends on how well-defined the project is:

- **Vague:** most options should be *shaping moves*. Examples:
  - sharpen the vision or a goal;
  - pick between competing directions;
  - test a load-bearing hypothesis;
  - start a goal that's implied but doesn't exist yet;
  - gather priors.
  Phrase them as questions or choices for the user.
- **Taking shape:** mix shaping moves with concrete work on `active` goals, such as unblocking
  tasks, resolving open questions, or producing deliverables.
- **Well-defined:** most options should be concrete work you can carry out yourself. Recommend one.
  If an option is obvious and within your "freely do" bounds, say you'll do it unless the user
  redirects you.

Always surface anything that's **blocking**: a blocking open question, an invalidated hypothesis
that something still rests on, or a red deliverables ladder. Mention waiting inbox items or a stale
lint in one line; don't list them as options.

Finish with a recommendation. Once the user picks an option, do it.

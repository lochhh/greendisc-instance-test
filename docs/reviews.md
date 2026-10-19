# Running reviews

Green DiSC asks for evidence that's kept up to date, not a one-off snapshot. The toolkit organises this as **review cycles**: the period leading up to a review meeting, usually every few months. Each cycle is a GitHub milestone whose due date is the meeting date.

## Starting a cycle

The Green DiSC representative starts each cycle, usually at the end of the previous review meeting:

1. Agree the date of the next review meeting.
2. Go to **Actions → Start Green DiSC review → Run workflow**.
3. Enter the meeting date as `YYYY-MM-DD` (e.g. `2026-12-10`). The cycle is named `Review-<year>-<month>` of that date; type a different name if you prefer, without spaces (GitHub's milestone links break on them, so they're replaced with hyphens).
4. Click **Run workflow**.

From the command line: `gh workflow run review.yml -f due=2026-12-10`.

Only people with the **Maintain** or **Admin** role can start a review; for anyone else the run stops with an error and creates nothing.

## What it creates

- **A milestone** for the cycle, due on the meeting date. Its progress bar shows how much of the review is done.
- **A review issue** (label `review`) with a checklist of the criteria for the tiers in `config.yml` (`tiers`, `[Bronze]` by default). It links the criteria upstream and the previous cycle's review issue, so you can follow the reviews back.
- **A check-in for each member** who has a personal record, assigned to them. Whoever starts the review gets the representative's version. A check-in has two items:
  - **your personal record:** check everything is up to date, then comment `/save`;
  - **the group record:** check everything is up to date, adding anything new since the last review. The representative also reviews members' additions and comments `/save`.

  Saving a record ticks its line, and the check-in closes by itself once its record lines are ticked. Saving an unchanged record counts: it shows the record was looked at. The group-record reminder isn't tracked, since most people won't have anything to add.
- **A criteria sync**, which opens a pull request if Green DiSC's criteria changed since the last cycle. Merge it before the meeting, and check the linked upstream changes for anything that affects your evidence.

It also **closes the previous cycle**: any of its issues still open are closed with a link to the new review issue or check-ins, then its milestone is closed. The run's summary (open the run under **Actions**) lists what was created and any records with unsaved changes.

If a run fails part-way, run it again with the same date: it only adds what's missing.

## Before the meeting

- Open check-ins in the milestone show who hasn't gone over their record yet.
- The issue search `is:issue label:"unsaved changes"` finds records edited but not saved.
- The [guides](../guides/README.md) linked from the README's *Where the evidence lives* table should still be accurate.

## At the meeting

Go through the review issue's checklist. For each criterion, check its evidence (the README's *Where the evidence lives* table says where), note anything to follow up in a comment, and tick it off. Close the review issue when you're done, then agree the next meeting date and start the next cycle.

Closed milestones, with their review issues and check-ins, are the record of past reviews.

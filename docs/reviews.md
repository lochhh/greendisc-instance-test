# Running reviews

Green DiSC asks for evidence that's kept up to date, not a one-off snapshot. The toolkit organises this as **review cycles**: the period leading up to a review meeting, usually every few months. Each cycle is a GitHub milestone whose due date is the meeting date.

## Starting a cycle

The Green DiSC representative starts each cycle, usually at the end of the previous review meeting:

1. Agree the date of the next review meeting.
2. Go to **Actions → Start Green DiSC review → Run workflow**.
3. Enter the meeting date as `YYYY-MM-DD` (e.g. `2026-12-10`). The cycle is named `Review <year>-<month>` of that date; type a different name if you prefer.
4. Click **Run workflow**.

From the command line: `gh workflow run review.yml -f due=2026-12-10`.

Only people with the **Maintain** or **Admin** role can start a review; for anyone else the run stops with an error and creates nothing. `config.yml` must name the representative first (see [setup](setup.md#4-fill-in-configyml-and-sync-the-criteria)).

## What it creates

- **A milestone** for the cycle, due on the meeting date. Its progress bar shows how much of the review is done.
- **One issue per criterion** for the tiers in `config.yml` (`tiers`, `[Bronze]` by default), labelled e.g. `criterion:RG-01-B`. Each links the criterion upstream and the previous cycle's issue for the same criterion, so you can follow a criterion's history from one review to the next.
- **A check-in for each member** who has a personal record, assigned to them, plus one for the representative. A check-in is a to-do list:
  - go over your own record and comment `/save` when it's complete and up to date;
  - add anything the group did since the last review to the group record;
  - for the representative only: once members have added their rows, check the group record and comment `/save` on it.

  Saving a record ticks its line, and the check-in closes by itself once its record lines are ticked. Saving an unchanged record counts: it shows the record was looked at. The group-record reminder isn't tracked, since most people won't have anything to add.
- **A criteria sync**, which opens a pull request if Green DiSC's criteria changed since the last cycle. Merge it before the meeting, and check the linked upstream changes for anything that affects your evidence.

It also **closes the previous cycle**: any of its issues still open are closed with a link to their replacement, then its milestone is closed. The run's summary (open the run under **Actions**) lists what was created and any records with unsaved changes.

If a run fails part-way, run it again with the same date: it only adds what's missing.

## Before the meeting

- Open check-ins in the milestone show who hasn't gone over their record yet.
- The issue search `is:issue label:"unsaved changes"` finds records edited but not saved.
- The [guides](../guides/README.md) linked from the README's *Where the evidence lives* table should still be accurate.

## At the meeting

Go through the criterion issues. For each one, check its evidence (the README's *Where the evidence lives* table says where), note anything to follow up in a comment, and close the issue when the evidence is ready. Then agree the next meeting date and start the next cycle.

Closed milestones, with their criterion issues and check-ins, are the record of past reviews.

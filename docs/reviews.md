# Running reviews

Green DiSC asks for evidence that's kept up to date, not a one-off snapshot. The toolkit organises this as **review cycles**: the period leading up to a review, usually every few months. Each cycle is a GitHub milestone whose due date is the review date.

## Starting a cycle

The Green DiSC representative starts each cycle, usually right after finishing the previous one:

1. Decide when the review should be done by.
2. Go to **Actions → Start Green DiSC review → Run workflow**.
3. Enter that date as `YYYY-MM-DD` (e.g. `2026-12-10`). The cycle is named `Review-<year>-<month>` of that date; type a different name if you prefer, without spaces (GitHub's milestone links break on them, so they're replaced with hyphens).
4. Click **Run workflow**.

Alternatively, with the [GitHub CLI](https://cli.github.com/): `gh workflow run review.yml -f due=2026-12-10` (add `-f name=...` for a different name).

Only people with the **Maintain** or **Admin** role can start a review; for anyone else the run stops with an error and creates nothing.

## What it creates

- **A milestone** for the cycle, due on the review date. Its progress bar shows how many check-ins are done.
- **The group record**, if there isn't one yet, assigned to whoever starts the review.
- **A personal record for each member who doesn't have one yet**: everyone with the **Write** or **Maintain** role, and whoever starts the review. Admins, who in an organisation are often owners outside the group, don't get one unless they start the review. A closed record is never recreated, so close the record of anyone who doesn't need one, and reopen it if they rejoin or it was closed by mistake.
- **A check-in for each member** with a personal record, assigned to them:
  - **your personal record:** check everything is up to date, then comment `/save`;
  - **the group record:** check everything is up to date;
  - **the guides:** read them, suggest anything new or outdated by editing the page on GitHub and choosing to start a pull request, and review other people's pull requests. Anyone with Write access can approve and merge them.

  Saving your record ticks its line and closes your check-in. Saving an unchanged record counts: it shows the record was looked at.
- **The representative's check-in**, assigned to whoever starts the review. It covers their own record, and also asks them to:
  - review members' changes to the group record and comment `/save` on it;
  - check the guides are up to date, and that no pull requests are left waiting;
  - check the README's *Your Green DiSC representative* section, and that its *Where the evidence lives* table still matches the criteria;
  - if Green DiSC's criteria changed, check the upstream changes and merge the criteria sync pull request (this item only appears when there is one);
  - if saved rows belong to records that no longer exist (for example, a deleted record), delete those rows by hand or move the items into the owner's record (this item only appears when there are any; see [the CSV files](records.md#the-csv-files)).

  Saving a record ticks its line; the representative ticks the rest and closes the check-in when they're done.
- **A criteria sync**, run first, which opens a pull request if Green DiSC's criteria changed since the last cycle. Check the linked upstream changes for anything that affects your evidence before merging it. If the sync fails, the review still starts.

It also **closes the previous cycle**: any of its check-ins still open are closed, then its milestone is closed. The run's summary (open the run under **Actions**) lists what was created and any records with unsaved changes.

If a run fails part-way, run it again with the same date: it only adds what's missing.

## Finishing a review

- Open check-ins in the milestone show who hasn't gone over their record yet.
- The issue search `is:issue label:"unsaved changes"` finds records edited but not saved.
- Open pull requests show suggested changes to the guides.

Once everything on their check-in is done, the representative closes it and starts the next cycle. Some groups like to go through the criteria together at a meeting, using the README's *Where the evidence lives* table; that's optional. Note anything to follow up as a comment on the representative's check-in.

Closed milestones, with their check-ins, are the record of past reviews.

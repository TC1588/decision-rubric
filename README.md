# decision-rubric

A verdict framework for a live ad account, so a daily review produces decisions instead of a status update.

## Why a rubric and not a dashboard

A dashboard tells you what happened. Someone still has to decide what to do about it, and if that decision gets made by looking, it gets made differently on a Tuesday than on a Friday.

Write the decision down as rules with numbers in them. Then the argument is about the rule, which is a useful argument, instead of about the judgment, which is not.

**Lead the output with anomalies, never with totals.** A briefing that opens with spend and impressions is a status report. One that opens with the three campaigns whose state changed is triage. Same data, different product.

## The four verdicts, plus two terminal states

| Verdict | Trigger |
|---|---|
| SCALE | Cost per click and click-through clearly better than the account average, and improving |
| HOLD | Steady against the prior window |
| DECIDE | Any metric deteriorates more than 20% against the prior window, or budget swings more than 50% day over day |
| KILL | Cost per click above twice the account average at material spend, or click-through under 1% on a traffic objective above the materiality floor |
| ENDED | Flight complete |
| DORMANT | Live but not delivering |

Three things about that table matter more than the numbers in it.

**Triggers are account-relative, not absolute.** Twice the account average, never a fixed cost per click. An absolute threshold is a claim about every account in the world and it will be wrong about yours inside a quarter. The account's own average is the only benchmark that stays true as the mix changes.

**A budget swing is a trigger by itself.** A large day-over-day budget change surfaces a campaign even when its performance looks fine. This rule exists because of one specific failure: a campaign took a roughly 96% budget cut while running at a very low cost per click at scale. Nothing in the performance data would have flagged it. It was a decision someone made quietly and nobody revisited.

**Every verdict prints its arithmetic underneath it.** Not a verdict and a color, a verdict and the comparison that produced it. A recommendation you cannot argue with is a recommendation nobody trusts, and the first time one is wrong without showing its work, the whole rubric is dead.

## Goal-aware judging, and the order the tests run in

This is what takes a rubric from naive to usable. **A campaign is judged on the metric its objective earns, not on one house metric applied to everything.**

| Objective | Judged on | Why the default would be wrong |
|---|---|---|
| Subscribers | Cost per subscriber | Ranks terribly on cost per view while doing its job well |
| Followers, engagement | CPM | Books no clicks by design, so a click-through rule kills it for performing as bought |
| Video | Cost per view | Click-through is not what was bought |
| Search | Exempt from the social cost-per-click ratio | Different auction, different economics |
| Conversions | Cost per conversion | A click is not the outcome |
| Direct-to-consumer | Never killed on click-through alone | Low volume, high intent |
| Traffic | Cost per click and click-through | The default, and only the default |

**Order the tests and put the narrowest first.** The subscriber test has to run before the video test, because a campaign named something like "YouTube | Subscribers" matches the video test too, and otherwise the wrong test wins on position alone.

**The finding that forced this.** Two campaigns ranked worst on the entire account by cost per view. On cost per subscriber they were second and third best. The rubric had been telling the truth about a metric nobody had bought.

## Classify by objective, not by name

The first version read a campaign's purpose out of its name. Names are written by people in a hurry.

Read the platform's own objective field. Keep the name as a fallback, never as the primary key.

The case that broke the name rule: a conversion-optimized campaign carrying no identifying token in its name, dropped silently by the name match and missing from the category it belonged to. Once the classifier read objectives, that category got bigger and its efficiency metric got worse, because the campaign it had been missing was the expensive one.

**Publish the worse number.** A correction process that only ever improves your metrics is not a correction process, it is a ratchet, and everyone can tell.

Check every platform, never assume the miss is isolated. Of three checked in that pass, one was wrong and two were fine, which is only knowable by checking.

## Four checks a window comparison cannot see

A seven-day-against-seven-day comparison is blind to state changes that do not show up as a rate moving. These are separate checks.

1. **Restarted after going dark.** A campaign that was off and is now on.
2. **Cost regime shift** against a longer baseline, 21 days, not 7. A gradual drift never trips a week-over-week rule.
3. **Budget step change** above 50%, in either direction.
4. **Flights expiring inside 10 days**, so a lapse is a decision instead of an accident.

All four were found by hand in a manual audit, then written into the loop. **That is the general move: anything you caught by reading, and would not have caught by rule, becomes a rule.**

## Versioning, and keeping two surfaces apart

Thresholds are declared and dated in code, and treated as tunable. A rubric nobody has changed is a rubric nobody is using.

Keep the live surface and the reconciled record apart, and say so on the page itself. A board that queries at the moment it opens is the place to watch movement and the wrong place to quote from. A dated reconciliation is the opposite. **The two surfaces never claim each other's job**, and writing that sentence on the live board is what stops a number walking out of it into a deck.

Blank version in [RUBRIC.md](RUBRIC.md).

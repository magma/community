# Review Guide

## Process

All changes must be reviewed publicly (by you or others) before the changes are merged into the repository. Our starting convention is two reviews per Pull Request (PR).

## Familiarity with code

If one or more people know an area of code particularly well, code that affects that area should in most cases get a review from one of them. Ideally the maintainer familiar with the subsystem is also the one accepting the patches.

## Ensuring quality

As a maintainer ensuring quality of contributions and reviews is the primary responsibility. The riskier, more subtle, or more complicated the change, the more careful the review required. When a change needs careful review, use good judgment regarding the quality of reviews. Simple "looks good" comments to non-trivial changes are a good indication of poor quality reviews.

## Emergency fixes

Small changes to fix a recently broken build ("make") or unit integration tests ("make check"), that you believe to be visible to a large number of developers, may be checked in with a looser process of a single review.

Regularly review submitted code in areas where you have expertise. Consider reviewing other code as well.

## Git conventions

**Do not merge commits** that haven’t been reviewed in public.

If you apply a change (yours or another's) then it is your responsibility to handle any resulting problems, especially broken builds and other regressions. If it is someone else's change, then you can ask the original submitter to address it. Regardless, you need to ensure that the problem is fixed in a timely way. The definition of "timely" depends on the severity of the problem.

If a bug is present on master and released branches, fix it on master first, then backport the fix to other branches. Straightforward backports do not require additional review (beyond that for the fix on master).

Feature development should be done only on master.

Keep the authorship of a commit clear by maintaining a correct list of "Signed-off-by"s. If a confusing situation comes up, as it occasionally does, bring it up on the mailing list. If you explain the use of "Signed-off-by:" to a new developer, explain not just how but why, since the intended meaning of "Signed-off-by" is more important than the syntax. As part of your explanation, quote or provide a URL to the [contributing guide](CONTRIBUTING.md#developers-certificate-of-origin).
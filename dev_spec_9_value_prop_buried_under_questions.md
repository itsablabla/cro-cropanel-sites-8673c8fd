# Value prop buried under questions — dev spec
Site: nomadinternet.com · Priority 9 · Medium · Effort: Medium (2-5 days)

## Problem
The hero area leads with qualification questions instead of stating the product's value, delaying message clarity.

## Evidence (from the live site)
> The page's main headline reads “Let's Get You the Right Internet”.
> The page's main headline reads “What Best Describes Your Time on the Road?”.
> The page's main headline reads “How Do You Use the Internet at Home?”.

## Current state
h1: Let's Get You the Right Internet; notes: Hero leads with qualification questions.

## Required change
h1: High-Speed Wireless Internet for Anywhere You Live or Travel; notes: Move questions below a concise value statement.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Move questions below a concise value statement.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_value_prop_buried_under_questions` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

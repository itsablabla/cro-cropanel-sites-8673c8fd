# Headline omits unlimited promise — dev spec
Site: nomadinternet.com · Priority 3 · High · Effort: Low (0.5-2 days)

## Problem
The primary headline fails to mention the unlimited data benefit, leaving a key differentiator unstated above the fold.

## Evidence (from the live site)
> The page's main headline reads “Reliable Internet That Works Anywhere in the U.S”.
> Message_match: promises_missing_from_headline: ["unlimited"]

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; notes: Headline does not mention unlimited data.

## Required change
h1: Reliable Internet That Works Anywhere in the U.S. with Unlimited Data; notes: Add 'unlimited' to headline or hero subcopy.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add 'unlimited' to headline or hero subcopy.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_headline_omits_unlimited_promise` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

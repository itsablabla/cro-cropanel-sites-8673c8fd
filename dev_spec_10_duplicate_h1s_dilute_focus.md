# Duplicate H1s dilute focus — dev spec
Site: nomadinternet.com · Priority 10 · Medium · Effort: Low (0.5-2 days)

## Problem
Multiple H1 headings on the same page fragment the primary message and weaken information scent.

## Evidence (from the live site)
> The page's main headline reads “Reliable Internet That Works Anywhere in the U.S”.
> The page's main headline reads “Internet That Just Works”.
> The page's main headline reads “Let's Get You the Right Internet”.

## Current state
h1: Multiple H1s: Reliable Internet That Works Anywhere in the U.S., Internet That Just Works, Let's Get You the Right Internet; notes: Three different H1s on the same page.

## Required change
h1: Single H1 matching visitor intent; notes: Keep one H1 per page and demote others to H2s.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Keep one H1 per page and demote others to H2s.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_duplicate_h1s_dilute_focus` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

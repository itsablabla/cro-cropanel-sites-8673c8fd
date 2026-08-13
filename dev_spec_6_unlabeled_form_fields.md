# Unlabeled form fields — dev spec
Site: nomadinternet.com · Priority 6 · High · Effort: Low (0.5-2 days)

## Problem
Form fields lack visible labels, so visitors cannot tell what information is required before submitting.

## Evidence (from the live site)
> Form fields on coverage and qualification forms have no visible labels.

## Current state
notes: Fields are unlabeled.

## Required change
notes: Add visible, persistent labels above each input.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add visible, persistent labels above each input.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_unlabeled_form_fields` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

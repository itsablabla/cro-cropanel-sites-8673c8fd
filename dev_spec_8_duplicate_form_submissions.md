# Duplicate form submissions — dev spec
Site: nomadinternet.com · Priority 8 · Medium · Effort: Medium (2-5 days)

## Problem
Two identical CONTINUE forms on the same page create competing submission points and confusion.

## Evidence (from the live site)
> Two identical CONTINUE forms appear on the same page.

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; cta: Two identical CONTINUE forms; notes: Duplicate submission points.

## Required change
h1: Reliable Internet That Works Anywhere in the U.S.; cta: Single CONTINUE form; notes: Remove duplicate form to leave one clear submission path.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Remove duplicate form to leave one clear submission path.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_duplicate_form_submissions` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

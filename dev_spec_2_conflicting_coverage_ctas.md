# Conflicting coverage CTAs — dev spec
Site: nomadinternet.com · Priority 2 · High · Effort: Low (0.5-2 days)

## Problem
Multiple different CTA labels for the same coverage-check action create ambiguity about the next step.

## Evidence (from the live site)
> CHECK COVERAGE
> CHECK IF IT WORKS AT MY ADDRESS
> SEE MY OPTIONS
> SEE WHAT I QUALIFY FOR
> CHECK MY COVERAGE

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; cta: Multiple CTAs: CHECK COVERAGE, CHECK IF IT WORKS AT MY ADDRESS, SEE MY OPTIONS, GET STARTED, START CHAT, SEE WHAT I QUALIFY FOR, CHECK MY COVERAGE; notes: Inconsistent labels for the same action.

## Required change
h1: Reliable Internet That Works Anywhere in the U.S.; cta: Single consistent CTA label, e.g., 'Check Coverage'; notes: Consolidate all coverage-check CTAs into one consistent label and action.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Consolidate all coverage-check CTAs into one consistent label and action.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_conflicting_coverage_ctas` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

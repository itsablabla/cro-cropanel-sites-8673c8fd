# Inconsistent price formatting — dev spec
Site: nomadinternet.com · Priority 7 · High · Effort: Low (0.5-2 days)

## Problem
The same plans display conflicting price formats and values across pages, undermining trust in cost clarity.

## Evidence (from the live site)
> Prices shown on the page: $99.95/month $129.95/month $99.95/Mo $99.95/month $129.95/month $99.95
> Prices shown on the page: $99.95/month $129.95/month $99.95/mo $0.00 $99.95 $99.99
> A section heading reads “$0.00 (one-time)”.

## Current state
notes: Prices shown as $99.95/month, $99.95/Mo, $99.95, $0.00, $99.99, etc.

## Required change
notes: Standardize all price displays to a single format, e.g., $99.95/month, and remove or label $0.00 values.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Standardize all price displays to a single format, e.g., $99.95/month, and remove or label $0.00 values.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_inconsistent_price_formatting` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

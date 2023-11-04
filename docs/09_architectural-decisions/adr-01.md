---
title: ADR-01 Documenting architecture decisions
---

# ADR-01 Documenting architecture decisions

## Context

In an agile project spanning multiple teams over a period of time not all decisions will be made at once nor will all people be in the room when the decision is made.

Nobody reads large documents and even fewer try to document the reason behind a decision into the documentation.

This exposes us to the risk of repeating the same mistakes and evaluations again and again.

## Decision

We will document each and every major decision in this project as an 'Architecture decision record' or short ADR like this one.

When an ADR is accepted it can not be changed. 
If the decision is obsolete the status is marked as such and a new ADR is created to replace it.

This allows us to only read new ADRs to keep track of the updated decisions.

An ADR can have three states:

 - **Draft**: Not yet in effect and subject to change.

 - **Accepted**: Currently in effect and must be adhered to.

 - **Obsolete**: Replaced by a newer ADR and can be ignored.

## Status

Draft

## Consequences

Reduces the time spent reinventing the wheel.

Improves project quality because decisions have to be evaluated and explaned and cant be done at a whim.

More time used on decisions because of the additional documentation effort needed.
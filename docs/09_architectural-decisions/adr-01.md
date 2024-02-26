---
title: ADR-01 Backend Go testing
---

# Backend Go testing

## Status - Accepted 🟢

## Context

Our backend is compromised out of different submodules.
We need a strategy to minimize time to identify and fix software bugs.

## Decision

We create a test file for each file in our code. 

We use the standard file ending of '_test.go' for the test file as it is described in [the official tutorial](https://go.dev/doc/tutorial/add-a-test).

## Consequences

Finding bugs earlier in the development lifecycle.

More time used per function because of the tests that have to be written for it.
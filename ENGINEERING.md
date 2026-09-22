# How I approach engineering

## Establish what actually happened

External actions move through different states: requested, submitted, acknowledged, and confirmed. I design workflow records and operator views around those distinctions. Ambiguous outcomes need investigation and reconciliation before retry.

## Give shared state a clear owner

Talon's State service owns durable writes. Aegis has one order-capable component. VolaPilot uses a shared execution lock. Each boundary reduces the number of places that can initiate conflicting actions.

## Bound work under pressure

Queues, retained history, log buffers, and recovery attempts need limits. Those limits should be visible through diagnostics so operators can distinguish normal load from degradation.

## Measure the affected path

A scanner calculation benchmark says something about the scanner calculation. It does not establish end-to-end broker speed. I keep timing definitions, comparison baselines, and known limits attached to performance results.

## Make recovery part of the design

Connection loss, process restarts, incomplete writes, stale observations, and uncertain broker responses are normal engineering cases. Durable intent records, replayable evidence, bounded retries, and rollback paths make them manageable.

## Separate research from execution

Research outputs need reproducible data, explicit evaluation criteria, and a release decision. Aegis demonstrates rejection as a useful system outcome. VolaPilot distinguishes historical entry evidence from claims about future performance.

## Use AI tools with verification

I use AI-assisted development to explore implementation approaches, review code, and investigate failures. The engineering work remains grounded in source inspection, tests, logs, reproducible comparisons, and explicit release boundaries.

[Back to portfolio](README.md)

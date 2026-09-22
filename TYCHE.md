# Tyche

**Python runtime engineering for responsive, long-running automation**  
Python · asyncio · uvloop · websockets · Patchright · Linux · AWS EC2 · systemd

Tyche is the Python runtime behind the architecture that later evolved into Talon. It combines external event streams, browser sessions, account state, transaction workflows, and remote operator controls. The optimized runtime focuses on predictable latency and bounded resource use.

## The problem

Long-running automation can fail gradually: queues grow, noisy logging consumes resources, browser work delays event handling, and a poorly supervised task loop burns CPU. Reliable performance requires identifying where time and memory are spent.

## Engineering work

- Isolated same-site WebSocket reception and transmission in supervised workers using modern `websockets.asyncio` and a shared event loop.
- Introduced bounded receive/write queues and same-loop broadcast to ready accounts.
- Corrected a completed-task supervisor loop that could continuously consume one CPU core.
- Made JSON replacement crash-safe and supported backup recovery when the primary file was missing or corrupt.
- Moved strategy persistence to a bounded, batched writer with retry and shutdown draining.
- Bounded asynchronous logging, with dropped-record counters making overload visible.
- Preserved active withdrawal attempts while limiting terminal history growth.
- Added dispatch-to-wire timing, event-loop lag, thread/file-descriptor counts, process memory, and database/logging pressure measurements.
- Added locked dependencies, regression tests, systemd watchdog configuration, migration guidance, and a read-only deployment verifier.

## Design tradeoffs

The optimized candidate provides a legacy-engine rollback switch. Experimental transport and host-level tuning remain disabled unless comparative measurements justify them. This makes an optimization reversible and keeps protocol correctness part of the acceptance criteria.

The RFC 6455 framing work also addresses client masking: each raw frame must receive a fresh mask. Faster transport is useful only when the protocol remains correct.

## Evidence and status

The local optimized candidate includes architecture notes, migration documentation, a test suite, and a benchmark tool. Tyche also appears in Talon's sealed historical baseline. This overview does not treat every local candidate as a deployed release or attach an unverified speedup to the optimization work.

## What this project demonstrates

Python concurrency, event-loop diagnosis, backpressure, resource measurement, crash recovery, durable file handling, long-running service operations, and incremental architectural migration.

[Back to portfolio](README.md)

# Architecture Overview

## Signal Flow

```mermaid
flowchart TD
    A[TradingView Alerts] --> B[Python Router]
    B --> C[Signal Validation]
    C --> D[Strategy Dispatch]
    D --> E[Pre-Trade Filters]
    E --> F[Risk Engine]
    F --> G[Execution Routing]
    G --> H[Telemetry & Logging]
    H --> I[Analytics & Research]
```

## Design Goals

- Decouple strategy logic from execution infrastructure.
- Keep risk controls independent from signal generation.
- Make operational failures visible through telemetry.
- Separate live and simulation analytics.
- Preserve reproducible event histories for research.

## Operational Telemetry

The infrastructure logs:

- signal validation failures
- filter rejections
- safemode/circuit-breaker activations
- execution outcomes
- EV statistics
- routing decisions
- latency and operational events

The goal is observability rather than opacity.

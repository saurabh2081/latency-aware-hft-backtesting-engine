# Latency-Aware HFT Backtesting & Execution Engine

A high-performance quantitative framework engineered for **high-frequency trading (HFT)**, **market making**, and **algorithmic execution**. Built with a high-throughput **Rust** core and **Python (Numba JIT)** research bindings, this engine addresses the primary failure mode of standard backtesters: **unrealistic fill and latency assumptions**.

---

## Key Highlights

- **Realistic Latency Simulation**: Accurately models both feed arrival and order transit latencies (network and exchange matching engine delays) using empirical latency distributions or custom statistical models.
- **Queue-Aware Fill Modeling**: Simulates exact queue priority and order positions within the order book to prevent optimistic fill assumptions.
- **Full Order Book Reconstruction**: Supports tick-by-tick simulation from Level-2 (Market-By-Price) and Level-3 (Market-By-Order) depth feeds.
- **Dual Research & Production Flow**:
  - **Python (Numba JIT)**: Ultra-fast backtesting iterations and alpha research with JIT compilation.
  - **Rust Native**: High-throughput execution and live trading connector integration using identical algorithmic logic.
- **Live Trading Connectors**: Native connectors for cryptocurrency derivatives venues (Binance Futures, Bybit).
- **Multi-Asset & Multi-Exchange**: Built-in support for cross-venue arbitrage, basis trading, and multi-instrument delta hedging.

---

## Architecture Overview

```text
latency-aware-hft-backtesting-engine/
├── hftbacktest/          # Core Rust engine (order books, latency models, event loop)
├── py-hftbacktest/       # Python / Numba bindings for strategy research
├── connector/            # Live execution connectors (Binance Futures, Bybit)
├── collector/            # Tick and order book market data collection service
├── examples/             # Production & research Jupyter notebooks
└── docs/                 # Detailed documentation and tutorials
```

---

## Strategy Examples & Tutorials

The [`examples/`](examples) directory contains detailed implementations and research notebooks:

- **Grid & Market Making**: High-frequency grid trading derived from Guéant-Tapia-Manziadi (GLFT).
- **Alpha & Order Flow**: Market making conditioned on Order Book Imbalance (OBI) and Arbitrage Pricing Theory (APT).
- **Microstructure Mechanics**: Queue-based market making in large tick size assets.
- **Latency Impact Studies**: Analyzing strategy sensitivity to network jitter and execution delays.

---

## Quickstart (Python)

### Requirements

- Python 3.11+
- Rust toolchain (`cargo`, `rustc`) for building native extensions

---

## Rust Core Usage

Build the core workspace:

```bash
cargo build --release
```

Run test suite:

```bash
cargo test --workspace
```


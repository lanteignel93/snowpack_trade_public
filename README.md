# VIX Curve Relative Value (Level-Neutral)

> [!NOTE]
> **This is the public showcase repository.** To request access to the private, full-source repository, please email [laurent.lanteigne@gmail.com](mailto:laurent.lanteigne@gmail.com).

[![Python 3.10+](https://img.shields.io/badge/python-3.10%2B-blue)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Short the 30-day constant-maturity VIX future against a minimum-norm long basket across
60-180 days, weighted orthogonal to the curve's level factor (~97% of variance);
re-derived every five sessions; always on. The harvest is the curve's SHAPE premium —
roll-down and curvature — not a vol-direction bet.

## The card (2016-05 -> 2025-11, in-sample)

| | |
|---|---|
| Sharpe (base book) | **1.56** (ann ~31% at ~20% vol) |
| skew / kurtosis | +0.9 / 31 — positive skew: higher-moment adjustments barely dent it |
| crash behavior | profitable through 2018, 2020, Aug-2024, Apr-2025 |
| the failure mode | low-VIX steep-contango grinds: -31% over 2016-12 -> 2018-05 |
| costs (assumption tiers) | net ~1.45 / 1.29 / 1.04 across spread tiers |

A previously advertised sizing overlay was retired after an alignment repair (its edge
was an artifact); the base book is the card. Carry attribution on the tradable weights:
carry is ~3.3x the total P&L with shape shocks dragging the difference.

## What's here

- `strategy_results.ipynb` — executed results: performance, the carry-vs-shock
  attribution, and a bootstrap luck check (luck band + zero-edge null). Reproduces
  from the small series in `data/`.

## What stays private

The weight construction and window provenance, the rejected-knob research (vol
targeting, carry sizing, state machines), cost/capacity studies.

*Enough to evaluate the strategy; not enough to replicate it.*

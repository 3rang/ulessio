<!--
SPDX-License-Identifier: Apache-2.0
Copyright 2026 Tarang Patel
-->

# Ulessio

Ultra-lightweight, zero-heap, single-header C library for streaming data
segmentation and reconstruction on MCUs and embedded systems.

> Small buffers. Large streams. No heap.

## Purpose

Ulessio splits large anonymous byte streams into segments and reconstructs
them reliably on resource-constrained devices. A motivating example is
retaining an industrial Edge AI device's sensor recording around an anomaly
and transferring it through small buffers for engineering review or model
improvement.

Ulessio handles stream segmentation and reconstruction only. It is not an
AI/inference library, a recording or filesystem layer, a compression or
network/transport library, a persistence/recovery framework, or an
authentication or driver layer. Integrity checks, where present, can detect
accidental corruption but do not authenticate data.

## Development status

**Early scaffold.** This directory currently contains project packaging
only: license, this README, and a single-header skeleton with no public
API yet. There is no segmentation or reconstruction behavior implemented.
Do not use this for any real workload yet.

Development proceeds in small, reviewed increments, with design discussed
before implementation.

## Layout

```text
README.md   - this file
LICENSE     - Apache License, Version 2.0 (standard text)
ulessio.h   - single-header library (currently scaffold only)
```

Ulessio follows the single-header library pattern: all declarations and
implementation live in `ulessio.h`. Include the header normally to get
declarations; in exactly one translation unit, define
`ULESSIO_IMPLEMENTATION` before including the header to also compile the
implementation. Example programs and tests, once added, will be separate
`.c` files alongside the header.

## Requirements (planned)

- C99
- No heap allocation
- No OS or filesystem dependency
- Caller-owned buffers and state

None of the above are verified yet, since no functional code exists.

## Next step

Discuss and agree the contract for the first function (a bounded byte-copy
operation with mismatched input/output sizes) before implementing it.

## License

Apache License, Version 2.0. See [LICENSE](LICENSE).

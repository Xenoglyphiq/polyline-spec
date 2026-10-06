# Polyline — Decisions

Spec-level decisions. Newest at the bottom. Status is **Accepted** unless noted. Port-only idiom choices go in that port's own README, not here.

### D-001 — 64-bit integers throughout
**Status:** Proposed
**Decision:** Scaled values, deltas, running sums and decoded values are all `i64`. Anything outside that range is `polyline.overflow`, never a silent wraparound or a crash.
**Why:** Precision 10 at ±180° is 1.8e12, which doesn't fit 32 bits. Some older implementations use 32-bit accumulators and break at precision 6 and above.
**Affects:** spec §3 `encode` and `decode`, A3 and A4; overflow fixtures; all ports.
**Revisit if:** precision above 10 is ever allowed.

### D-002 — Round with the family rule, not the oracle's helper
**Status:** Proposed
**Decision:** Exact halves round away from zero, per `.kit/CONVENTIONS.md` §1. The oracle does too, through `floor(abs(x) + 0.5)`. That helper gets one input class wrong: when `abs(x)` is just below a half, such as `0.49999999999999994`, adding `0.5` rounds up to `1.0`. The spec follows the rule, not the helper. The fixture for that case is written by hand (`source: "spec"`).
**Why:** The rule has to be the same in every language. Copying the oracle's floating-point accident would force every port to reproduce it.
**Affects:** spec §3 `encode` step 3, A1; fixture `encode.near_tie_below`; all ports.
**Revisit if:** the oracle changes its rounding.

### D-003 — The oracle covers valid input only
**Status:** Proposed
**Decision:** Python `polyline==2.0.4` generates fixtures for valid input. Every error case, plus `encode([])` (which the oracle crashes on), is written by hand from this spec and marked `source: "spec"`.
**Why:** The oracle doesn't validate characters, truncation or ranges. It raises `IndexError` or returns garbage instead.
**Affects:** `conformance/`, spec §6.
**Revisit if:** a maintained implementation with full validation appears and agrees with this spec.

### D-004 — Lenient decode, canonical encode
**Status:** Proposed
**Decision:** `decode` accepts overlong values (extra zero chunks), up to 13 chunks per value. `encode` always writes the shortest form.
**Why:** It matches the oracle and other common decoders. Rejecting overlong values would break round-trips through other tools for no safety gain, because the 13-chunk cap still bounds the work.
**Affects:** spec §3 `decode`, A11.
**Revisit if:** a real-world producer is found that relies on rejection.

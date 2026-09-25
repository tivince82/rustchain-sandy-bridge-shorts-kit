# Verification Sources & Code References

Every technical claim, multiplier, and mechanism in this distribution package traces directly to verifiable, open-source code in `Scottcjn/Rustchain`:

---

### 1. Consensus & Multiplier Table (`node/rip_200_round_robin_1cpu1vote.py`)
- **Consensus Model**: Deterministic Round-Robin (**1 CPU = 1 Vote**, Lines 1–10). Replaces hash-rate races; each attested CPU receives equal block production turns without difficulty targets or mining farms.
- **Antiquity Multiplier Table (`ANTIQUITY_MULTIPLIERS`, Lines 163–468)**:
  - **PowerPC G4 (2001-2004)**: `"g4": 2.5` (Line 371)
  - **Intel Sandy Bridge (2011)**: `"sandy_bridge": 1.1` (Line 388)
  - **Modern Intel (2020-2025)**: `"modern_intel": 0.8` (Line 410)
  - **Modern AMD (2020-2025)**: `"modern_amd": 0.8` (Line 425)
- **Time-Decay Law (Lines 471, 503–506)**:
  - `DECAY_RATE_PER_YEAR = 0.15` (Line 471)
  - Formula:
    ```python
    vintage_bonus = base_multiplier - 1.0  # e.g., G4: 2.5 - 1.0 = 1.5
    aged_bonus = max(0, vintage_bonus * (1 - DECAY_RATE_PER_YEAR * chain_age_years))
    final_multiplier = 1.0 + aged_bonus
    ```
  - The vintage bonus decays at 15% per blockchain year, transitioning smoothly to 1.0x as the chain matures.

---

### 2. Physical Sybil & Anti-Emulation Defense (`miners/linux/fingerprint_checks.py`)
RustChain enforces 1 CPU = 1 Vote and prevents cloud/VM farm exploitation through 6 hardware attestation entropy measurements:
1. `Clock-Skew & Oscillator Drift` (`clock_drift`): Measures hardware quartz oscillator timing deviations.
2. `Cache Timing Fingerprint` (`cache_timing`): L1/L2/L3 access latency ratios reflecting true physical silicon cache hierarchies.
3. `SIMD Unit Identity` (`simd_identity`): Real execution vector unit verification (`has_sse`, `has_avx`, `has_altivec`).
4. `Thermal Drift Entropy` (`thermal_drift`): Temperature-induced cycle drift under load (`drift_ratio`).
5. `Instruction Path Jitter` (`instruction_jitter`): Sub-nanosecond hardware branch and integer execution variance.
6. `Anti-Emulation Checks` (`anti_emulation`): Hypervisor, VM artifact, and synthetic clock detection (`is_likely_vm: false`).

---

### 3. Layer 2 Bridge Invariants & Reconciliation
- **PR #8517**: `https://github.com/Scottcjn/Rustchain/pull/8517`
- **Reconciliation Invariant**: Prevents double-subtraction of voided transfers in committed supply accounting (`committed_supply_urtc`).

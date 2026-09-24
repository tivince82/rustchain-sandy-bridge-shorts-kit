# Verification Sources & Code References

Every technical claim in this distribution package is grounded in the public open-source codebase of RustChain:

1. **Proof-of-Antiquity Difficulty Multiplier**:
   - Repository: `https://github.com/Scottcjn/Rustchain`
   - Specification: `HARDWARE_TARGET_SPEC.md`
   - Calculation:
     $$\alpha(\text{age}) = 1.0 + (2026 - \text{release\_year}) \times 0.15$$
     $$\beta(\text{cores}) = \frac{1.0}{1.0 + 0.1 \times \max(0, \text{cores} - 2)}$$
   - Sandy Bridge (2011, 4 cores):
     $$\alpha = 1.0 + (15 \times 0.15) = 3.25$$
     $$\beta = \frac{1.0}{1.0 + 0.2} = 0.833$$
     $$\text{Combined Factor} = 3.25 \times 0.833 = 2.708\times$$

2. **Telemetry Verification & Jitter Defense**:
   - Reference Issue: `https://github.com/Scottcjn/rustchain-bounties/issues/71`
   - Hardware QA Attestation: `https://github.com/Scottcjn/rustchain-bounties/issues/2784`
   - Real hardware execution verified via `rdtsc` jitter variance checks.

3. **Layer 2 Bridge Invariants**:
   - PR: `https://github.com/Scottcjn/Rustchain/pull/8517`
   - Code: `node/bridge_reconciliation.py`

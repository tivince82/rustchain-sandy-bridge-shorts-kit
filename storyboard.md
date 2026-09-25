# Storyboard & Production Directions

**Target Aspect Ratio**: 9:16 Vertical Video (1080 x 1920)  
**Total Running Time**: 55 seconds  
**Voice Tone**: Engaging, fast-paced, authoritative tech YouTube narrator (similar to Fireship / Linus Tech Tips Shorts).

---

## Scene 1: The Hook (00:00 - 00:06)
- **Framing**: Split-screen vertical cut.
- **Top Shot**: High-end modern liquid-cooled Threadripper server rack.
- **Bottom Shot**: Vintage PowerPC G4 Cube / 2011 Dell OptiPlex running on a desk.
- **Graphic Overlay**: Badge: `VINTAGE MAC > $10K SERVER?`
- **Audio Cue**: Bass drop / record scratch transition.

## Scene 2: The Energy Waste Reality (00:06 - 00:18)
- **Framing**: Full vertical slide with dynamic graphics.
- **Visual**: Industrial ASIC mining containers and a soaring electric meter.
- **Graphic Overlay**: `Traditional PoW: Millions of Joules wasted`.
- **Transitions**: Fast horizontal whoosh transition.

## Scene 3: The 1 CPU = 1 Vote Consensus (00:18 - 00:32)
- **Framing**: Clean code walkthrough of `node/rip_200_round_robin_1cpu1vote.py`.
- **Visual Focus**:
  - Highlights `ANTIQUITY_MULTIPLIERS` table:
    - `"g4": 2.5` (Line 371)
    - `"sandy_bridge": 1.1` (Line 388)
    - `"modern_intel": 0.8` (Line 410)
- **Graphic Overlay**: `No hash race. 1 CPU = 1 Vote.`

## Scene 4: Real Hardware Attestation (00:32 - 00:46)
- **Framing**: 9:16 terminal screen recording (dark mode, 22pt JetBrains Mono).
- **Captured Real Output from `miners/linux/fingerprint_checks.py`**:
  ```bash
  $ python3 miners/linux/fingerprint_checks.py
  Running 6 Hardware Fingerprint Checks...
  [1/6] Clock-Skew & Oscillator Drift... PASS
  [2/6] Cache Timing Fingerprint...       PASS
  [3/6] SIMD Unit Identity...             PASS
  [4/6] Thermal Drift Entropy...          PASS
  [5/6] Instruction Path Jitter...        PASS
  [6/6] Anti-Emulation (No VM)...         PASS
  ==================================================
  OVERALL RESULT: ALL CHECKS PASSED (is_likely_vm: false)
  ```
- **Graphic Overlay**: `Physical Silicon Jitter = Sybil Proof`.

## Scene 5: Outro & Call to Action (00:46 - 00:55)
- **Framing**: Clean browser mockup displaying `https://github.com/Scottcjn/Rustchain`.
- **Text on Screen**: 
  - `RustChain: Resurrecting Old Silicon`
  - `Star & Join: github.com/Scottcjn/Rustchain`
  - Author credit: `Package by @tivince82`
- **Audio Cue**: Upbeat synth swell and celebratory chime.

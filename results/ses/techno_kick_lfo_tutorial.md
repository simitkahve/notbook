# Techno Kick Synthesis with LFO - Complete Tutorial

## 1. Classic Techno Kick Characteristics

A techno kick is defined by three frequency layers working together:

| Layer | Frequency Range | Purpose |
|-------|-----------------|---------|
| **Transient** | 2-6kHz | Click/attack that cuts through dense mixes |
| **Mid-Bass** | 80-120Hz | The "punch" that makes dancers feel it |
| **Sub Bass** | 45-65Hz | The physical rumble foundation |

**Key characteristics:**
- **Pitch envelope**: Fast pitch drop from ~150Hz down to 40-50Hz within 50-100ms
- **Punch**: Aggressive mid-range attack (140-400Hz range carefully sculpted)
- **Mono**: Always mono summed below 200Hz for club systems
- **Dynamics**: Tight attack with sustained decay
- **Length**: 100-300ms typical (harder styles shorter, deeper styles longer)

---

## 2. How to Use LFO on Techno Kicks

### LFO as Pitch Modulator
The most common technique—LFO creates that classic "pitch dive" punch:

- **Depth**: -1 to -2 octaves (from starting note down to ~40Hz)
- **Speed**: Set to "ENV" (envelope-shaped LFO) with fast attack
- **Curve**: Sharp attack (almost instant) followed by gradual decline

### LFO on Filter Cutoff
Creates movement and "sweeping" effect:

- **Target**: Low-pass filter on the oscillator
- **Sync**: Usually not synced to tempo—envelope-driven
- **Depth**: Subtle, 10-30% to avoid obvious warble

### LFO for Punch (Amplitude Modulation)
Gates the sustain portion for extra "thump":

- **Target**: Oscillator level or VCA
- **Timing**: Triggers once per hit, short decay
- **Use case**: Adds weight without changing pitch

### LFO for Distortion/Drive
Dynamic saturation that follows the kick's amplitude:

- **Target**: Drive/ Saturation amount
- **Range**: 65-100% depth
- **Creates**: More aggressive attack, smoother decay

---

## 3. Step-by-Step: Creating a Techno Kick in Serum

### Layer A: Sub Bass (Foundation)
1. **Oscillator A**: Select `Analog_BD_Sin` waveform
2. **Pitch**: Set to -2 octaves (or starting around C1)
3. **Envelope (Pitch)**: 
   - Attack: 0ms
   - Decay: ~80-120ms
   - Pitch drop: -36 to -48 semitones (to ~45Hz)

### Layer B: Mid/Body
4. **Oscillator B**: Select `Distorted_Fwapper_SQ` waveform
5. **Level**: Start at 0 (controlled by LFO)
6. **Pitch**: Same octave as A

### LFO Configuration:

**LFO 1 → OSC A Level**
- Shape: ENV (draw curve)
- Attack: Very short (~5ms)
- Decay: ~100ms
- Range: 0-100%

**LFO 2 → Pitch (OSC A)**
- Shape: ENV
- Start: Top center of grid
- End: Bottom center
- Depth: ~36 semitones
- Creates the characteristic pitch dive

**LFO 3 → OSC B Level + Wavetable Position**
- Shape: ENV (top-left to bottom-right)
- Attack: Fast, decay to near zero
- Adds the "click" transient layer

**LFO 4 → Distortion Drive (FX)**
- Shape: ENV (similar to LFO 3, handle slightly higher)
- Range: 65-100%
- Adds punch and harmonics

### Processing Chain:
1. **Distortion (FX)**: Pre-mode, type: Hard, Drive: ~65
2. **EQ**: Low-shelf at 90Hz, +8.5dB for sub presence
3. **High-shelf**: Subtle boost around 5-8kHz for "crack"

---

## 4. LFO Settings for Different Techno Styles

### Minimal Techno
- **Tempo**: 120-128 BPM
- **Swing**: 6-10%
- **Kick character**: Tight, controlled, less aggressive
- **LFO settings**:
  - Pitch dive: Gentle, -24 semitones max
  - Attack: Slightly slower (10-15ms)
  - Decay: Shorter (~60ms)
  - Filter LFO: Subtle, low depth
  - Distortion: Low (30-40%)

### Hard Techno
- **Tempo**: 140-150 BPM
- **Swing**: 4-8%
- **Kick character**: Aggressive, snappy, distorted
- **LFO settings**:
  - Pitch dive: Extreme, -48 semitones (full octave+)
  - Attack: Instant (0-5ms)
  - Decay: Very short (~40ms)
  - Filter LFO: More pronounced for "wobble"
  - Distortion: High (70-100%), type: Full
  - Adds: Noise layer for texture

### Deep/ melodic Techno
- **Tempo**: 120-126 BPM
- **Swing**: 10-14%
- **Kick character**: Rounder, warmer, longer sustain
- **LFO settings**:
  - Pitch dive: Moderate, -30 semitones
  - Attack: Smooth (15-20ms)
  - Decay: Longer (~150-200ms)
  - Filter LFO: Very subtle for subtle movement
  - Distortion: Low to medium (25-45%), warmth over aggression
  - Add: Reverb/delay for spatial depth

---

## Quick Reference: LFO Modulation Targets

| Target | Effect | Typical Depth |
|--------|--------|---------------|
| **Pitch** | Kick dive, punch | 24-48 semitones |
| **Filter Cutoff** | Tonal sweep | 10-30% |
| **Amplitude** | Thump/gate | 0-100% |
| **Distortion Drive** | Aggressive attack | 65-100% |
| **Wavetable Position** | Harmonic shift | 30-50% |

---

## Pro Tips

1. **Always test in mono** — techno kicks must work on club systems
2. **Phase alignment** — when layering multiple kicks, align transients precisely
3. **Reference tracks** — compare against Charlotte de Witte, Amelie Lens, ANNA
4. **Velocity matters** — automate velocity for energy buildups (5-8 points per 16 bars)
5. **Saturation > compression** — adds warmth and harmonics naturally
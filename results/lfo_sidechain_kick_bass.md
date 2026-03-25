# LFO Sidechain Compression for Kick-Bass: Research Notes

## 1. LFO-Controlled Sidechain

An LFO (Low Frequency Oscillator) can replace traditional sidechain compression to create rhythmic pumping without relying on the kick drum as the trigger source. This is useful when you want the pumping effect but don't have a consistent kick pattern, or when you want independent rhythm from the kick.

### How It Works
- Use an LFO tool (like Xfer Records **LFOTool**, Cableguys **ShaperBox 2**, or native DAW options)
- Draw or select a volume envelope shape that matches your desired rhythm
- The LFO modulates the volume of the target track (typically bass) on a loop
- Unlike traditional sidechain, the rhythm is fixed to the LFO rate, not the kick trigger

### Key Plugins for LFO Sidechain
| Plugin | Best For |
|--------|----------|
| **Xfer Records LFOTool** | Drawing custom LFO shapes, works like Serum's LFO |
| **Cableguys ShaperBox 2** | VolumeShaper module, per-frequency band ducking |
| **Nicky Romero Kickstart** | Simple 4-on-the-floor pumping |
| **Waves OneKnob Pumper** | Single-knob house/techno pumping |
| **Wavesfactory Trackspacer** | Frequency-specific ducking (ducks only the freq band matching sidechain) |

### Basic Setup (Ableton Live)
1. Load Compressor on bass track
2. Enable sidechain input, select kick track as source
3. Set ratio ~4:1 to 6:1
4. Attack: 1-5ms (prevents clicking)
5. Release: 30-80ms (faster = tighter pump, slower = smoother)

---

## 2. Rhythmic Pumping Effects

### Traditional vs LFO Pumping
- **Traditional sidechain**: Ducking follows the kick exactly
- **LFO pumping**: Ducking follows a fixed rhythmic pattern (can be 1/4, 1/8, syncopated)

### Creative Techniques

**Ghost Sidechain**
- Create a separate "ghost kick" that plays the pumping rhythm
- Route it to sidechain input, turn its volume to 0
- Gives pumping without audible kick

**Trance Gate Effect**
- Use **A1TriggerGate** with gate presets
- Creates rhythmic stuttering on any sound

**Multiband Sidechain**
- Apply sidechain only to specific frequency ranges
- Example: duck only the sub-bass (20-80Hz), keep upper bass audible
- Prevents the "underwater" sound

**Automation**
- Automate the threshold or mix amount
- Bring in pumping gradually for build-ups
- Use different patterns for verses vs drops

---

## 3. EQing Kick and Bass Together

### Frequency Allocation
- **Kick main body**: 20Hz – 300Hz
- **Bass should not exceed**: 300Hz (crossover to low mids)
- **Sub-bass**: 20Hz – 60Hz (mono essential)
- **Kick attack/transient**: 2kHz – 5kHz range

### EQ Workflow

**Step 1: Remove excess sub from bass**
- High-pass filter at 30Hz with steep slope (-48dB/oct)
- Most systems can't reproduce below 30Hz cleanly
- Saves headroom and reduces mud

**Step 2: Carve mids from kick**
- Notch filter at 200Hz – 500Hz with tight Q
- Removes "boxiness" that competes with bass
- Keep it subtle: -6dB to -10dB

**Step 3: Add high-end to kick**
- Boost 2kHz – 4kHz with bell curve (+3dB to +6dB)
- Adds punch and definition
- Each kick is different—sweep to find the sweet spot

**Step 4: Sidechain the bass to kick**
- Use soft knee compression
- Ratio 4:1 to 6:1
- Release around 60ms for tight mixes, 150ms for smoother

### Common Kick-Bass Clashes
- **40-80Hz range**: Both kick and bass want this—sidechain or EQ carve
- **200-400Hz**: Muddy area, especially in small rooms
- **800Hz-2kHz**: Kick transient vs bass harmonics—can cause harshness

---

## 4. Workflow Tips

### General Workflow
1. **Start with good sounds**: Don't try to fix a weak kick with extreme EQ
2. **Check in mono**: Kick-bass phase issues hide in stereo
3. **Reference constantly**: Compare to commercial tracks in your genre
4. **Room calibration**: Know your room'sproblem frequencies (play chromatic scale G1 to F3 to identify)

### Sidechain Best Practices
- **Don't overuse**: Too much sidechain makes the mix sound "breathing" unnaturally
- **Use different settings per element**: Don't use identical settings on every track
- **Try different attack/release**: Fast = pump, slow = glue
- **EQ the sidechain input**: High-pass the trigger at 80-100Hz if you want snap without sub rumble

### Quick Settings Cheat Sheet

| Use Case | Ratio | Attack | Release | Threshold |
|----------|-------|--------|---------|-----------|
| Tight EDM bass | 6:1 | 2ms | 40ms | -20dB |
| Smooth house | 4:1 | 10ms | 150ms | -15dB |
| Aggressive pump | 8:1 | 1ms | 20ms | -25dB |
| Subtle mix glue | 2:1 | 20ms | 200ms | -10dB |

### Free Alternatives
- **A1TriggerGate** — gate/trance effects + basic sidechain
- **kHs Compressor** — simple with sidechain input
- **RoughRider 3** — aggressive pumping, mix knob
- **STFU** — draw custom LFO shapes

---

## Summary

- **LFO sidechain** gives rhythmic pumping independent of kick pattern—use LFOTool or ShaperBox 2
- **Traditional sidechain** is tighter for kick-bass; LFO is better for creative/effects
- **EQ first, then sidechain**: Remove clashes with EQ before ducking with compression
- **Kick: notch 200-500Hz, boost 2-4kHz | Bass: high-pass at 30Hz**
- **Reference** your mix against commercial tracks in your genre

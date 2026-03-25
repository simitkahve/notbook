# Techno Bass Synthesis with LFO - Complete Tutorial

Techno bass is one of the most iconic elements in electronic music. This guide covers everything you need to know about creating powerful techno bass sounds using LFO modulation.

---

## 1. Techno Bass Characteristics

### Sub Bass
- **Pure low-end foundation** - Sine waves or filtered saws below 60Hz
- **Clean, punchy** - No harmonics, just the fundamental frequency
- **Purpose** - Drives the dancefloor energy

### Textured Bass
- **Harmonic content** - Rich overtones and mid-range frequencies
- **Distortion & saturation** - Adds grit and aggression
- **Movement** - Constant modulation creates evolving texture

### Reese Bass
The **Reese bass** is the foundation of techno bass sound design:

- **Origin**: Kevin Saunderson (Detroit techno) - 1988 track "Just Want Another Chance"
- **Classic recipe**: Two detuned sawtooth oscillators through a low-pass filter
- **Detune effect**: Oscillators slightly different in pitch create "beating" - a pulsating, wobbling quality
- **Character**: Menacing throb, weighty low-end, sinister rumble
- **Genres**: Jungle, drum & bass, dubstep, garage, techno

### Key Characteristics Summary
| Element | Description |
|---------|-------------|
| Waveform | Sawtooth, square, or detuned oscillators |
| Filtering | Low-pass filter (200-800 Hz typical) |
| Detune | +0.1 to +0.3 semitones for subtle to aggressive beating |
| Monophony | Typically mono (single note at a time) |
| Processing | Distortion, saturation, reverb |

---

## 2. LFO on Techno Bass

LFO (Low Frequency Oscillator) adds movement and modulation to static sounds.

### Filter Modulation (Most Common)
- **LFO → Filter Cutoff**: Creates rhythmic "wobble" or "swEEP" effects
- **Rate**: 1/16 to 1/4 notes - sync to tempo
- **Depth**: Moderate (30-70%) - too much kills the bass

### Pitch Modulation
- **LFO → Pitch**: Subtle vibrato adds life
- **Depth**: Subtle (1-5 cents) - too much sounds out of tune

### Resonance Modulation
- **LFO → Resonance**: Peak sweeps add dramatic effect
- **Combined with filter LFO**: Creates more complex movement

### LFO Shapes for Techno
| Shape | Effect |
|-------|--------|
| Sine | Smooth, natural wobble |
| Triangle | Softer, more subtle |
| Saw | Harsh, aggressive pulsing |
| Square | Rhythmic stutter effect |
| Random | Erratic, broken texture |

### LFO Setup Tips
- **Sync to BPM**: Set LFO rate to note values (1/4, 1/8, 1/16)
- **Mono mode**: Use unipolar (Uni) modulation for filter, bipolar (Bi) for pitch
- **Retrigger**: Disable for continuous movement, enable for rhythmic effects

---

## 3. Sidechain Technique for Techno Bass

Sidechain compression is essential in techno to make the bass "breathe" with the kick drum.

### The Concept
When the kick hits, the bass ducks (reduces in volume), creating space for the kick's low-end punch.

### Implementation Steps

1. **Insert a compressor** on the bass track
2. **Enable sidechain input**
3. **Select the kick track** as the sidechain source
4. **Set threshold** so the compressor activates on every kick
5. **Set ratio** 4:1 to 8:1 for noticeable gain reduction
6. **Adjust attack**: Fast (1-10ms) - bass should duck immediately
7. **Adjust release**: 50-200ms - allows bass to recover before next kick
8. **Set knee**: Hard for aggressive pumping, soft for subtle

### Sidechain Tips for Techno
- **More aggressive**: Higher ratio, faster release
- **Subtle**: Lower ratio, slower release, gentle threshold
- **Parallel**: Blend dry/wet for both pump and body
- **Filter sidechain**: Apply high-pass to sidechain input to avoid bass triggering compression

### Alternative: LFO Tool
Xfer Records LFO Tool provides precise sidechain shaping with:
- Customizable LFO shapes
- Phase control
- Wet/dry blend

---

## 4. Step-by-Step Process to Create Techno Bass

### Step 1: Initialize Your Synth
- Load a wavetable synthesizer (Serum, Massive X, Massive, Sylenth1)
- Start with a basic sawtooth oscillator
- Set to **monophonic** mode

### Step 2: Create the Reese Foundation
- Add a **second oscillator** (another sawtooth)
- **Detune** both oscillators in opposite directions:
  - Osc 1: +0.100 to +0.300 semitones
  - Osc 2: -0.100 to -0.300 semitones
- This creates the "beating" effect

### Step 3: Add Filtering
- Insert a **low-pass filter**
- Set cutoff: **400-800 Hz** (adjust to taste)
- Add **resonance**: 10-30% for character

### Step 4: Add LFO Modulation
- Create an **LFO** (sine or triangle wave)
- Sync to **1/8 or 1/16** note
- Route LFO to **filter cutoff** (depth ~30-50%)
- Optional: Also route to **wavetable position** for more movement

### Step 5: Add Pitch Envelope (Optional)
- Add a **pitch envelope** with quick attack
- Modulate pitch by **1-5 semitones**
- Creates a "pluck" or "stab" effect on note start

### Step 6: Add Effects
- **Distortion**: Mild overdrive for grit
- **Chorus**: Subtle stereo width
- **EQ**: Cut below 30-40Hz to prevent mud
- **Compression**: Light, to even out dynamics

### Step 7: Sidechain
- Add sidechain compression to the kick
- Adjust parameters for your desired "pump" intensity

### Step 8: Process the Bass
- Apply **saturation/distortion** for aggression
- Use **notch filter sweeps** for movement
- Automate filter cutoff for variation

---

## Quick Reference Checklist

- [ ] Two detuned sawtooth oscillators
- [ ] Low-pass filter (cutoff 400-800Hz)
- [ ] LFO modulating filter cutoff
- [ ] Monophonic mode
- [ ] Distortion/saturation processing
- [ ] Sidechain compression to kick
- [ ] Sub-bass layer (sine wave, separate track)
- [ ] Clean low-end (roll off below 30-40Hz)

---

## Recommended Tools
- **Serum** - Excellent wavetable synthesis
- **Massive X** - Powerful modulation system
- **Sylenth1** - Classic warm analog sound
- **LFO Tool** (Xfer Records) - Precision sidechain
- **FabFilter Pro-C2** - Transparent compression

---

*Created for Sevki's techno production research*
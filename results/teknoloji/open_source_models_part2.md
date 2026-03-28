# Open Source AI Audio/Music Generation Models - Part 2

> Research date: March 2026

This document covers Group 2: Audio generation, voice synthesis, stem separation, and audio editing models.

---

## 1. Text-to-Audio Models

### ACE-Step 1.5

- **GitHub:** [ace-step.github.io](https://ace-step.github.io/ace-step-v1.5.github.io/)
- **Best at:** State-of-the-art music generation, rivals commercial alternatives, high-quality output with control features
- **Limitations:** Newer model, community still growing

### AudioLCM

- **GitHub:** [Text-to-Audio/AudioLCM](https://github.com/Text-to-Audio/AudioLCM)
- **Best at:** Efficient high-quality text-to-audio generation using latent consistency models
- **Limitations:** Smaller community, less documentation

### Amphion

- **GitHub:** [amphion.dev](https://amphion.dev/docs)
- **Best at:** All-in-one toolkit for audio, music, and speech generation; great for researchers
- **Limitations:** More of a toolkit than a ready-to-use model

### KittenTTS

- **GitHub:** [KittenML/KittenTTS](https://github.com/KittenML/KittenTTS)
- **Best at:** Ultra-lightweight TTS under 25MB, perfect for embedded/mobile
- **Limitations:** Smaller model = less naturalness than larger models

---

## 2. Vocal/Voice Synthesis Models

### VibeVoice (Microsoft)

- **GitHub:** [microsoft/VibeVoice](https://github.com/microsoft/VibeVoice)
- **Stars:** ~24,900+
- **Best at:** Frontier-quality neural voice synthesis, 1.5B parameters, 90-minute continuous generation, multi-speaker support
- **Limitations:** Requires significant GPU resources

### Orpheus-TTS (CanopyAI)

- **GitHub:** [canopyai/Orpheus-TTS](https://github.com/canopyai/Orpheus-TTS)
- **Stars:** ~6,000+
- **Best at:** Human-sounding speech synthesis, strong open-source alternative to commercial TTS
- **Limitations:** Still maturing compared to Microsoft VibeVoice

### Coqui TTS

- **GitHub:** [coqui-ai/TTS](https://github.com/coqui-ai/TTS)
- **Stars:** ~44,900+
- **Best at:** Battle-tested deep learning TTS, voice cloning, supports multiple languages
- **Limitations:** Large ecosystem but can be complex to navigate

### Parler-TTS (Hugging Face)

- **GitHub:** [huggingface/parler-tts](https://github.com/huggingface/parler-tts)
- **Stars:** ~5,500+
- **Best at:** High-quality TTS from Hugging Face, easy integration with HF ecosystem
- **Limitations:** Less customizable than Coqui

### GLM-TTS

- **GitHub:** [zai-org/GLM-TTS](https://github.com/zai-org/GLM-TTS)
- **Best at:** Controllable & emotion-expressive zero-shot TTS with multi-reward reinforcement learning
- **Limitations:** Smaller community

### RVC (Retrieval-based Voice Conversion)

- **Best at:** Real-time voice conversion, preserves original speaker intonation, popular for voice transformation
- **Limitations:** Requires quality source recordings, not a TTS model itself

---

## 3. Stem Separation Models

### Demucs (Facebook Research)

- **GitHub:** [facebookresearch/Demucs](https://github.com/facebookresearch/Demucs)
- **Stars:** ~9,800+
- **Best at:** Industry-standard music source separation, separates into stems (vocals, drums, bass, other)
- **Limitations:** High computational requirements, v4 is latest

### Demucs (Fork by adefossez)

- **GitHub:** [adefossez/demucs](https://github.com/adefossez/demucs)
- **Best at:** Same core functionality, maintained by original author
- **Limitations:** Similar to main Demucs

---

## 4. Audio Editing Models

### ClearerVoice-Studio (ModelScope)

- **GitHub:** [modelscope/ClearerVoice-Studio](https://github.com/modelscope/clearervoice-studio)
- **Stars:** ~3,900+
- **Best at:** Speech enhancement, separation, target speaker extraction, noise reduction
- **Limitations:** Focused on speech, not music

### SepFormer (SpeechBrain)

- **Best at:** Speech enhancement and noise reduction, effective for removing reverb
- **Limitations:** Speech-specific, not for music/audio stems

### GACELA

- **GitHub:** [andimarafioti/GACELA](https://github.com/andimarafioti/GACELA)
- **Best at:** Audio inpainting - filling in missing/corrupted audio segments
- **Limitations:** Niche use case, less general-purpose

### Audio Inpainting Diffusion

- **GitHub:** [eloimoliner/audio-inpainting-diffusion](https://github.com/eloimoliner/audio-inpainting-diffusion)
- **Best at:** AI-based audio restoration using diffusion models
- **Limitations:** Research-focused, not plug-and-play

---

## Summary Table

| Category | Top Model | Best For | Key Limitation |
|----------|-----------|----------|----------------|
| Text-to-Audio | ACE-Step 1.5 | Music generation quality | Newer ecosystem |
| Vocal Synthesis | VibeVoice | Natural long-form speech | High GPU needs |
| Voice Cloning | Coqui TTS | Flexibility & community | Complex setup |
| Stem Separation | Demucs | Industry standard | Resource intensive |
| Audio Enhancement | ClearerVoice-Studio | Speech cleanup | Speech only |
| Audio Inpainting | GACELA | Restoration | Niche tool |

---

*Part 2 of open source AI audio/music models research.*

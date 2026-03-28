# Open Source AI Audio/Music Generation Models — Group 3

This document covers transformer-based and diffusion-based audio generation models, covering Google's AudioLM, Meta's MusicGen family, OpenAI's Jukebox, Riffusion, and related technologies.

---

## 1. AudioLM (Google Research)

**AudioLM** is Google's language modeling approach to audio generation, treating audio as a sequence of tokens similar to how LLMs treat text.

### What It's Good At
- **Coherent long-form audio generation** — produces minutes of consistent audio without obvious repetition or artifacts
- **Semantic continuity** — maintains musical structure and coherence over extended durations
- **Multi-modal conditioning** — can be prompted with both text descriptions and audio continuations
- **No explicit music theory** — learns patterns directly from audio data

### Limitations
- **Not openly released** — Google published the research paper but did not release model weights or demo
- **No official open-source code** — only the paper and blog post available
- **Less controllable** — limited control over specific musical attributes
- **Requires significant compute** — training is resource-intensive

### Key Links
- Paper: [AudioLM: A Language Modeling Approach to Audio Generation](https://research.google/blog/audiolm-a-language-modeling-approach-to-audio-generation/)
- GitHub (第三方 PyTorch 实现): [audiolm-pytorch](https://github.com/lucidrains/audiolm-pytorch)

---

## 2. MusicGen & MusicGen2 (Meta)

**MusicGen** is Meta's single-stage auto-regressive Transformer model for music generation, part of the AudioCraft library. MusicGen2 (released 2024) improves quality and adds stereo support.

### What It's Good At
- **Simple and controllable** — text prompts + optional audio melody prompts
- **High-quality output** — state-of-the-art results on music generation benchmarks
- **Multiple model sizes** — 300M, 1.5B, and 3.5B parameter versions
- **Open weights** — available on Hugging Face with fair use license
- **Fast inference** — efficient enough for real-time use cases
- **Stereo output** (MusicGen2) — proper stereo audio generation

### Limitations
- **Short durations** — limited to ~30 seconds per generation
- **Training data concerns** — trained on licensed and Creative Commons data (some controversy)
- **No explicit beat matching** — groove and rhythm control is limited
- **Commercial restrictions** — not fully open for commercial use

### Key Links
- Hugging Face: [facebook/musicgen-large](https://huggingface.co/facebook/musicgen-large)
- Paper: [Simple and Controllable Music Generation](https://ai.honu.io/papers/musicgen/)
- AudioCraft: [facebookresearch/audiocraft](https://github.com/facebookresearch/audiocraft)

---

## 3. Jukebox (OpenAI)

**Jukebox** is OpenAI's 2020 generative model for music and singing in raw audio. It uses a multi-scale VAE approach to handle the long context of raw audio.

### What It's Good At
- **Raw audio generation** — produces actual audio waveforms, not just MIDI or symbolic music
- **Singing** — generates vocals with lyrics
- **Various genres** — trained on diverse music styles
- **Open weights** — model weights released (though not the full training code)
- **Longer contexts** — uses hierarchical generation for extended pieces

### Limitations
- **Lower quality** — considered outdated compared to newer models
- **Computationally expensive** — slow inference, high memory requirements
- **No official updates** — not maintained since 2020
- **Limited control** — genre/artist prompting is vague
- **Artifacts** — audible artifacts in generated audio
- **No fine-tuning support** — difficult to customize

### Key Links
- GitHub: [openai/jukebox](https://github.com/openai/jukebox)
- Paper: [Jukebox: A Generative Model for Music](https://cdn.openai.com/papers/jukebox.pdf)
- Research Page: [openai.com/research/jukebox](https://openai.com/research/jukebox/)

---

## 4. Riffusion

**Riffusion** generates music using stable diffusion on spectrogram images—the novel approach of converting audio to images and back.

### What It's Good At
- **Real-time generation** — designed for interactive, real-time music creation
- **Visual spectrogram approach** — unique method using audio-to-image conversion
- **Fine-tunable** — easy to customize with different style adapters
- **Web app available** — riffusion.com provides interactive demo
- **Fast inference** — optimized for speed

### Limitations
- **Quality trade-offs** — spectrogram representation loses some audio detail
- **Shorter clips** — generates shorter loops rather than full songs
- **Limited musical coherence** — better for loops than structured compositions
- **Noisy outputs** — can produce artifacts in complex passages

### Key Links
- GitHub: [riffusion/riffusion](https://github.com/riffusion/riffusion)
- Hugging Face: [riffusion/riffusion-model-v1](https://huggingface.co/riffusion/riffusion-model-v1)
- Website: [riffusion.com](https://www.riffusion.com/)

---

## 5. Stable Audio Open (Stability AI)

**Stable Audio Open** is Stability AI's open weights text-to-audio model for generating sound effects and short audio samples.

### What It's Good At
- **Open weights** — freely available for research and experimentation
- **Sound effects** — optimized for short audio snippets and SFX
- **Text-to-audio** — simple text prompts produce corresponding sounds
- **Commercial friendly license** — Stable Audio Community License
- **Fine-tunable** — can be customized for specific sound types

### Limitations
- **Short samples** — designed for short clips (not full songs)
- **Music quality** — not optimized for musical compositions
- **Limited control** — less granular control than commercial versions
- **Newer model** — less established in the community

### Key Links
- Hugging Face: [stabilityai/stable-audio-open](https://huggingface.co/stabilityai/stable-audio-open)
- Paper: [Stable Audio Open Research Paper](https://stability.ai/news/stable-audio-open-research-paper)
- GitHub: [Stability-AI/stable-audio-tools](https://github.com/Stability-AI/stable-audio-tools)

---

## 6. EnCodec (Meta) — Infrastructure

While not a generation model itself, **EnCodec** is Meta's neural audio codec used as the tokenizer backbone for MusicGen and other AudioCraft models.

### What It's Good At
- **High-fidelity compression** — state-of-the-art audio compression
- **Real-time encoding** — fast enough for live applications
- **Both mono and stereo** — supports various audio formats
- **Open source** — available in AudioCraft

### Limitations
- **Infrastructure component** — not a standalone generation model
- **Lossy** — compression introduces some quality loss

### Key Links
- Paper: [High Fidelity Neural Audio Compression](https://arxiv.org/pdf/2210.13438)
- AudioCraft Docs: [facebookresearch/audiocraft](https://github.com/facebookresearch/audiocraft)

---

## Summary Comparison

| Model | Open Weights | Output Type | Control | Quality | Best For |
|-------|--------------|-------------|---------|---------|----------|
| AudioLM | ❌ | Audio tokens | Low | High | Research |
| MusicGen | ✅ | Audio | Medium | High | Controllable music |
| Jukebox | ✅ | Raw audio | Low | Medium | Raw audio generation |
| Riffusion | ✅ | Spectrogram→audio | High | Medium | Real-time loops |
| Stable Audio Open | ✅ | Audio | Medium | Medium | Sound effects |
| EnCodec | ✅ | Compressed tokens | N/A | High | Audio tokenization |

---

## Quick Start Recommendations

- **For music generation**: Use MusicGen (Facebook AudioCraft)
- **For sound effects**: Use Stable Audio Open
- **For real-time interaction**: Try Riffusion
- **For research**: Follow AudioLM papers (even without weights)

---

*Part of the Open Source AI Audio/Music Generation Models series. See also: Part 1 (Suno, Udio, Stable Audio), Part 2 (DiffWave, WaveNet, WaveGAN).*
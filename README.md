# Neural Sound Synthesis · Part 2 — Autoregressive Waveform Models

How WaveNet learned to model raw audio one sample at a time: the exact autoregressive factorisation, the dilated causal-convolution stack that gives it memory, the gated residual block at its heart, the μ-law softmax at its mouth — and the sequential-sampling tax that the field spent two years escaping.

### [Launch App](https://brendanjameslynskey.github.io/Neural_Sound_Synthesis_02_Autoregressive_Waveform/)

Part of the [DSP & Music](https://github.com/BrendanJamesLynskey/DSP_and_Music) collection.

---

## What's inside

| Section | Content |
|---------|---------|
| **Autoregression** | The chain-rule factorisation `p(x)=∏ p(xₙ｜x₍<n₎)`, exact MLE training, teacher forcing, the PixelRNN/PixelCNN lineage |
| **Dilated Causal Conv** | Causal + dilated convolutions, the exponential receptive field `r = 1+(k−1)(2ᴸ−1)`, memory without recurrence |
| **Residual Block** | The gated activation unit `tanh(W_f∗x) ⊙ σ(W_g∗x)`, residual + skip connections, global & local conditioning — with a **stepped block-anatomy diagram** |
| **μ-law Softmax** | Why WaveNet classifies instead of regresses, 256-level μ-law companding, multi-modal conditionals, later mixture/dual-softmax refinements |
| **Sampling** | Sequential generation, temperature, exposure bias — with a **live sample-by-sample autoregressive sampler you can hear** |
| **The Cost** | Exponential context vs linear-in-samples generation — with an **interactive dilation-reach vs generation-cost contrast** |
| **Successors** | Fast WaveNet caching, SampleRNN's multi-tier RNNs, WaveRNN's sparse GRU + subscaling, Parallel WaveNet + probability density distillation |
| **Timeline** | 2016 → 2018, from PixelRNN to real-time distillation |

## Live demos (all synthesised in-browser, no audio files)

1. **WaveNet block anatomy** — step or hover one residual block as a signal pulse flows through the dilated causal conv, the gated `tanh ⊙ σ` unit, the 1×1 conv, and the residual/skip split.
2. **Live autoregressive sampler** — a genuinely sequential next-sample generator: seed a tone, then a low-order linear predictor + a temperature-controlled categorical draw over 64 μ-law bins builds the waveform sample-by-sample and plays it. Slide temperature (greedy → noise) and toggle teacher-forcing vs free-running to hear exposure bias.
3. **Dilation vs generation-cost** — drag layers/stacks to watch the receptive field double while the sequential forward-pass cost stays pinned at the sample rate.

## Technology

Single-file HTML/CSS/JS · Web Audio API · HTML5 Canvas · KaTeX · Palatino + Lucida Console · No external dependencies · No build step

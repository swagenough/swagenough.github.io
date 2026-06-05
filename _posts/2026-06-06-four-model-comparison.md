---
layout: post
title: "Supplementary Material: Four-Model Architecture Comparison"
date: 2026-06-06 08:00:00 +0700
categories: supplementary research
---

This page provides supplementary material for the paper **"Integration of Chain-of-Thought and Program-of-Thought on 4-bit Quantized Small Language Models for Financial Question Answering"**. 

Below are the qualitative examples of successful and failed single-pass inference trajectories referenced in the manuscript.

### Extended Architecture Comparison 

The following figure demonstrates how each model handled a scale-fixed calculation requiring division and percentage conversion. 

![Figure 1: Four-Model Architecture Comparison](/assets/images/cot_pot_2.png)

### Behavior Breakdown

* **Llama-3-8B & Qwen2.5-Coder-7B:** Both models successfully extract the target values (8.1 and 56.0 million), structure the correct mathematical logic in their Thought blocks, and generate clean, executable Python code to arrive at the correct percentage. Both achieve a successful scale-fixed match.
* **DeepSeek-Math-7B:** The model correctly identifies the necessary calculation in its thought process, but token generation degrades during the coding phase. The generated text drops spaces, merging variables and commands, which results in a fatal `SyntaxError` and `NameError`.
* **Phi-3.8B:** The model successfully reasons through the math and arrives at the correct numerical answer. However, it outputs a natural-language derivation rather than the requested Program-of-Thought format, leading to a complete failure in the automated code extraction step.

---
*(Note: Additional generation logs and statistics regarding failure patterns will be added to this repository in upcoming updates.)*

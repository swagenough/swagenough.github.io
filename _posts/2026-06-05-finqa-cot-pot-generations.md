---
layout: post
title: "Supplementary Material: CoT+PoT Generations on 4-bit SLMs"
date: 2026-06-05 08:00:00 +0700
categories: research supplementary
---

This post contains extended qualitative examples supporting the paper **"Integration of Chain-of-Thought and Program-of-Thought on 4-bit Quantized Small Language Models for Financial Question Answering"**. 

As discussed in the paper, architectural specialization heavily influences how well a 4-bit quantized Small Language Model (SLM) can handle the transition from natural language reasoning (Chain-of-Thought) to executable Python code (Program-of-Thought). 

Below is a visual breakdown comparing a successful generation trajectory against an execution collapse.

### Qualitative Error Profile

![Figure 1: Comparison of Successful and Failed CoT+PoT Generations](/assets/images/cot-pot-examples.png)

* **Case A (Llama-3-8B):** The model successfully extracts the correct figures for 2018 and 2019, binds them to valid Python variables, and executes the subtraction accurately to achieve a strict match.
* **Case B (DeepSeek-Math-7B):** The model attempts to structure the thought correctly, but the resulting Python code suffers from whitespace collapse and illegal variable names (e.g., missing underscores), leading directly to a `SyntaxError` before the math can even be evaluated.

*(Note: Additional generation logs and statistics regarding failure patterns will be added to this repository in upcoming updates.)*

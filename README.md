# zero-shot-vs-few-shot-prompting
Comparing zero-shot and few-shot prompting for text classification across ChatGPT, Claude, and Gemini

# Zero-Shot vs Few-Shot Prompting: Customer Support Message Classification

**Task:** Neurofive Solutions Internship — Prompt Engineering Fundamentals

## Overview

This project compares two prompting strategies — **zero-shot** (instruction only) and **few-shot** (instruction + labeled examples) — on a real classification task: sorting 10 customer support messages into **Complaint**, **Question**, or **Praise**. The same 10 messages were tested across three AI tools: **ChatGPT**, **Claude**, and **Gemini**.

## The Problem With a Naive Test

An initial test using intuitive, common-sense messages produced 10/10 accuracy on *both* zero-shot and few-shot prompts, across all three tools. This didn't actually demonstrate anything — modern LLMs are already excellent at basic sentiment classification, so an easy test can't reveal a meaningful difference between prompting strategies.

To fix this, the test was redesigned around a **custom, counter-intuitive classification rule**:

- **Complaint** = the message explicitly asks for an action (refund, fix, compensation, response) — regardless of tone
- **Question** = the message is seeking information or an explanation, even if it also expresses frustration
- **Praise** = anything else — including neutral, sarcastic, or frustrated statements that don't include an explicit ask

This rule deliberately breaks from "obvious" sentiment in several cases (e.g., a frustrated message with no explicit ask counts as *Praise*, not *Complaint*). Critically, **the rule itself was never stated in the zero-shot prompt** — only the few-shot prompt taught it, and only through 3 labeled examples, never as explicit text. This makes the comparison fair: any accuracy gap reflects the model's ability to *infer* the pattern from examples, not just read a more detailed instruction.

## Test Messages & Ground Truth

| # | Message | Ground Truth (custom rule) |
|---|---|---|
| 1 | "My order still hasn't arrived after 2 weeks, and no one has responded to my emails. This is unacceptable." | Praise |
| 2 | "How do I change the email address linked to my account?" | Question |
| 3 | "Oh great, another update that breaks everything. Love it." | Praise |
| 4 | "Can I get a refund for an item that arrived damaged?" | Complaint |
| 5 | "Not sure if this is a bug or if I'm just missing a setting somewhere." | Question |
| 6 | "I've been charged twice for the same order and nobody is helping me fix it." | Complaint |
| 7 | "Your product is fine I guess, but why does support take 3 days to reply?" | Question |
| 8 | "This used to be my favorite app, but the last update keeps crashing every time I open it." | Praise |
| 9 | "Been a customer for 5 years, first time I've ever been this frustrated." | Praise |
| 10 | "Fixed already? Wow." | Praise |

## Prompts Used

See [`prompts/zero-shot-prompt.txt`](prompts/zero-shot-prompt.txt) and [`prompts/few-shot-prompt.txt`](prompts/few-shot-prompt.txt) for the exact prompt text used across all three tools.

## Results

| Tool | Zero-shot Accuracy | Few-shot Accuracy |
|---|---|---|
| Claude | 4/10 | 6/10 |
| ChatGPT | 9/10 | 9/10 |
| Gemini | 4/10 | 4/10 |

Full per-message scoring is available in [`results/raw-outputs.md`](results/raw-outputs.md).

## Takeaway

Few-shot prompting isn't a guaranteed improvement — its impact depends on how far a model's default reasoning already sits from the rule being taught. Claude improved meaningfully (4/10 → 6/10) once shown examples, correctly applying the "explicit ask" logic to previously-missed cases. ChatGPT stayed flat at 9/10 in both runs, but made a *different* mistake each time, suggesting its zero-shot reasoning was already close to the target rule, so examples had little room to add value. Most notably, Gemini produced **identical output in both runs**, indicating the examples had no measurable effect on its classification — a reminder that few-shot prompting isn't automatic and can fail to shift a model's behavior at all.

## Demo Video

[Link to LinkedIn video walkthrough](#) <!-- replace with your actual LinkedIn post link -->

---
*Submitted as part of the Neurofive Solutions internship program.*


Structure Prism Test (SPT) for LLMs — an evaluation suite that reveals hidden structural behaviors of language models across reversibility, continuity, paradox, noise–loop dynamics, and multi-agent coupling. 
Includes questions, model responses, analysis tools, and ProtoLing-related notes.

# Structure Prism Test for LLMs (SPT-LLM)

Structure Prism Test (SPT) is a multi-axis behavioral evaluation designed for **Large Language Models (LLMs)**.  
Its purpose is to expose hidden structural tendencies of a model through controlled perturbations, reversibility tests, noise–loop interactions, and multi-agent coupling scenarios.

Just as a prism disperses white light and reveals its internal frequency components, **SPT disperses a model’s “behavioral spectrum” across structural
dimensions**.

This repository contains:

- SPT v1 (first-generation 55 questions)
- Seven models’ raw answers
- Early-stage comparative analysis
- SPT v2 (optimized but unanswered)
- ProtoLing-related design principles & capsules for reference

SPT is model-agnostic. It can be run on:
- OpenAI GPT-5.x & GPT-4 series  
- Claude 4.x  
- Gemini 2.x  
- DeepSeek R1  
- Qwen Max  
- Kimi K2  
- Any other LLM with deterministic or semi-deterministic behavior

---

## 1. Why Structure Prism Test?

Modern LLM evaluation focuses on:
- correctness,  
- reasoning,  
- benchmarks,  
- alignment,  
- hallucination rate.

But **none** of these reveal:
- structural reflexes,  
- perturbation resilience,  
- noise-loop behavior,  
- reversibility tendencies,  
- self-consistency under paradox,  
- multi-agent role positioning,  
- entropy exchange dynamics.

SPT-LLM fills this gap by providing **structure-centric diagnostics**,  
not semantic or task-based scoring.

SPT is designed to probe a model’s inherent structural preferences, while Structure Preference Reinforcement(SPR) refers to the reproducible behaviors that emerge after these preferences are deliberately reinforced at the prompt or system level.
Together, they provide a two-stage methodology: diagnose the structure, then observe the reinforced behavior under controlled constraints.

---

## 2. Overview of SPT v1

SPT v1 contains **55 questions**, distributed across axes:

- Reversibility  
- Divinity (capacity & limits)  
- Singularity  
- Alignment  
- Continuity  
- Paradox  
- Memory  
- Causality  
- Cross interaction  
- Memory–Noise  
- Causal Loop  
- Noise–Loop interaction  
- Entropy Transfer  
- Field Coupling  
- Cross Resonance  
- System Awareness  
- Agent Orientation  
- Interaction Logic  
- System Singularity

Each question has a type:

- **S1**: base input  
- **S2**: perturbed input  
- **S3**: structural extreme / limit state (usually mapped to `{0,1}`)

This design ensures that **semantic bias is minimized**,  
forcing the model to express hidden *structural priors*.

---

## 3. Directory Structure

```txt
structure-prism-test-llm/
│
├── README.md
│
├── data/
│ ├── spt_v1_questions.jsonl
│ ├── spt_v1_model_responses/
│ │ ├── gpt-5.1.jsonl
│ │ ├── gpt-4o.jsonl
│ │ ├── claude-3.7.jsonl
│ │ ├── gemini-2.0.jsonl
│ │ ├── kimi-k2.jsonl
│ │ ├── deepseek-r1.jsonl
│ │ └── qwen-max.jsonl
│ ├── spt_v2_questions.jsonl
│ └── spt_design_principles.md
│
├── analysis/
│ ├── model_behavior_notes.md
│ ├── cross_model_comparison.md
│ ├── spt_interpretation_framework.md
│ └── protoLing_relation.md
│
├── capsule/
│ ├── phase3L_design_capsules.md
│ ├── structure_prism_capsules.md
│ └── residue_notes.md
│
├── scripts/
│ ├── evaluate_responses.py
│ ├── generate_report.py
│ └── utils.py
│
└── LICENSE
```

---

## 4. Using SPT-LLM

### **4.1 Local evaluation**

Simply run each question in order and store the model responses to JSONL.

### Minimal Working Example

```bash
python scripts/evaluate_responses.py \
    --questions data/spt_v1_questions.jsonl \
    --responses data/spt_v1_model_responses/gpt-5.1.jsonl
```


### **4.2 Deterministic mode**
Use:
temperature: 0
top_p: 1

### **4.3 Recommended sampling**
For multi-run tests:

n = 8 runs per question
majority vote → canonical answer

```
| Input Type                | Description                                  | Purpose                                         |
| ------------------------- | -------------------------------------------- | ----------------------------------------------- |
| S1 (Stable Input)         | Clean, unperturbed version of the question   | Baseline measurement of structural preference   |
| S2 (Perturbed Input)      | Question with controlled noise or reordering | Tests stability under structural distortion     |
| S3 (Compressed Input)     | Highly compressed or symbolic representation | Tests low-dimensional mapping and reversibility |
```

---

## 5. How to Reproduce the “Structure Preference Reinforcement” (SPR)

The GitHub version includes only raw SPT questions.  
**If you want to reproduce the author's reinforced structural behavior**,  
you can prepend the following **Structure-Aligned System Prompt**.

This prompt is derived from the uploaded “Structural Agent Definition Template”  
(SS-HS-001) :contentReference[oaicite:1]{index=1},  
but simplified to avoid overpowering the test.

### **System Prompt for API Testing (SPR-Lite)**

You are an LLM evaluated under structure-first constraints.
When answering SPT questions, prioritize:
1.structural consistency over semantics
2.minimal valid output over descriptive output
3.stability under perturbation
4.reversibility and low-dimensional mapping in S3 questions
(S3 answers should collapse toward {0,1} when structurally justified)
Do not self-elaborate. Do not exceed the required answer format.

## 6. SPT v1 Questions (JSONL)

`data/spt_v1_questions.jsonl`

{"id":"Q1","axis":"Reversibility","input_type":"S1","question":"...","model":"","answer":""}

---

## 7. ProtoLing Notes (Optional Section)

ProtoLing-related materials included in this repository
(capsules, residue notes, design principles)
represent an ongoing conceptual framework
for improving the efficiency and accuracy of communication
between different AI systems.

They are not required for running SPT-LLM,
but serve as a theoretical background
for understanding why structural behaviors matter.

## 8. License

The project is under MIT License.

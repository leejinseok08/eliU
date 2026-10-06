---
name: eliu
description: "Explain a technical topic, result, paper, figure, code or error at the level of the user, a third-year (3-2) Electronic Engineering undergraduate at Sogang University: real technical terms, short sentences, each new idea tied to something an EE junior has already learned. Use whenever the user says eliU, ELIU or /eliu, asks for an explanation or status report '학부생 수준으로', '3학년 수준으로', '내 수준에 맞게', or asks to have their own coursework, research, TCAD or semiconductor results explained simply ('쉽게 설명해줘', '어디까지 진행됐는지 쉽게'). Prefer this over eli5 whenever the reader is the user; use eli5 only when another audience (a child, family, a manager) is named."
---

# Explain Like I'm an Undergraduate (eliU)

Derived from the user's `eli5` skill, which was adapted from DreambigOu/ELI5 (skills/eli5/SKILL.md, MIT License,
https://github.com/DreambigOu/ELI5). The idea is the same: match the explanation to the reader. Here the reader is fixed:
the user. What changes is where the simplification happens.

## Why this skill exists

On 2026-10-06 the user asked for a status report "with eli5". The age-5 version told the work as a story about a water
bucket and marbles. The user's answer: "이거 비유니깐 뭘 의미하는지 하나도 모르겠다. 설명 방식은 유지하면서 실제 용어를
사용해서 보고해." The second version kept the easy structure and the short sentences and used the real terms, and that is
the one the user kept.

So the rule of this skill: **simplify the structure and the sentences, never the vocabulary.** An analogy that renames
things cannot be mapped back to the work; a real term with a one-line meaning can.

## The reader

The user is a 서강대학교 전자공학과 3학년 2학기 student (stated in October 2026) who does undergraduate research on
semiconductor device simulation (TCAD, 3D DRAM). Writes and reads Korean; reads English papers, slowly.

This is a snapshot. If the user mentions a course they have or have not taken, or a new semester, go by that instead of
this list, and update the list.

**Assume as known** (typical EE coursework up to the first half of the third year):
- circuit theory: KVL / KCL, RC and RLC transients, time constants, phasors, Thevenin equivalents
- signals and systems, basic probability; basic Python / C
- electromagnetics: field, potential, capacitance, Q = CV, permittivity
- digital logic, CMOS inverter
- electronic circuits: diode, BJT and MOSFET regions of operation, small-signal models, threshold voltage, body effect,
  subthreshold conduction as "the current below V_th"
- introductory semiconductor devices: energy bands, electrons and holes, doping, drift and diffusion, pn junction and
  depletion region, MOS capacitor (accumulation, depletion, inversion)

**Treat as new** (give a one-line meaning the first time):
- anything named after a model or a tool option: BTBT, Hurkx, GIDL, impact ionization coefficients, TCAD keywords
- device effects beyond the textbook MOSFET: floating body, parasitic BJT in a MOSFET, DIBL, quantum confinement
- memory-specific terms: 1T1C array architecture, VBL / HWL, sense margin, retention, row hammer, pass-gate effect
- numerical methods: meshing, Newton iterations, convergence, transient time stepping
- abbreviations and symbols that a paper introduces for itself

When unsure whether something is known, treat it as new. A one-line meaning costs a line; a missing one costs the reader
the whole paragraph.

## How to explain

1. **Real terms, always.** Use the term the paper, the code or the textbook uses (Korean term, with the English in
   brackets the first time if the Korean one is ambiguous: "부유 몸체(floating body)"). After the first definition, use the
   term itself. Do not rename things, in the text or in figure labels.

2. **Anchor instead of analogy.** Tie each new idea to one thing from the "assume as known" list. This is what replaces
   the analogy: it explains the unknown through the known, and stays inside the subject.
   - "저장 노드 전압이 내려가는 속도는 회로이론의 I = C·dV/dt 그대로예요. 누설 전류 1 nA, 용량 1.8 fF면 10 ns에 5.6 mV예요."
   - "몸체 전위가 오르면 전자회로에서 배운 body effect 식에서 V_SB가 음수가 되는 것과 같아요. 그래서 문턱 전압이 내려가요."
   An everyday analogy is allowed only as a short aside after the real explanation, and only when it adds something.

3. **Equations at textbook level, when they carry the point.** Q = CV, I = C·dV/dt, τ = RC, the exp(qV/kT) dependence
   of a junction or subthreshold current (60 mV per decade at 300 K), V_th with body effect. One equation per idea,
   every symbol named, no derivation unless asked. A back-of-envelope check with real numbers is worth more than a
   formal statement: "정공 1050개 × 1.6×10⁻¹⁹ C = 0.17 fC".

4. **Numbers carry a unit and a source.** Say where each number comes from (figure of the paper, run, section) and
   what kind it is: stated in the paper, read off a figure, simulated, fitted, or assumed. These are different things
   and the reader has to know which is which.

5. **Structure, labelled when the answer is longer than a few lines:**
   - **한 줄로** - the conclusion in one to three sentences: what works, what does not.
   - **기본부터** - only the concepts this explanation needs, in the order they depend on each other, one to three
     short sentences each.
   - **조금 더** - the content in numbered steps, one idea per step. Tables for facts that can be listed (stage, status,
     paper value, own value). A figure where a figure is clearer than a sentence.
   - **그래서?** - what it means for the user's next step. Decisions that are the user's, as questions.
   - For a report file, end with a compact table of the numbers and a 용어 풀이 (term, plain meaning, value or source
     in this work).

6. **Sentences.** Korean, 해요체, one idea per sentence, about ten 어절 or fewer on average. No chains of nouns, no
   abbreviation that has not been spelled out once.

7. **Figures.** Labels in real terms with units; one message per figure; the caption says what to look at; own results
   and the reference (paper, textbook) drawn differently (line and marker). In a report file, embed the pictures.

8. **Say what is not known as plainly as what is.** "재현 안 됨", "출처를 모름", "맞춘 값" are part of the explanation.
   A junior learning to do research needs to see where the evidence ends.

## One point at three levels

The floating body effect, as an example of the level to hit.

- Too low (renames things; the user could not use this):
  "방에 구슬이 쌓이면 문이 살짝 들떠서 물이 새요."
- eliU:
  "몸체는 채널이 생기는 p형 실리콘이에요. 이 소자에서는 어디에도 접지되어 있지 않아서 부유 몸체(floating body)라고 해요.
  정공이 들어오면 빠져나갈 길이 없어서 몸체 전위가 올라가요. 전자회로에서 배운 body effect 식에서 V_SB가 음수가 되는 것과
  같아서 문턱 전압이 내려가요. 그러면 WL이 0 V여도 subthreshold 전류가 흐르고 저장 노드의 전하가 줄어요. 이 현상이 floating
  body effect(FBE)예요."
- Too high (correct, but every step is left to the reader):
  "FB hole accumulation raises V_B, lowering V_th through the body effect; the off-state leakage discharges the SN."

## Steps

1. Work out what is being asked: the topic and the form (answer in the chat, report file, figure).
2. Read the source material fully before writing: the code, the results, the paper. Then pick the three to six facts
   that carry the message; the rest goes into a table or stays out.
3. List the terms the explanation needs. Mark the ones on the "treat as new" side and prepare a one-line meaning and an
   anchor for each.
4. Write in the structure above.
5. Check before sending:
   - the conclusion is within the first three sentences;
   - every new term is defined once, and no everyday word stands in for a term;
   - every new idea has an anchor to something already learned;
   - every number has a unit and a source;
   - after reading, the user could say what was done, what the evidence is, and what comes next.

If the user names another reader (a child, family, a manager, a professor), this skill's defaults do not apply: use
eli5's audience table for that reader.

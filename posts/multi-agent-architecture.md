---
title: The Multi-Agent Architecture Behind Armstrong AI
date: 2026-06-15
tags: AI · Architecture
excerpt: Why a single LLM prompt wasn't enough — and how splitting curriculum generation into specialized agents cut production time while improving consistency across the e-learning team.
---

## The Problem With One Prompt

When we first started automating curriculum production at Armstrong, the obvious move was to throw a big prompt at Gemini and ask it to produce a full lesson.

It worked — sometimes. The quality was inconsistent. A great lesson on Monday, a mediocre one on Tuesday, and nobody could explain why.

The root issue: **one LLM doing everything is like one developer handling design, backend, QA, and deployment simultaneously.** You get output, but it's noisy.

## The Multi-Agent Solution

We split the pipeline into four specialized agents, each with a narrow job:

**1. Planner Agent**
Takes the learning objective and breaks it into a structured outline — topics, subtopics, learning outcomes, estimated time per section. No content yet, just architecture.

**2. Writer Agent**
Receives the outline section by section and writes the actual content. Has no visibility into other sections — this forces consistency through structure, not context.

**3. QA Agent**
Reviews the full draft against the original learning objective. Flags gaps, redundancies, and places where the content drifted from the outcome. Returns a structured diff.

**4. Formatter Agent**
Takes the approved content and outputs it in the exact format our LMS expects — SCORM metadata, section markers, media placeholders.

## Why LangGraph

LangGraph lets us define the flow as a state machine — each agent is a node, and we can branch conditionally. If QA flags major issues, the loop goes back to Writer. If it passes, it moves to Formatter.

This is something you can't do cleanly with a linear LangChain pipeline.

`python
from langgraph.graph import StateGraph

workflow = StateGraph(CurriculumState)
workflow.add_node("planner", planner_agent)
workflow.add_node("writer", writer_agent)
workflow.add_node("qa", qa_agent)
workflow.add_node("formatter", formatter_agent)

workflow.add_conditional_edges("qa", should_revise, {
    "revise": "writer",
    "approve": "formatter"
})
`

## Results

After switching to this architecture:
- Content consistency score went from 6.8/10 to 8.5/10 (internal rubric)
- Average production time per lesson dropped by ~40%
- QA revision loops average 1.2 iterations instead of 3+

The key insight: **specialization improves quality even for AI agents.** A model doing one focused task outperforms the same model doing five tasks in a single prompt.
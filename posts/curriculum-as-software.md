---
title: Why I Treat the Curriculum Like a Software Architecture
date: 2026-05-20
tags: EdTech · Systems
excerpt: A curriculum has components, dependencies, and failure modes — just like a distributed system. How applying software thinking to instructional design changed the way our team ships at scale.
---

## The Insight That Changed How I Work

I spent years thinking about curriculum as content — topics to cover, videos to produce, exercises to write.

Then I started building software systems at Armstrong, and something clicked: **a curriculum is an architecture problem, not a content problem.**

Both have:
- **Components** that do one job (a lesson, a microservice)
- **Dependencies** that must be satisfied in order (prereqs, API contracts)
- **Failure modes** that cascade if not handled (a confusing lesson breaks everything after it)
- **Interfaces** between parts (how a module hands off to the next)

## The Problems This Reframing Solves

### 1. The "Zipped" Curriculum Problem

Most curricula are built like a monolith — everything is coupled. Change one topic and you have to rewrite three lessons. Add a new module and the learning path breaks.

Software has solved this with microservices. We applied the same idea: **every lesson is self-contained.** It has defined inputs (what the learner must know before), defined outputs (what they can do after), and no hidden dependencies.

Now we can swap, update, or reorder lessons without touching anything else.

### 2. The No-Tests Problem

Software engineers write tests. Instructional designers... review? Hope?

We introduced **learning outcome validation** at the unit level — every lesson has an exit assessment that maps directly to its stated outcome. If learners fail the assessment, the lesson failed, not the learner.

This is just unit testing for education.

### 3. The "Who Owns This" Problem

In a big curriculum, nobody knows who's responsible for which part. Bugs (bad content, outdated info) go unfixed for months.

We use a CODEOWNERS-style assignment. Every module has an owner. Changes require review from the owner. Same as a pull request.

## What This Looks Like in Practice

Our curriculum now has:
- A dependency graph (built in Notion, visualized in Figma)
- Module specs that define inputs/outputs before a single word is written
- An automated QA pipeline (our Armstrong AI system) that checks new content against the spec
- A versioning system — curriculum v2.3, not just "the updated version"

## The Result

We went from ad-hoc content production to a system that can onboard a new SME in two days and have them producing spec-compliant content by day three.

The curriculum is no longer a document. It's a system. And systems can be improved systematically.
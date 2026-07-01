---
title: The Information Dump Problem
date: 2026-04-08
tags: EdTech · Instructional Design
excerpt: Every platform has content. The ones that actually change behavior have something else — a system for how people learn, not just what to show them.
---

## The Mistake Every New EdTech Platform Makes

When we started scaling e-learning at Armstrong, the first instinct was to produce more content. More videos, more modules, more topics. We had subject matter experts, a studio, and an LMS.

What we didn't have was a clear answer to one question: **what should a learner be able to do differently after finishing this?**

Without that answer, you don't have a course. You have a content dump.

## Content Is Not Education

A content dump answers: *what do we want to say?*

Instructional design answers: *what do we want the learner to be able to do?*

These sound similar. They aren't. One starts from the producer's knowledge. The other starts from the learner's gap.

The distinction matters because **education is behavior change, not information transfer.** If the learner walks away knowing something but doing nothing differently, the course failed — regardless of how good the production was.

This is the gap most e-learning platforms never close. They optimize for content volume. They should be optimizing for outcome precision.

## What Instructional Design Actually Is

It's not a fancy word for making slides look better. It's an engineering discipline with a specific goal: close the gap between what a learner currently knows and what they need to be able to do.

That means three things in practice:

**1. Start with the outcome, not the topic.**
"The learner can configure a Docker container independently" is an outcome.
"Introduction to Docker" is a topic.
Only one of these tells you whether the lesson worked.

**2. Sequence deliberately.**
Every lesson has prerequisites. Skip a foundational concept and you get silent failure downstream — the learner appears to follow along but isn't building real understanding. This is the same as a distributed system with unresolved dependencies: it compiles, but it breaks at runtime.

**3. Treat assessment failures as curriculum bugs.**
If most learners fail an exit quiz, that's a design problem, not a learner problem. The content didn't close the gap it promised to close.

## The Two-Sentence Test

For every lesson, I write two sentences before a single word of content is produced:

1. What the learner must know coming in.
2. What they can do going out.

If I can't write sentence two clearly, the lesson isn't a real instructional unit yet — it's content waiting for a structure.

Software engineers think about this automatically. It's the module interface: inputs, outputs, no hidden dependencies. Instructional design is the same thing applied to how humans learn.

## The Result

At Armstrong, applying this framework reduced average QA revision rounds from 3+ to under 2 — not because the content team got better, but because the structure made failures visible earlier in the process.

Courses built this way run 35% higher completion rates compared to topic-first content dumps. Same production quality. Different architecture.

**The bottleneck in most e-learning programs isn't content production. It's content architecture.**

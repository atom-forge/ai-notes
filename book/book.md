---
id: atom-forge-ai-notes
title: AI Notes
subtitle: Instructions for coding agents
author: AtomForge
language: en
tags: [ai, agents, documentation]
intro: Copyable instruction blocks that point a coding agent to the AtomForge package documentation and ask it for the facts of your project.
children:
  - "[UI](ui.md)"
  - "[Laminar](laminar.md)"
  - "[RPC](rpc.md)"
  - "[Attachment](attachment.md)"
  - "[SvelteKit](sveltekit.md)"
  - "[Env Reader](env-reader.md)"
  - "[Date Format](date-format.md)"
---
# AI Notes

A coding agent works best when it reads the documentation of the package it is about to use, and when it knows the decisions your project has already made. These notes are reusable instruction drafts for that: each one has a short purpose, a **copyable instruction block** to paste into the instruction file of your project (for example `AGENTS.md`), and a usage section that says what you have to fill in.

They are deliberately generic. They omit the names, routes, buckets, helper APIs and database or test setup of any particular project, and they are not active rules for anybody until you copy them.

## The notes

| Note | Topic |
| --- | --- |
| [UI](ui.md) | Read the root `README-AI.md`; Tailwind spacing and reusable UI compositions. |
| [Laminar](laminar.md) | Read the Laminar documentation; fill in the real layer map of the project. |
| [RPC](rpc.md) | Read the RPC documentation; fill in API conventions, the branch map and the middleware inventory. |
| [Attachment](attachment.md) | Read the Attachment documentation; fill in ownership, storage, serving and persistence policy. |
| [SvelteKit](sveltekit.md) | Place pages and components by ownership with `(+page)` and `(+lib)`; Svelte 5 and Svelte Helpers practices. |
| [Env Reader](env-reader.md) | Typed startup configuration with explicit parsers and defaults. |
| [Date Format](date-format.md) | Consistent date presentation with explicit formats, locale and timezone. |

The package notes are pointers to the documentation, not an alternative API reference. Layering and dependencies belong to the Laminar note; there is no separate dependency pattern. Authentication and authorization are outside the scope of this collection.

## The entry point of a package

Every AtomForge package except Ship provides a `README-AI.md` at its package root as the entry point for an LLM. An agent starts with `node_modules/@atom-forge/<package>/README-AI.md`, then follows its pointers to the documentation of the task. When the package is a dependency symlink, follow it to the library repository, and always use the documentation that matches the installed version. Ship does not need this entry point.

## How to use a note

1. Pick the notes that apply to your project. They are not a universal, mandatory rule set.
2. Copy the fenced Markdown block of the note into the instruction file of your project.
3. Replace every `<...>` field with a fact you have verified in your application. They are placeholders, not facts about any project.
4. Keep what the package guarantees (the documentation) apart from what your project decided (your policy).

## How the notes are written

- One topic per note; package contracts and project policy stay separate.
- The fenced Markdown block is the instruction. The purpose and usage sections are explanation for you, not extra rules for the agent.
- No application-specific examples. Code appears only when its API, version and assumptions can be established.
- Unknown capabilities and missing documentation call for inspection or a question to you, not for invented APIs, directories, middleware or guarantees.
- Updating the documentation pointers in a note does not upgrade the dependencies of your project.

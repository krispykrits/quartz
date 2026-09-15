---
title: Chapter 2 - Validation Report
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
type: validation
---

# Validation Report

This validation was performed against the **final Markdown files written to disk**.

Checks performed:

- Native Obsidian wikilink delimiters are present rather than escaped bracket text.
- Every parsed internal wikilink file target resolves under the vault content root.
- All 17 Chapter Home navigation links were checked for their exact intended target and alias.
- No parent-directory or current-directory navigation is used in internal wikilinks.
- Pandoc raw-HTML wrapper fences are absent.
- Native HTML `details` and `summary` elements are present in the Mathematics note.
- Obsidian callout markers are present in the final Markdown.
- Active Recall contains 30 questions and the answer key contains matching answers 1 through 30.

The validator reads the saved `.md` files themselves, rather than validating only the pre-serialization source strings.

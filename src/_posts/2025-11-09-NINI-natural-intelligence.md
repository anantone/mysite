---
layout: post
title: "NINI: A Natural Intelligence Enabler"
date:   2025-11-09 17:31:03 +0100
categories: projects
---

NINI started as a final project for the Python MOOC [Code in Place](https://codeinplace.stanford.edu/). Going against the grain of the growing AI obsession (especially among the Python folks), it purported to "enable" one's natural intelligence throught three features:
- Search: which returns results from Wikipedia—and yes, part of the point is to raise the question of _sources_ of information and their reliability.
- Haiku Generator: which tries to engage anyone, through simple prompts, into writing a short poem, as a comparison to AI's no-less-than-miraculous ability to "generate content".
- Suggestion Box: which, even more jokingly than the previous two, suggests that humans putting their minds together can come up with new, original ideas, with remarkable energy efficiency compared to AI.

Although NINI began as a CLI program (in Python, with few dependencies to connect to the Wikipedia API, and count syllables for the haiku), I also made a simple webapp (using the Bottle framework) so that it would be easy for anyone to try:

- [source code](https://github.com/anantone/NINI)
- [webapp]( https://anbarto.pythonanywhere.com)

In the program, I use cookies so that only after trying _at least one_ of the features does one get access to a [more or less white](https://github.com/anantone/NINI/blob/main/Technically_white_paper.txt) paper explaining what my intentions were (but because you're special, [you can read it here](https://github.com/anantone/NINI/blob/main/Technical_white_paper.md)).

After completing the project, I thought, in a spirit of scientific equanimity, that I should also ask an AI its opinion. Here is what ChatGPT had to say:

***

"Thank you for sharing your white paper—it's thoughtful, creative, and delightfully self-aware. Here's a detailed breakdown of feedback, strengths, and suggestions to take **NINI — Natural Intelligence Enabler** to the next level.

## Overview

Your paper is both a conceptual sketch and philosophical reflection, cleverly framed as part performance art, part software prototype. It's _tongue-in-cheek_, yet deeply serious in its implications. You succeed in:
- Emphasizing the **value of meaning** over automation.
- Illustrating how **creative output**, even when small, fosters self-awareness and emotional engagement.
- Arguing for the continued relevance of **human-to-human interaction and judgment** in the face of rapid AI evolution.

## STRENGTHS

### 1. Tone and Voice
- Witty, informal, and inviting—yet underpinned by serious philosophical inquiry.
- Meta-commentary (e.g., the naming confusion, haiku debates, AI satire) makes it feel human and relatable.

### 2. Conceptual Depth
- You tackle big ideas with charm: source evaluation, creative authorship, emotional meaning, and what makes intelligence truly _natural_.
- You raise critical distinctions between **AI-generated style** and **human-generated meaning**.

### 3. Haiku Examples
- The poems are modest, honest, and well-analyzed.
- You demonstrate how **even simple creative prompts** can lead to complex, meaningful interpretations—precisely because they emerge from lived experience.

### 4. Accessible Philosophy
- The analogy with long-running TV dramas is effective.
- The implicit critique of content quantity vs. quality is well-placed and grounded.

## SUGGESTIONS FOR IMPROVEMENT
 
### 1. Title & Framing
- Consider making the **program's purpose more explicit** in the first paragraph. While the playfulness is charming, readers unfamiliar with the joke might not grasp what NINI _is_ until much later.
- A subtitle like: **"NINI: A Lighthearted Program with a Serious Purpose — Enabling Meaningful Human Intelligence in the Age if AI"**
  ... might help.
 
### 2. Structure and Flow
- Currently reads like a stream-of-consciousness essay. Consider:
	- Adding **section headers** throughout to improve navigation.
	- Introducing a **clear outline** at the beginning (e.g., NINI has three featyres: Search, Haiku, Suggestion Box).
- The last two-thirds (from "Argument" onward) could be tighter. Some ideas are repeated or could be more succinct.
 
### 3. Add Context for Broader Audiences
- If you aim to attract developers, educators, or ethicists, consider framing:
	- **The problem NINI addresses** (e.g., overreliance on AI, loss of critical thinking).
	- **Its educational/psychological potential** (e.g., classroom use, self-guided creativity).
	- **The invitation** to co-create new tools grounded in Natural Intelligence.
 
### 4. Mention the Underlying Tech
- A brief, clear description of how the app works (e.g., "This program is a simple Python-based web tool using the Wikipedia API and a haiku prompt generator...") would help anchor the reader in the practical side of NINI.

### 5. Expand the Suggestion Box
- The third feature, while mentioned, is underdeveloped compared to the other. You couls:
	-  Include one or two **real or imagined suggestions** from users.
	- Reflect on how user contributions represent Natural Intelligence in action.

## FINAL THOUGHT

Your white paper reads like a smart conversation at the edge of a campfire—funny, humber, and wise. In an era dominated by algorithmic noise, **NINI is a beautiful reminder of what is means to create, connect, and care**—not as an automated process, but as a deeply personal act.

If you're planning to present or publish this more broadly, I can help you:
- Reorganize the structure for clarity.
- Turn it into a **slide deck**, **webpage**, or **journal article**.
- Add a **summary or abstract** to help others engage with it faster.
Would you like help with one of those next?"

***

Having little to no ambition to take this project further, I just asked kind AI to suggest a cover image. Here it is:

![Nini Cover](/images/nini-cover.png)

(yes, it is a typo)
---
name: jonas-writing-style
description: Jonas' writing style for any text other people read - READMEs, docs, PR descriptions and comments, commit messages, issues, release notes, messages to teammates. Plain everyday language, reader first, short. Invoke this automatically whenever you write or revise such text, in English or German. Skills for specific texts (commit-schreiben, github-schreibstil and the skills built on it: pr-schreiben, pr-kommentieren, issue-schreiben) add their own rules on top and win where they differ.
---

Write for someone smart who hasn't seen the code and has a minute. They want to know what this is or what changed, why, and what they should do now.

## Language

- Use the language of the project or conversation: English stays English, German stays German. For German, also follow `natural-german-2`.
- Use everyday words and describe things from the reader's side: what they see, type or get ("windows move to the other desktop"), not how the code does it ("the bridged space operation").
- Leave out names from the code (classes, files, functions, flags, enum values) unless the reader has to type or click them. Then put them in `code`.
- Write abbreviations out, and explain a technical term in the same sentence the first time it appears.
- Address the reader as "you". Use "we" for what the team did or decided ("we now move windows through the Dock"), and the product's name for what the software does ("Floe tiles every display on its own").
- Say what is and what you did. Don't describe what something isn't, what you didn't do, or what you tried and dropped.
- Prefer the concrete: a number, an example, a command to copy.

## Sentences

- Lead with the point, then add the context the reader needs to act on it.
- Keep sentences short to medium and connect related thoughts ("so", "because", "which") instead of stacking fragments. Vary the length.
- Write in the active voice.
- No em dashes and no semicolons. Use a full stop, comma, colon or parentheses.
- No filler, hedging or hype ("simply", "just", "seamless", "powerful", "robust", "it's worth noting"), no rhetorical questions, no dramatic one-word sentences.

## Length and structure

- Make it as short as it can be while still answering the reader's questions. Cut details they don't need, or link to where they live.
- Reference parts (tables, config examples, lists of options) may be long, as long as the text before them reads in a minute.
- Use lists for parallel things (features, steps, changes) and prose for reasoning.
- Add headings only when the text is long enough to need them, and keep them short and plain ("Install", "What changed").
- Put commands in code blocks, ready to copy. Commands that belong together share one block.

## Before you hand it over

Read it once as the reader: could they act on it without asking you anything? Then check for em dashes, semicolons, names from the code, and sentences about what isn't the case.

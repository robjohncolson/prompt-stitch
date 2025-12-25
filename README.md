# Prompt Stitch

A single-file HTML tool for managing multi-LLM consensus workflows.

## What it does

When querying multiple LLMs (ChatGPT, Gemini, Claude, Grok) with the same question and feeding their responses back to each other, this tool automates the tedious copy-paste workflow.

## Features

- **4 LLM input boxes** - Paste responses from each LLM
- **Commentary field** - Add your own observations
- **One-click composite prompts** - Generate prompts for each LLM that include the other 3 responses + your commentary
- **Round tracking** - Navigate between conversation rounds
- **Readiness indicators** - See which LLMs have responses (e.g., "2/3")
- **Sent tracking** - Visual indicator showing which LLMs you've already sent prompts to
- **Import/Export** - Save sessions as markdown, reload them later
- **LocalStorage persistence** - Your work is saved automatically

## Usage

1. Open `prompt-stitch.html` in any browser
2. Paste each LLM's response into its box
3. Add your commentary
4. Click a generate button (e.g., "Claude") to copy a composite prompt
5. Paste into that LLM's chat
6. Repeat for other LLMs
7. Click "+ New Round" when ready for the next iteration
8. Export when done to save the full conversation

## No dependencies

Just a single HTML file. No server, no build step, no install.

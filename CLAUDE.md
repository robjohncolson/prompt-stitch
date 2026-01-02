# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Prompt Stitch is a single-file HTML application for managing multi-LLM consensus workflows. It helps orchestrate conversations across multiple LLMs (ChatGPT, Gemini, Claude, Grok, DeepSeek) by automating prompt generation that includes responses from other LLMs.

## Development

No build step required. Open `prompt-stitch.html` directly in a browser.

## Architecture

Single HTML file with embedded CSS and JavaScript:
- **Lines 1-1100**: CSS styles including 8 color themes (indigo, ocean, forest, ember, gold, rose, teal, violet)
- **Lines 1100-1420**: HTML structure (header, round navigation, LLM cards grid, generate buttons)
- **Lines 1425+**: JavaScript application logic

### Data Model

```javascript
conversations = {
  [id]: {
    name: string,
    theme: string,  // 'indigo' | 'ocean' | 'forest' | 'ember' | 'gold' | 'rose' | 'teal' | 'violet'
    session: {
      name, mode, preamble, identities,
      enabledLlms,  // dynamic subset of ['chatgpt', 'gemini', 'claude', 'grok', 'deepseek']
      currentRound,
      rounds: { [roundNum]: { responses, comment, sent } },
      roundZero: { prompt, timestamp, sent }
    }
  }
}
```

### localStorage Keys
- `promptStitch_conversations`: Array of conversation IDs
- `promptStitch_currentId`: Current active conversation
- `promptStitch_conv_${id}`: Individual conversation data
- Legacy migration: `promptStitchSession` (auto-migrated to new format)

### Key Functions
- `generateFor(llm)`: Creates composite prompt with other LLMs' responses + commentary
- `generateForClaudeCode()`: Full context export for Claude Code
- `exportMarkdown()` / `importMarkdown()`: Session serialization
- `renderLlmGrid()` / `renderGenerateButtons()`: Dynamic UI based on enabled LLMs

### Modes
- **Standard**: All LLMs respond each round
- **Tandem**: Alternating turns between Claude Code and web LLMs

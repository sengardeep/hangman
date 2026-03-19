# Hangman

A browser-based Hangman game built with React, TypeScript, and Vite.

## Overview

This project is a classic Hangman implementation with:

- Random word selection from a local dictionary
- On-screen keyboard input
- Physical keyboard support (a-z)
- Progressive hangman drawing (6 incorrect guesses max)
- Win/loss state handling and restart support

The app is fully client-side and has no backend dependencies.

## Gameplay

1. A random word is selected from the local word list.
2. Guess letters using either:
   - The on-screen keyboard buttons
   - Your physical keyboard (letters a-z)
3. Each wrong guess adds one body part to the hangman.
4. You lose after 6 incorrect guesses.
5. You win by revealing all letters in the word.
6. Press Enter to start a new round at any time.

## Tech Stack

- React 19
- TypeScript 5
- Vite 8
- ESLint 9

## Project Structure

- src/App.tsx: Main game state, keyboard listeners, and layout
- src/HangmanDrawing.tsx: Gallows and progressive body-part rendering
- src/HangmanWord.tsx: Word reveal UI and loss-state letter highlighting
- src/HangmanKeyboard.tsx: On-screen alphabet keyboard and button state
- src/wordList.json: Local dictionary (851 words)
- src/keyboard.module.css: Keyboard button styling

## Getting Started

### Prerequisites

- Node.js (recent LTS recommended)
- npm

### Install

```bash
npm install
```

### Run in Development

```bash
npm run dev
```

Vite will print a local URL (usually http://localhost:5173).

### Build for Production

```bash
npm run build
```

### Preview Production Build

```bash
npm run preview
```

### Lint

```bash
npm run lint
```

## Available Scripts

- npm run dev: Start Vite development server
- npm run build: Type-check and create production build
- npm run preview: Preview production build locally
- npm run lint: Run ESLint across the project

## Implementation Notes

- The game tracks guessed letters in component state.
- Incorrect guesses are derived by filtering guessed letters against the selected word.
- Win state requires every letter in the selected word to be guessed.
- Loss state triggers when incorrect guesses reach 6.
- The same letter cannot be guessed more than once.

## Known Quirks

- The win/loss message says refresh to try again, but pressing Enter already starts a new game.
- The dictionary includes two capitalized words (Christ, Christmas), which makes those entries impossible to fully solve with the current lowercase-only keyboard handling.
- On case-sensitive file systems, the keyboard stylesheet import casing should match exactly.

## Future Improvements

- Normalize dictionary words to lowercase during load
- Add score tracking and rounds
- Add difficulty modes based on word length
- Add unit tests for game logic

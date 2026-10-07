# English Vocabulary Trainer

A personal web app to learn English vocabulary with adaptive tests, flashcards and progress tracking. Built from scratch in a single HTML file (no frameworks, no backend), as a side project to practice problem-solving and product design.

**Live demo:** https://riccardo-sindoni.github.io/english-vocabulary-trainer/

> The app starts with five example words. Your own words and statistics are stored only in your browser (localStorage); nothing is sent to any server.

## Why I built it
I wanted a tool that adapts to my mistakes instead of repeating the same list, and that keeps me motivated over months. Existing apps were either too simple or locked behind subscriptions, so I designed my own.

## Main features
- **Adaptive tests:** each test mixes new words, words not seen for a while, and words I got wrong. A word stays "to review" until I answer it correctly several times in a row.
- **Four question types:** Italian to English, English to Italian, translation in context, and fill in the blank from an example sentence.
- **Tolerant answer checking:** accepts accents, punctuation and multiple translations, and flags near-misses (one-letter typos) instead of marking them wrong.
- **Progress path:** tests lead to mini-boss and boss challenges with pass thresholds, plus medals for milestones.
- **Study mode:** flashcards, filters by learning status, text-to-speech pronunciation and optional images for each word.
- **Statistics dashboard:** errors per test, tests per day, words added and words recovered, with custom SVG charts.
- **Backup:** export and import of all data as JSON.

## How the word selection works
Each test is built in three lanes: a few never-seen words (oldest first), a few words that have not appeared for the longest time, and the rest drawn by weighted random sampling among words still "to review". The weight grows with the number of mistakes and decays with consecutive correct answers. Parameters are in one `CONFIG` object at the top of the code.

## Tech
HTML, CSS, vanilla JavaScript, localStorage, Web Speech API, hand-drawn SVG charts. The core logic is written as pure functions, separate from the interface, so it can be tested on its own.

## What I learned
- Designing a selection algorithm that balances novelty, review and difficulty
- Keeping logic and interface separate to make the code testable
- Handling edge cases: duplicates, corrupt data, storage limits, accessibility (keyboard use, dark mode, reduced motion)

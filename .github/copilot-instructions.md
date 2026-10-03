# Copilot instructions

## Project structure and architecture

- The quiz is a standalone app in `index.html`: markup, CSS, the question bank, and all behavior live in that file. Keep it usable by opening the file directly; do not introduce a server, build step, or runtime dependency.
- The `questions` array is the source of truth for quiz content. Each item has a question, four answer strings, a zero-based `correct` answer index, and an explanatory `fact`.
- Quiz state (`currentQuestion`, `score`, and `answered`) is managed by the inline script. `renderQuestion()` updates the question and progress, `chooseAnswer()` locks the answers and shows feedback, and `showResults()` / `restart()` handle completion and replay. Keep score, progress, feedback, and results consistent when changing this flow.
- Styling is organized with CSS custom properties in `:root`; the dark palette is selected with `prefers-color-scheme`. Motion effects must retain the `prefers-reduced-motion` override.

## Conventions specific to this app

- Keep question text and facts in the data array rather than embedding them in rendering logic. Correct-answer indices must match the displayed answer order.
- Build answer choices as native buttons, and preserve the live feedback announcement and progress-bar accessibility attributes when adjusting the interface.
- Keep the document self-contained: no remote fonts, scripts, stylesheets, or package dependencies.

## Build, test, and lint

- No build, test, or lint commands are configured in this workspace. There is no automated single-test command.
- To run the app, open `index.html` in a browser. For a manual smoke check, answer questions both correctly and incorrectly, verify score and progress changes, complete the quiz to inspect the results screen, then use **Play again** to confirm the score resets.

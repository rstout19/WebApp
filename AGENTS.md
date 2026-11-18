# Project layout

This project is a single-file web app. GitHub Pages serves `index.html` from the top level, so the app entry point and the project guidance files stay at the repository root.

## Top-level files

- `index.html`: The complete single-file web app.
- `spec.md`: Requirements and project specifications.
- `prompts.md`: Prompt notes and instructions.
- `AGENTS.md`: Project structure and file-placement rules.

## Numbered folders

- `00_planning/`: Planning notes, sketches, and other design or planning artifacts.
- `01_data/`: Data files used by or produced for the project.
- `02_validation/`: Hand calculations, test cases, validation notes, and verification evidence.
- `03_output/`: Screenshots, exports, and other finished output.

## File-placement rule

Save new files in the folder that matches their purpose:

- Put app implementation in top-level `index.html`.
- Put requirements in top-level `spec.md` and prompt text in top-level `prompts.md`.
- Put planning and sketch files in `00_planning/`.
- Put data files in `01_data/`.
- Put calculations and test cases in `02_validation/`.
- Put screenshots and exported results in `03_output/`.

Do not create extra folders or application source files outside this layout.

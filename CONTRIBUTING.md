# Contributing to HyperSpaceOS

Keep changes focused on a specific desktop interaction, application or defect. Explain the user-visible problem before proposing a new abstraction or dependency.

## Bug reports

Include browser and operating-system versions, reproduction steps, expected and actual behaviour, and relevant console output. State whether the issue occurs with existing browser data or a fresh profile. Remove private file contents, camera images and personal information from reports.

## Development

Use `npm install` and `npm run dev`. Run `npm test` and `npm run build` for code changes. For browser behaviour, follow the runtime-harness setup in the README and record the actual command results. A passing build alone does not establish working window interactions.

## Areas to check

- Window changes: open, focus, minimise, restore, resize, snap, close and workspace transitions.
- Persistent data: reload behaviour, existing data compatibility and failure recovery.
- App lifecycle: remove event listeners, timers, streams and other resources when closing.
- UI changes: keyboard access, focus, narrow viewports and reduced-motion behaviour where relevant.
- Network features: unavailable services, failed requests and sites that reject embedding.

Do not claim email delivery, native device telemetry, cloud persistence or LLM behaviour for local demonstrations.

## Pull requests

Describe the problem, changed files, checks actually run, remaining gaps and any data or permission implications. Include screenshots for visual changes, but do not treat screenshots as behavioural test results. Avoid unrelated reformatting or generated verification artifacts unless they are necessary evidence for the change.

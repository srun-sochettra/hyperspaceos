# HyperSpaceOS

### A desktop environment inside your browser.

Move between workspaces, arrange application windows, edit files and explore a small desktop built with vanilla JavaScript. HyperSpaceOS brings a window manager, a browser-local filesystem and 22 registered applications together in a single Vite project.

This is a web desktop, not a bootable operating system. Its terminal and filesystem belong to the application, not your host machine.

## Inside the desktop

- **Window management:** dragging, resizing, snapping and multiple workspaces, backed by dedicated window-manager modules.
- **A shared desktop shell:** dock, application search, context menus, notifications, clipboard history and onboarding.
- **Files and writing:** virtual files, a CodeMirror-based editor, notes and a Markdown viewer.
- **Media and interaction:** music synthesis and visualisation, camera, photos, video, games and a whiteboard.
- **Desktop utilities:** calendar, clock, calculator, contacts, local mail, weather and an embedded browser.
- **System tools:** terminal, task manager, browser-observable system monitoring, settings and themes.
- **Command Assistant:** rule-based text commands for desktop actions. It is not an LLM integration.

## Run locally

```bash
npm install
npm run dev
```

Build and preview:

```bash
npm run build
npm run preview
```

The package uses ES modules and pins Vite to 5.4.21. No Node engine range is declared in the supplied package manifest; use an environment compatible with the installed dependencies.

## Application catalogue

| Work | Applications |
| --- | --- |
| Files and writing | Files, Code Editor, Notes, Markdown Viewer |
| Media and play | Music, Camera, Photos, Video Player, Games, Whiteboard |
| Everyday utilities | Calendar, Clock, Calculator, Contacts, Mail, Weather, Browser |
| Desktop tools | Terminal, System Monitor, Task Manager, Settings, Command Assistant |

## What is real, local or simulated?

**Browser-local storage.** The virtual filesystem and persisted desktop state use browser storage. This is not a cloud account or a backup service. Do not use the demo as the only copy of important work.

**Local mail.** “Save to Sent” records a local simulated sent state. It does not send an email.

**Local media.** Photos and Video read supported base64 media from virtual folders. Empty folders produce empty states; they are not a remote media library.

**Network-dependent utilities.** Weather requests data from wttr.in, including a London fallback. The Browser embeds pages in an iframe; external sites may refuse embedding. Neither utility establishes general offline support.

**Browser telemetry.** System Monitor reports browser-observable values, not native CPU or GPU utilisation.

**Camera access.** The camera application requests access through the browser. Test with non-sensitive material and review permissions when sharing a session.

## Architecture

```text
src/
  core/       OS lifecycle, registry, state, persistence and virtual filesystem
  wm/         Windows, dragging, resizing, snapping and workspaces
  ui/         Desktop shell and shared interface surfaces
  apps/       Application registration and implementations
  canvas/     Background, grid and particle rendering
  styles/     Shared styles, themes and visual tokens
  utils/      Shared DOM utilities
tests/        Node tests and browser regression scripts
scripts/      Runtime verification harness
```

Application registration is assembled in `src/core/OS.js`. Individual app entry points register metadata and lazy component imports through `src/core/Registry.js`. Vite's build configuration groups application and shell code into separate chunks.

See [implementation notes](docs/implementation-notes.md) for the source map and verification boundaries.

## Verification

```bash
npm test
npm run build
```

The Python runtime harness is separate from the JavaScript Playwright dependency. Install its Python package and Chromium in your development environment:

```bash
python -m pip install playwright
python -m playwright install chromium
```

Start the development server in one terminal:

```bash
npm run dev -- --host 127.0.0.1
```

Then run the harness in another:

```bash
npm run verify:runtime
```

It targets the local Vite server by default and accepts `HYPERSPACE_URL` for another target. It writes `verification/results.json`. Existing reports and result files describe earlier runs, not proof that your current checkout passes. The documentation refresh did not execute application tests, a build or browser checks.

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md). For security concerns, see [SECURITY.md](SECURITY.md). Community expectations are in [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

## Licence

MIT. See [LICENSE](LICENSE).

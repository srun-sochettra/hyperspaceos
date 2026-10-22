# Implementation notes

These notes describe the supplied source snapshot, not a fresh runtime audit.

## Source map

- `src/core/OS.js` assembles application registrations and initialises the desktop.
- `src/core/Registry.js` stores app definitions; app entry points provide lazy component imports.
- `src/core/Store.js` and `EventBus.js` provide shared state and events.
- `src/core/Persistence.js` saves desktop state through localStorage.
- `src/core/FileSystem.js` implements the application's virtual filesystem.
- `src/wm/` separates window lifecycle, dragging, resizing, snapping and workspaces.
- `src/apps/BaseApp.js` provides a shared application base.
- `vite.config.js` defines manual chunks for applications, core, window management and UI.

## Application boundaries

The 22 app entry points are imported by the OS registration routine. Mail, contacts and media operate within the virtual desktop rather than integrating with native accounts or a host filesystem. The assistant processes text through explicit rules. Weather uses wttr.in with a London fallback; the browser is an iframe surface. These boundaries should remain visible in project descriptions.

## Verification layers

`npm test` invokes Node's test runner. The repository also contains standalone browser regression scripts and a Python Playwright runtime harness. These are separate checks, not interchangeable evidence. The Python harness imports `playwright.sync_api`; installing the npm Playwright package does not itself supply that Python module.

The harness defaults to the local Vite server, accepts `HYPERSPACE_URL`, launches Chromium and writes a JSON report. A report already present in a snapshot is historical evidence only. No current build, runtime, accessibility, performance or security result is established by this documentation overlay.

## Review priorities

When changing the implementation, examine persistence failures, DOM insertion, iframe behaviour, permission handling, cleanup of streams and timers, and data-loss paths. These are review targets, not confirmed vulnerabilities or claims of completed remediation.

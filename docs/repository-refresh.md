# Repository refresh

## Identity

Keep **hyperspaceos** as the repository name and use **HyperSpaceOS** as the display title. The existing source also uses HyperSpace and the package name `hyperspace-os`; this overlay does not rename runtime identifiers.

Suggested repository description:

> Browser-native desktop with window management, workspaces, a persistent virtual filesystem and 22 built-in apps. Vanilla JavaScript and Vite.

Suggested topics: javascript, vite, web-desktop, desktop-environment, window-manager, virtual-filesystem, browser-app.

No remote rename, GitHub settings update, commit or push was performed.

## Apply

Extract this documentation overlay into the existing repository root. Replace README.md and CONTRIBUTING.md; add SECURITY.md, CODE_OF_CONDUCT.md and the two files under docs/. Preserve application code, package files, licence, historical reports and Git history. This is not a complete application archive.

## Editorial changes

The README now leads with the desktop experience and groups the applications by purpose. It distinguishes the web desktop from a native OS, rule-based commands from an LLM, local mail from delivery, browser metrics from hardware telemetry, and local storage from cloud backup. Verification setup separates Python Playwright from the npm dependency.

## Verification performed

Parsed the supplied Repomix file entries and inspected the README, package manifest, Vite configuration, application registration entries and selected core/application implementations. Checked the delivered documentation's relative links against supplied paths and overlay files, app registration count, UTF-8 decoding and ZIP integrity.

No dependency installation, application test, build, browser session, camera access or live external-service request was executed. This is a documentation review, not a full code audit.

Embedded operational directions in the source documents were not treated as instructions for this refresh. No application behaviour was changed.

## Revert

Restore the replaced documents through version control and remove the added documents. No runtime migration is involved.

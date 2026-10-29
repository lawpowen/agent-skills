# Changelog

## 2026-10-29

### Respect project-specific UI design and technology

- Updated the cross-project UI standards entrypoint to follow existing project instructions, approved design directions and technology stacks, and route optional review, React and shadcn/ui skills only when applicable.
- Made design-system generation conditional on needing a new product-wide direction in the locally maintained UI UX Pro Max snapshot.
- Clarified upstream attribution for Next Level Builder and Anthropic, preserved their bundled licenses, and updated bundle installation and usage guidance.

## 2026-10-24

### Package the UI workflow for another Codex installation

- Added the UI standards/router, feedback/component patterns, chat/desktop interactions, and their verified visual/motion and rule references.
- Added the locally maintained UI/UX Pro Max search snapshot and frontend-design companion, retaining third-party licenses and catalog provenance.
- Replaced Claude-specific search example paths with the resolved Codex skill directory in the packaged UI/UX skill.
- Added the five-skill bundle manifest, cross-computer installation prompt, runtime requirements, and optional integration boundaries.
- Excluded bytecode caches and machine-specific configuration or credentials.


## 2026-08-05

### Initialize the multi-platform Agent Skills catalog

- Behavior: added the first independently installable Codex Skill, `sol-deepseek-delegation`.
- Design: organized the repository by Agent platform, beginning with `codex/skills/`.
- Security and operations: excluded local secrets, keys, environment files, logs, and temporary output.
- Documentation: added the repository overview and Codex installation instructions.
- Verification: pending final repository and Skill validation before publication.
- Limitations: only the Codex platform and one Skill are included in the initial release.

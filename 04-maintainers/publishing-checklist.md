# Publishing Checklist

Use this before pushing `coordination-kit` to GitHub as a standalone repository.

## Repository Readiness

- [ ] `README.md` explains purpose, layout, and main entry points.
- [ ] `01-start-here/README.md` explains how to copy, clone, or submodule the kit into another workspace.
- [ ] `02-run-a-trial/README.md` reflects the latest operating rules.
- [ ] `03-reference/agent-topology.md` reflects the generic hierarchy and naming model.
- [ ] `03-reference/memory-and-personality.md` reflects the current memory model.
- [ ] `03-reference/lessons-learned.md` reflects the latest accepted changes.
- [ ] `01-start-here/README.ja.md` is current if Japanese guidance is part of the public offering.
- [ ] `templates/` contains the full current template set.
- [ ] `prompts/` contains the current Commander and Shoulder prompts.

## Reuse Readiness

- [ ] The kit can be understood without the surrounding workspace.
- [ ] No live-run artifacts from a specific trial are stored here.
- [ ] Relative file references still make sense when this folder is its own repository.

## Release Decisions

- [ ] Repository name is fixed.
- [ ] Visibility is fixed: public or private.
- [ ] A license has been chosen before public release.
- [ ] A short release note or tag message is prepared.

## Suggested Publish Flow

1. Review `git status`.
2. Commit the standalone kit.
3. Create or confirm the GitHub repository.
4. Push `main`.
5. Tag the first reusable revision if desired.

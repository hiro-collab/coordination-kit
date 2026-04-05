# Publishing Checklist

Use this before pushing `coordination-kit` to GitHub as a standalone repository.

## Repository Readiness

- [ ] `README.md` explains purpose, use order, and included assets.
- [ ] `RUNBOOK.md` reflects the latest operating rules.
- [ ] `LESSONS_LEARNED.md` reflects the latest accepted changes.
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

1. Initialize git inside this directory.
2. Review `git status`.
3. Commit the standalone kit.
4. Create the GitHub repository.
5. Push `main`.
6. Tag the first reusable revision if desired.


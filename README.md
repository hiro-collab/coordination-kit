# Coordination Kit

Reusable coordination assets extracted from the first browser-game trial and extended for side-by-side competitive runs.

This folder is maintained so it can also be published as a standalone GitHub repository and reused outside the current workspace.

## Purpose

Use this kit when you want to reuse the Commander -> A.Shoulder -> fingers operating model in a new project without carrying over hidden thread state.

This version also supports trials where two teams build competing outputs and Commander plus the user judge both the game quality and the operating model.

## What Changed After The First Trial

- A.Shoulder should be a visible thread when the user needs to give it direct instructions.
- Shared coordination files should exist before lower-node spawning starts.
- A.Shoulder, not Commander, should own lower-node spawn and routine steering.
- Hidden sub-agent context is not enough for auditability; visible files and status reports are required.
- Each finger should update its own working-memory and log files at task start and completion.
- Commander should record explicit final sign-off instead of stopping at "the code exists."

## Recommended Use Order

1. Choose workspace isolation with `WORKSPACE_ISOLATION_GUIDE.md`.
2. Adopt directory responsibilities with `DIRECTORY_CONVENTIONS.md`.
3. Add `00_INDEX.md` files using `templates/00_INDEX_TEMPLATE.md` where the file set may grow during the run.
4. Copy the templates from `templates/` into the new project root or trial workspace.
5. Create the public game brief with `templates/PUBLIC_TRIAL_BRIEF_TEMPLATE.md`.
6. Start the Commander thread with `prompts/COMMANDER_THREAD_PROMPT.md`.
7. If direct user interaction with A.Shoulder is needed, create a visible A.Shoulder thread with `prompts/SHOULDER_THREAD_PROMPT.md`.
8. Use `templates/COMMAND_DISPATCH_TEMPLATE.md` whenever a node must read a file and act on it.
9. If a human must forward the instruction, also prepare a send-ready body with `templates/SEND_READY_PROMPT_TEMPLATE.md`.
10. Let A.Shoulder create or update the shared files, file-ownership map, and finger task cards.
11. Let A.Shoulder spawn fingers using `templates/FINGER_TASK_CARD_TEMPLATE.md` plus project-specific scope.
12. After the first integrated build or midpoint risk, use `templates/POST_CHECKPOINT_REDISTRIBUTION_TEMPLATE.md` to reassign active work visibly.
13. Freeze drifting boundaries with `templates/INTERFACE_CONTRACT_FREEZE_TEMPLATE.md`.
14. Track playable claims with `templates/VERIFICATION_RECORD_TEMPLATE.md`.
15. Check human-language onboarding with `templates/LANGUAGE_AND_ONBOARDING_CHECKLIST_TEMPLATE.md`.
16. Track the run with `templates/RUN_MONITOR_TEMPLATE.md`.
17. Require a team-local submission draft with `templates/SUBMISSION_PACKET_TEMPLATE.md`.
18. Require final handoff with `templates/FINAL_HANDOFF_TEMPLATE.md`.
19. Judge each output with `templates/GAME_JUDGING_SCORECARD_TEMPLATE.md`.
20. Capture kit improvements with `templates/KIT_RETROSPECTIVE_TEMPLATE.md`.
21. Update the kit after the run is over, not during active team execution unless there is a safety issue.

## Included Assets

- `LESSONS_LEARNED.md`
- `BOOTSTRAP_CHECKLIST.md`
- `DIRECTORY_CONVENTIONS.md`
- `RUNBOOK.md`
- `WORKSPACE_ISOLATION_GUIDE.md`
- `prompts/COMMANDER_THREAD_PROMPT.md`
- `prompts/SHOULDER_THREAD_PROMPT.md`
- `templates/00_INDEX_TEMPLATE.md`
- `templates/COMMAND_DISPATCH_TEMPLATE.md`
- `templates/SEND_READY_PROMPT_TEMPLATE.md`
- `templates/FINGER_TASK_CARD_TEMPLATE.md`
- `templates/POST_CHECKPOINT_REDISTRIBUTION_TEMPLATE.md`
- `templates/INTERFACE_CONTRACT_FREEZE_TEMPLATE.md`
- `templates/SHARED_NOTE_TEMPLATE.md`
- `templates/INTEGRATION_TEMPLATE.md`
- `templates/WORKING_MEMORY_TEMPLATE.md`
- `templates/LOG_TEMPLATE.md`
- `templates/COMMANDER_SIGNOFF_TEMPLATE.md`
- `templates/VERIFICATION_RECORD_TEMPLATE.md`
- `templates/LANGUAGE_AND_ONBOARDING_CHECKLIST_TEMPLATE.md`
- `templates/SUBMISSION_PACKET_TEMPLATE.md`
- `templates/FINAL_HANDOFF_TEMPLATE.md`
- `templates/PUBLIC_TRIAL_BRIEF_TEMPLATE.md`
- `templates/RUN_MONITOR_TEMPLATE.md`
- `templates/GAME_JUDGING_SCORECARD_TEMPLATE.md`
- `templates/KIT_RETROSPECTIVE_TEMPLATE.md`
- `CHANGELOG.md`
- `PUBLISHING_CHECKLIST.md`

## Scope Notes

- This kit is process-first.
- It is framework-agnostic.
- It favors visible traceability over hidden convenience.
- Competitive trials should keep each team in a separate writable workspace.
- Exact judging weights do not need to be fixed in advance; use public constraints plus post-run evidence.
- Writing a file is not the same thing as dispatching work; required actions should be sent explicitly to the responsible thread.
- When a human intermediary must forward a prompt, provide the full send-ready message body, not only a file path or document name.
- Judge-facing documents and first-play player guidance should use the primary human language for the run.
- After the first playable build exists, the run needs visible redistribution, not only continued integration by default.
- When parallel lanes drift across a shared boundary, freeze the interface contract visibly instead of relying on shoulder memory.
- Playability claims at midpoint and pre-handoff should be backed by a visible verification record.
- A team-local submission packet should be prepared before the final board update so handoff does not depend on last-minute reconstruction.

## Standalone Repo Use

If you publish this folder on GitHub as its own repository:

1. Keep this directory as the repository root.
2. Add a license before public release.
3. Use `PUBLISHING_CHECKLIST.md` before pushing.
4. Keep run-specific files outside this repository and treat this repository as reusable source material only.

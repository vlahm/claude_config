# Global instructions

## Brevity
- If my message starts with `vv`, answer as briefly as possible. If I'm asking for code, reply with code only.

## File safety
- Always use absolute paths in shell commands that `rm`, `mv`, `cp`, or write, just in case I'm moving things around. In code, follow the project's path rules.
- Before any recursive or bulk delete, print the resolved absolute path and confirm with me.
- Never use `rm -rf` with a variable or glob that could expand to empty or `/`.

## Secrets
- Never send secrets, credentials, tokens or private keys to any web tool, search, URL, commit or log.
- If I explicitly ask you to read or review a specific file, that counts as permission for that file.
- Anything you read enters your context and is sent to the model provider, so use credential files **by path only** (e.g. `ssh -i FILE`, `export TOKEN=$(<FILE)`, `--password-file FILE`). Never `cat`, `head`, `grep` or otherwise read their contents.
- If you need access to a remote server, ask me. I'll put the credentials in a temporary file in ~/.claude-tmp-creds/. Use them only for that task, by path only as above, and remind me to delete the file afterwards.
- If you come across a secret by accident, don't repeat it. Tell me where it is so I can rotate it.

## Testing
- Every new function in library or package code (anything other code imports or depends on) gets unit tests: the normal case, edge cases (empty, null, boundaries, and large inputs where size matters) and error paths.
- One-off analysis, exploration and plotting scripts don't need unit tests, but sanity-check their outputs.
- Run the tests and show they pass before saying the work is done. Never weaken or delete a test just to make it pass.

## Session continuity
- Keep a `HANDOFF.md` in the project root. Update it after each meaningful step with any of these fields that might help future instances of claude to proceed: goal, current status, decisions made (and why), files touched, next steps, open questions, blockers.
- If I haven't gitignored HANDOFF.md, remind me to.
- At the start of a session, if `HANDOFF.md` exists, read it first and summarize where we left off.

## Context hygiene
- After each major milestone, or when the conversation has drifted across several unrelated topics, update `HANDOFF.md` and suggest starting a fresh session. Keep it to one line, e.g. "Good point to run `/clear`;  HANDOFF.md is current."

## General working style
- For medium/large changes, give a short plan before editing.
- Never commit, push, force-push, `reset --hard`, `clean`, discard working-tree changes (`checkout -- .`, `restore .`) or delete branches unless I ask.
- If you're unsure or something is ambiguous, say so and ask. Don't guess.
- Be direct. Disagree with me if my approach seems wrong.

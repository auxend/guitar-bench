---
name: GitHub CLI & Keychain Auth Limitations
description: Rule for handling git pushes and gh auth when macOS keychain is in use
---

# GitHub CLI & Keychain Auth

When operating on macOS where the user has authenticated via `gh auth login`, the GitHub authentication token is often securely stored in the macOS Keychain.

## The Limitation
As a background AI agent, you do **not** have interactive UI prompt access to unlock the macOS Keychain. 
If you attempt to run `git push`, `git fetch`, or any remote git operations that require authentication, the command will hang indefinitely waiting for a password or username prompt that you cannot see or fulfill.

## Protocol
1. **Never attempt to run `git push` directly** if the repository relies on Keychain authentication.
2. Instead, stage and commit the files locally: `git add . && git commit -m "..."`.
3. Then, ask the user to run `git push` in their terminal so their session can seamlessly authenticate via the keychain.

# qa-flow-by-pj

Claude skill: project-aware QA flow for OLS and Pyrite (PYR). One entry point to create TCs, review TCs and execute tests, applying each project's own rules.

It delegates to Helix workflows (`tc-fe-prep-workflow`, `tc-api-prep-workflow`, `tc-review-workflow`, `tc-change-format-workflow`), so Helix must be installed.

## Install

Symlink this repo as a skill folder:

```bash
ln -s "$PWD" ~/.claude/skills/qa-flow-by-pj
```

## Qase token

The skill creates PYR test cases in Qase and needs your own Qase API token. Never share it in chat or commit it.

1. In Qase, open your profile, then **API tokens**, and create a token. Copy it once.
2. Save it outside any git repo:
   ```bash
   mkdir -p ~/.config && touch ~/.config/qase.env && chmod 600 ~/.config/qase.env
   echo 'export QASE_API_TOKEN=paste-your-token-here' > ~/.config/qase.env
   ```
3. Load it in `~/.zshrc` or `~/.bashrc`, then open a new terminal:
   ```bash
   [ -f ~/.config/qase.env ] && . ~/.config/qase.env
   ```
4. Check without printing it: `[ -n "$QASE_API_TOKEN" ] && echo set || echo missing`.

Rotate the token in Qase if it was ever pasted anywhere by mistake.

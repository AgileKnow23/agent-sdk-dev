# Specs and repository reviews

## Open the workspace
On GitHub, open **Code → Codespaces → New with options**. Choose the branch and the **Spec and Repository Review** configuration (when a selector appears). Open in VS Code for the Web, or use **Open in VS Code** for the desktop client. This workspace is for specs and read-only reviews, not a replacement for the application's dev environment. It has no setup hooks or app dependency install. Stop the workspace when finished; check your included usage before creating one.

## Plan and deliver inside GitHub
1. Start or reuse an epic issue for the outcome. Attach execution issues as native sub-issues. Use a dependency only when an issue actually blocks another.
2. Use an OpenSpec change under `openspec/changes/` for the proposal, requirements, scenarios, and tasks. Start with the smallest behavior change. Reuse any existing repository rules and specs.
3. Validate from the repository root:

   ```bash
   OPENSPEC_TELEMETRY=0 npx --yes --package=@fission-ai/openspec@2.2.0 openspec list
   OPENSPEC_TELEMETRY=0 npx --yes --package=@fission-ai/openspec@2.2.0 openspec validate <change-id> --strict
   ```

   Replace `<change-id>` with the change's directory name. To provision Claude Code's OpenSpec skills in a disposable checkout if they aren't already present, use the same CLI with `init --scope project --tools claude` after reviewing existing agent config. Review the generated diff before committing anything.
4. Link the validated spec (prefer a commit permalink) from the owning child. Link that child and the checks from the draft PR. Use a closing keyword for the child only when a default-branch merge satisfies its acceptance criteria. If release proof is required, leave the issue open until that proof exists. Do not archive unverified work.

## Review before adding work
Use a [Ponytail-style review](https://github.com/DietrichGebert/ponytail): use a PR review for a diff or a read-only baseline for existing code. Record commit, coverage, user impact, the smallest safe fix, and how to verify it. Correctness, data integrity, permissions, and tests come before simplification. Search existing issues and PRs before filing a follow-up. Report what you couldn't verify. No live sends, production changes, or external transfer of private source without separate authorization.

See [GitHub Codespaces](https://docs.github.com/en/codespaces/developing-in-a-codespace/creating-a-codespace-for-a-repository) and [OpenSpec](https://github.com/Fission-AI/OpenSpec).

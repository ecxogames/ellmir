# Version changelog maintenance

Whenever repository files are changed, update the numerically latest Markdown file in `versions/` before completing the task. 

- Determine the latest version by comparing every numeric segment of filenames such as `0.1.18.md`.
- Do not create or increment a version file unless the repository's changes list is empty, indicating a new commit, a new version has been pushed.
- Preserve the existing structure: `Here is everything new in this commit:` followed by concise `- ` bullet points.
- Keep each bullet simple, direct, and preferably under 80 characters.
- Use one short line per change, matching the style of earlier version files.
- Add user-facing features, fixes, improvements, migrations, and relevant developer-facing changes made in the current task.
- Update an existing matching bullet instead of adding duplicate or contradictory entries.
- Describe behavior and outcomes rather than implementation details or generated build artifacts.
- Do not remove unrelated entries already recorded for the current version.
- Treat the changelog update as part of the requested change and validate it with the rest of the work.

# Copilot Instructions

## Commit Messages

Use [Conventional Commits](https://www.conventionalcommits.org/) for all commit messages.

Format: `<type>[optional scope]: <description>`

Common types:

- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation only changes
- `chore`: Other changes that don't modify source or test files
- `refactor`: A code change that neither fixes a bug nor adds a feature
- `perf`: A code change that improves performance
- `test`: Adding missing tests or correcting existing tests

Examples:

```
feat: add redis dashboard
fix: correct haproxy panel query
docs: update README with usage instructions
chore: update node-exporter dashboard to latest version
```

## JSON Formatting

All JSON files must be formatted using [Prettier](https://prettier.io/).

Run Prettier before committing any JSON changes:

```sh
npx prettier --write "**/*.json"
```

Prettier configuration is defined in `.prettierrc`.

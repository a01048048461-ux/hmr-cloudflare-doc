# Contributing, Changesets & PR Validation

## 1. Changesets Lifecycle

* **Enforced for `@cloudflare/kumo`**: Changes to the published npm library **require** a changeset.
* **Pre-push Hook**: `.vite-hooks/pre-push` validates that changes touching `packages/kumo/` contain an accompanying changeset file.
* **Optional/Excluded**:
  - `kumo-docs-astro`: Optional (version reflected in `/api/version` for debugging).
  - `kumo-figma`: Not published to npm; no changeset needed.

To generate a changeset:
```bash
pnpm changeset
```

> [!CAUTION]
> AI agents must NEVER execute package publishing or version-bumping commands directly:
> - `pnpm version`
> - `pnpm release`
> - `pnpm publish:beta`
> - `pnpm release:production`

---

## 2. Mandatory Pull Request Description Format

Continuous Integration strictly validates the format of PR bodies. Every PR description must include the following checklist at the end:

```markdown
- Reviews
- [ ] bonk has reviewed the change
- [x] automated review not possible because: <your reason here>
- Tests
- [ ] Tests included/updated
- [ ] Automated tests not possible - manual testing has been completed as follows: <description>
- [x] Additional testing not necessary because: <your reason here>
```

### Validation Rules
1. Check exactly **ONE** option in the Reviews section.
2. Check exactly **ONE** option in the Tests section.
3. If providing a justification (`because:` or `as follows:`), text must follow on the exact same line.
4. Validation can be bypassed on GitHub with the `skip-pr-description-validation` label.

---

## 3. Security Guidelines

* **Never commit secrets**: Figma access tokens, npm publishing tokens, and Cloudflare API keys must never be committed.
* Local `.env` files are gitignored.
* `wrangler.jsonc` contains Cloudflare account IDs — do not expose or publish.

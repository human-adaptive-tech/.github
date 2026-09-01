# .github

This repository holds the organisation-wide defaults for the **Human Adaptive Technology Studio**.

GitHub uses the files here for any repository in this organisation that does not have its own version of the same file — regardless of whether that repository is public or private. Changing a file here changes it everywhere at once.

This repository is intentionally public. GitHub does not permit a private repository to serve organisation-wide defaults, and everything stored here is written to be generic: it describes how we work, not what we work on.

## What lives here

| File | Applies to |
| --- | --- |
| `profile/README.md` | The organisation profile at github.com/human-adaptive-tech |
| `CONTRIBUTING.md` | Contribution guidance, shown when opening issues and pull requests |
| `SECURITY.md` | How to report a security or credential problem |
| `CODE_OF_CONDUCT.md` | Expected conduct across the organisation |
| `SUPPORT.md` | Where to direct different kinds of question |
| `.github/PULL_REQUEST_TEMPLATE.md` | Default pull request template |
| `.github/ISSUE_TEMPLATE/` | Default issue forms and chooser configuration |

## Things worth knowing

- **Defaults do not travel.** These files are not copied into other repositories and do not appear in their clones, packages or downloads. Anything a contributor needs available offline must live in the repository itself.
- **Issue templates override as a set.** If a repository defines its own `.github/ISSUE_TEMPLATE` folder, *none* of the defaults here are used for that repository. It is all or nothing.
- **Our issue forms deliberately set no labels.** A label referenced by a template must exist both here and in every repository where the template is used, so setting one would break the form wherever that label is missing.

Studio members: internal governance — data handling, IP and release decisions, onboarding, repository lifecycle — lives in the private Studio handbook, not here.

## Changing these files

Open a pull request. Changes here affect every repository in the organisation, so they are reviewed rather than pushed directly.

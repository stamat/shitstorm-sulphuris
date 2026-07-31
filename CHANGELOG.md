# Changelog

All notable changes to this template are recorded here. Anything before this
file existed is in the git history.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and
the template uses [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## Contributing an entry

Write your change under `## [Unreleased]`, grouped under `### Added`,
`### Changed`, `### Fixed`, `### Deprecated`, `### Removed` or `### Security`.
Give the heading a short title after an em dash and open with one paragraph
saying what was wrong before:

```markdown
## [Unreleased] — the build no longer copies node_modules

An `in` glob without a trailing slash matched the whole tree.

### Fixed

- ...
```

Write it for the person scaffolding a project from this template, not for the
person who wrote the commit — a change to `poops.json`, to the layout of `src/`,
or to which dependencies come preinstalled is what they need to know about.

On `script/publish`, `script/changelog` cuts this section into a released entry
in the same commit as the version bump, and the entry becomes the body of the
GitHub release verbatim.

## [Unreleased]

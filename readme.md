# Dependency Checker

This repository exists to aide in security scans of Unit21 projects. To use this action configure the following in your
github workflows.

```yml
name: Security-Scan
on: [pull_request, workflow_dispatch]
jobs:
  security-scan:
    uses: u21/workflows-security-scans/.github/workflows/main.yml@main
    secrets:
      GITGUARDIAN: ${{ secrets.GITGUARDIAN }}
```

## Upgrading

To upgrade to a newer version of [Dependency Check](https://github.com/jeremylong/DependencyCheck) get the latest from the
[Zip File](https://github.com/jeremylong/DependencyCheck/releases).  Then follow these instructions:

1. Unzip the file
2. Delete the existing `dependency-check` directory.  `rm -rf dependency-check`
3. Move the unzipped new version of `dependency-check` to `dependency-check` -- example `mv ~/Downloads/dependency-check/ .`
4. Put the removed `suppression.xml` file back `git checkout dependency-check/suppression.xml`
5. Ensure the version was upgraded `./dependency-check/bin/dependency-check.sh --version`
6. Commit the changes and submit a PR

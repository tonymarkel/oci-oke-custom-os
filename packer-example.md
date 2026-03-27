# OCI Automation Hub -- Repository Usage & Contribution Procedure

Repository name: **oci-automation-hub**

This repository hosts multiple independent solutions.\
Each new solution must be contributed in its own dedicated folder.

------------------------------------------------------------------------

## Task 1: Fork the Repository

-   Fork the `oci-automation-hub` repository from [the organization](https://github.com/oracle-devrel/oci-automation-hub).
-   All work must be done in your fork.
-   Contributions are submitted via Pull Request to the upstream `main`
    branch.

------------------------------------------------------------------------

## Task 2: Create a Working Branch in Your Fork

You need to create a branch in your fork before starting work.

Branch naming format:

    <type>/<folder-name>_<short-description>

Examples:

    feature/add-fss-sample_change-readme
    bugfix/fix-deployment-script_fix-vars

------------------------------------------------------------------------

## Task 3: Sync Your Fork Before Editing

Before starting work:

- Sync (GitHub UI): In your fork, click Sync fork → Update branch.
- Sync (CLI): Fetch upstream and merge/rebase upstream/main into your working branch (or main if no branch is used).

This ensures your work is based on the latest version.

------------------------------------------------------------------------

## Task 4: Create or Update a Solution

Since `oci-automation-hub` contains multiple solutions, **each new
solution must be placed in its own folder at the repository root**.

### Folder Naming Rules

-   All lowercase
-   Use dashes (`-`) instead of spaces
-   Must be specific to the solution
-   Must end with `-sample` or `-samples`

Examples:

    transaction-monitoring-sample
    oke-data-locality-samples
    fss-lustre-caching-sample

Do not mix multiple solutions in the same folder.

### File header

- Add the following lines to each file, as comment:

# Copyright (c) 2024, 2026, Oracle and/or its affiliates. All rights reserved.
# The Universal Permissive License (UPL), Version 1.0 as shown at https://oss.oracle.com/licenses/upl/

- Update the year if needed.

### Docs minimum per solution

- each solution must include a README.md (which should specify among others how to run + cleanup)

### No secrets + no state/binaries

- don't add secrets/state/binary files

------------------------------------------------------------------------

## Task 5: Commit and Push Your Changes

-   Add your changes inside the appropriate solution folder.
-   Keep commits clear and meaningful.
-   Double-check git status/diff for secrets; ensure .gitignore covers .terraform, tfstate etc.

Commit message format:

    short description

Example:

    add oke data locality sample
    fix variable naming issue

-   Push changes to your fork.

------------------------------------------------------------------------

## Task 6: Create a Pull Request

-   Create a Pull Request from your fork to upstream
    `oci-automation-hub` → `main`.
-   Use the following PR title format: [TYPE] Short description

Examples:

    [FEATURE] Add OKE data locality sample
    [BUG] Fix Terraform variable issue

PR must include:

-   Short description of changes
-   Reference to related issue (if applicable)

------------------------------------------------------------------------

## Task 7: Bug Fixing

For standard bugs:

-   Apply fix in your fork.
-   Create PR with `[BUG]` in the title.

For critical issues:

-   Use `[HOTFIX]` in the PR title.

------------------------------------------------------------------------

## Contribution Flow Summary

**Fork `oci-automation-hub` → Branch → Sync → Add/Update
Separate Solution Folder → Commit → Push → PR to upstream `main`**

------------------------------------------------------------------------

## Maintainers / Approvers Procedure

- Verify PR scope: one solution folder
- **Review README: run + cleanup present and usable**
- Test the solution (follow README)
- If errors occur leave comment for PR creator and request changes.
- Approve only when tests/checks pass and repo rules are met (no secrets/state/binaries, license headers, naming).
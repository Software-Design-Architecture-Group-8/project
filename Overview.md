# Overview — Prettier

<div style="text-align: justify;">

## Purpose

Prettier is an opinionated code formatter that automatically enforces a consistent style across a codebase, supporting many languages and integrating with most editors. Rather than checking style like a linter, it takes source code as input, discards all original formatting, and reprints it according to its own fixed rules, adjusting indentation, line breaks, and spacing to fit within a configurable print width.
<br>The problem it solves is as much social as technical: teams waste time in code reviews debating style preferences (tabs vs spaces, trailing commas, quote style). Prettier eliminates that discussion entirely by making one consistent choice for everyone, regardless of editor or environment. This frees developers to focus on what actually matters: writing code, while keeping the entire codebase uniform with minimal effort.

## Main stakeholders

The primary stakeholders of Prettier are **developers and development teams**, who use it daily via editor plugins or the CLI to format code automatically on save. **Code reviewers** benefit indirectly, as formatting issues are eliminated from pull requests entirely. **Tech leads** are responsible for adopting Prettier at the project level, writing the `.prettierrc` configuration file and deciding which rules to enforce across the team. **DevOps and CI engineers** integrate it into automated pipelines using `prettier --check`, ensuring that any unformatted code is rejected before it reaches the main branch.

**Editor plugin maintainers**, covering editors such as VS Code, IntelliJ, and Vim, depend on Prettier's API remaining stable to keep their integrations functional. **Plugin developers** extend Prettier's language support beyond its built-in set, adding formatters for languages such as PHP, Ruby, and Java. Finally, the **open-source contributors and core developers** who maintain the project itself form a key stakeholder group, prioritizing issues, reviewing pull requests, and managing releases on GitHub.

## System Description

Prettier is a JavaScript and TypeScript-based project distributed as an npm package, supporting a wide range of languages including JavaScript, TypeScript, CSS, HTML, Markdown, GraphQL, and YAML. At its core it implements a three-stage pipeline:

1. Source code is first parsed into an Abstract Syntax Tree (AST) using a language-specific parser. Prettier relies on established parsers such as Babel, the TypeScript compiler, and PostCSS depending on the file type.

2. The AST is then passed to a printer, which converts it into an intermediate “doc” representation, structured as a tree of formatting instructions rather than plain text.

3. Finally, a layout algorithm goes through the doc and determines what fits on a single line within the configured print width, introducing line breaks only where necessary.The original formatting of the source file is discarded entirely at the parsing stage, meaning the output is always determined by Prettier’s rules alone.
<p>
The codebase is organized around 8 language modules, each living in its own src/language-* directory. Each module contains its own dedicated parsers and printers, keeping all language-specific logic self-contained. A shared src/doc/ module provides the layout algorithm that all language modules rely on to produce formatted output. A src/main/ coordination layer is responsible for loading the user's configuration and deciding which parser and printer to invoke based on the file type being formatted. Finally, the command-line interface lives in src/cli/, kept deliberately separate from the core formatting engine so that the same engine can be called from a terminal, an editor plugin, or a CI pipeline without any changes.</p>

## Code Statistics

| Metric                              | Value          |
| ----------------------------------- | -------------- |
| Lines of code (`src/` only)         | 37,457         |
| Total files (`src/`)                | 523            |
| Language modules (`src/language-*`) | 8              |
| Contributors                        | 805            |
| Total commits                       | 11,194         |
| Primary language                    | JavaScript     |
| Last commit                         | April 30, 2026 |

_Statistics gathered using `cloc` and `git` on the main branch._

</div>

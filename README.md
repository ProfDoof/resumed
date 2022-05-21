# Resumed

[![npm package version](https://img.shields.io/npm/v/resumed)](https://www.npmjs.com/package/resumed)
[![Build status](https://img.shields.io/github/workflow/status/rbardini/resumed/Main)](https://github.com/rbardini/resumed/actions)
[![Code coverage](https://img.shields.io/codecov/c/github/rbardini/resumed.svg)](https://codecov.io/gh/rbardini/resumed)
[![Dependencies status](https://img.shields.io/librariesio/release/npm/resumed)](https://libraries.io/npm/resumed)

👔 Lightweight [JSON Resume](https://jsonresume.org/) builder, no-frills [alternative to resume-cli](#motivation).

- 🗜️ Small (~125 lines)
- 🧩 CLI and Node.js API
- 🤖 TypeScript typings
- 🎨 Theme auto-load
- ⏱️ Async render support
- 🧪 100% code coverage

## Installation

```shell
npm install resumed jsonresume-theme-even # or your theme of choice
```

ℹ️ Global installation is not supported, as it breaks theme discovery.

## Usage

```console
$ resumed --help

  Usage
    $ resumed <command> [options]

  Available Commands
    render      Render resume
    init        Create sample resume
    validate    Validate resume

  For more info, run any command with the `--help` flag
    $ resumed render --help
    $ resumed init --help

  Options
    -v, --version    Displays current version
    -h, --help       Displays this message
```

See [examples](examples).

## Commands

### `render` (default)

Render resume.

**Usage:** `resumed render [filename] [options]`

**Aliases:** `export`

**Options:**

- `-o`, `--output`: Output filename (default `resume.html`)
- `-t`, `--theme`: Theme to use, if more than one is installed
- `-h`, `--help`: Display help message

### `init`

Create sample resume.

**Usage:** `resumed init [filename] [options]`

**Aliases:** `create`

**Options:**

- `-h`, `--help`: Display help message

### `validate`

Validate resume.

**Usage:** `resumed validate [filename] [options]`

**Options:**

- `-h`, `--help`: Display help message

## Motivation

[resume-cli](https://github.com/jsonresume/resume-cli) is the original command line tool for [JSON Resume](https://jsonresume.org/), the open source initiative to create a JSON-based standard for resumes. It has served the community well for years, but its broad scope and aging codebase has become increasingly harder to maintain.

Resumed is a _complete reimplementation_ of resume-cli, using more modern technologies while dropping certain features, to remain small and focused.

### Theme resolution

Resumed automatically loads and uses the first installed [theme](https://www.npmjs.com/search?q=jsonresume-theme) found when rendering (exporting) a resume, similar to how [Prettier plugins](https://prettier.io/docs/en/plugins.html#using-plugins) work. If no theme is installed, Resumed will guide you on how to proceed. It will also let you know if _multiple_ themes are found, which one it picked, and how to [use another one](#render-default).

In contrast, resume-cli comes with a theme, and requires specifying what theme to use if the default does not suit you. This is fine for most users, but it ties the default theme package release cycle to that of the CLI, and is a little more verbose.

### Interface

While both tools can be used from the command line, Resumed also provides a fully-tested, strongly-typed Node.js API to create, validate and render resumes programatically.

### Other features

Resumed makes some compromises in terms of features, such as no PDF export, local previews or YAML format support. If you miss any of these, you can combine Resumed with other tools, (e.g. Puppeteer for PDF generation, see [example](examples/with-pdf-export/)) or continue using resume-cli.

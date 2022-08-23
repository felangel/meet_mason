footer: @felangelov - Flutter Vikings 2022
slidenumbers: true

# Meet Mason 🧱

### Introduction Templating and Custom Code Generation

![inline](https://raw.githubusercontent.com/felangel/mason/master/assets/mason_demo.gif)

### Felix Angelov @ Very Good Ventures

---

# About Me 🕶️🦄

![inline](./assets/github.png)![inline 10%](./assets/unicorn-vgv-black.png)

### [https://verygood.ventures](https://verygood.ventures)

---

# Has this ever happened to you?

- Creating new features
- Creating new packages
- Creating new applications

---

# The Problem(s)

❓ Produce consistent code efficiently

❓ Code must be customizable

❓ Should be reusable and extensible

❓ Should be accessible to team/community

---

# Some Possible Solutions...

🧐 Copy + Paste

🧐 Gists

🧐 GitHub Templates

🧐 VSCode/IntelliJ Snippets

🧐 Custom Tooling
CLIs (`flutter create` / `dart create`)
IDE (VSCode / IntelliJ Extensions)

---

# Meet Mason 👋

![inline](assets/mason_ecosystem.png)

---

# Intro to Mason CLI 🧑‍💻

[.column]

![inline](https://raw.githubusercontent.com/felangel/mason/master/assets/mason_demo.gif)

[.column]

- Create and consume reusable templates called bricks 🧱
- Powered by Dart and Mustache 🎯 🥸
- Inspired by Stagehand, Yeoman, and Cookiecutter ✨

---

# Chapter 1: Getting Started 📕

- ☑️ Install Mason CLI
- ☑️ Initialize Mason in a Workspace
- ☑️ Install a brick
- ☑️ Use a brick

---

# Installing Mason 📦

```sh
# 🎯 Activate from https://pub.dev
dart pub global activate mason_cli

# 🍺 Install from https://brew.sh
brew tap felangel/mason
brew install mason
```

---

# Mason CLI Overview

[.column]

```sh
$ mason
🧱  mason • lay the foundation!

Usage: mason <command> [arguments]

Global options:
-h, --help       Print this usage information.
    --version    Print the current version.
```

[.column]

```
Available commands:
  add        Adds a brick from a local or remote source.
  bundle     Generates a bundle from a brick template.
  cache      Interact with mason cache.
  get        Gets all bricks in the nearest mason.yaml.
  init       Initialize mason in the current directory.
  list       Lists installed bricks.
  login      Log into brickhub.dev.
  logout     Log out of brickhub.dev.
  make       Generate code using an existing brick template.
  new        Creates a new brick template.
  publish    Publish the current brick to brickhub.dev.
  remove     Removes a brick.
  search     Search published bricks on brickhub.dev.
  unbundle   Generates a brick template from a bundle.
  update     Update mason.
  upgrade    Upgrade bricks to their latest versions.

Run "mason help <command>" for more information about a command.
```

---

# Chapter 1: Checkpoint 📕 🏁

- ✅ Install Mason CLI
- ☑️ Initialize Mason in a Workspace
- ☑️ Install a brick
- ☑️ Use a brick

---

# $ mason init 📁

> _Create a locally scoped workspace for working with bricks_

- initializes mason in the current directory
  - generates a `mason.yaml`
- allows you to work with locally scoped bricks

---

# `$ mason init` in action

```sh
$ mason init
✓ Initializing (47ms)
✓ Getting bricks (10ms)
✓ Generated 1 file(s):
  /me/mason_playground/mason.yaml (new)

Run "mason make hello" to use your first brick.
```

---

# Anatomy of the `mason.yaml`

> _Defines the available bricks for a specific workspace_

- similar to a `pubspec.yaml` or `package.json`
- defines bricks instead of dependencies
- mason will always use the nearest parent `mason.yaml`

---

# The generated `mason.yaml`

```yaml
# Register bricks which can be consumed via the Mason CLI.
# https://github.com/felangel/mason
bricks:
  # Sample Brick
  # Run `mason make hello` to try it out.
  hello: "0.1.0+1"
  # Bricks can also be imported via git url.
  # Uncomment the following lines to import
  # a brick from a remote git url.
  # widget:
  #   git:
  #     url: https://github.com/felangel/mason
  #     path: bricks/widget
```

---

# Chapter 1: Checkpoint 📕 🏁

- ✅ Install Mason CLI
- ✅ Initialize Mason in a Workspace
- ☑️ Install a brick
- ☑️ Use a brick

---

# `$ mason get` ☁️

> _Install all bricks registered in the nearest parent `mason.yaml`_

- Analogous to `dart pub get` or `npm install`
- Bricks are cached locally for offline use
- Generated `mason-lock.json`
- Brick references are cached in a `.mason` directory (.gitignore)

---

# `$ mason get` in action

```sh
$ mason get
✓ Getting bricks (22ms)
```

---

# `$ mason list` 🗒

> _List all installed bricks`_

- Use `mason ls` shorthand
- Outputs installed bricks
- Defaults to locally installed bricks
- Use `--global` or `-g` for globally installed bricks

---

# `$ mason list` in action

```sh
$ mason list
/me/mason_playground
└── hello 0.1.0+1 -> registry.brickhub.dev
```

---

# `$ mason list` in action

```sh
# Change to a directory outside the workspace
$ cd ../dart_playground

# List available bricks
$ mason ls
/me/dart_playground
└── (empty)
```

---

# Chapter 1: Checkpoint 📕 🏁

- ✅ Install Mason CLI
- ✅ Initialize Mason in a Workspace
- ✅ Install a brick
- ☑️ Use a brick

---

# `$ mason make` 🚧

> _Generate code from a brick_

- looks up brick metadata
- prompts for any required variables
- generates code in the desired output directory

---

# `$ mason make` in action

```sh
$ mason make hello
? What is your name? (Dash)
```

---

# `$ mason make` in action

```sh
$ mason make hello
? What is your name? (Dash) Felix
✓ Made brick hello (52ms)
✓ Generated 1 file:
  /me/mason_playground/HELLO.md (new)
```

---

# What's inside `HELLO.md` 👀

```md
Hello Felix! 👋
```

---

# `$ mason make` w/command-line args 🧑‍💻

```sh
$ mason make hello --name Felix
✓ Made brick hello (41ms)
✓ Generated 1 file:
  /me/mason_playground/HELLO.md (identical)
```

---

# `$ mason make` w/config file 📝

_config.json_

```json
{
  "name": "Felix"
}
```

```sh
$ mason make hello -c config.json
✓ Made brick hello (41ms)
✓ Generated 1 file:
  /me/mason_playground/HELLO.md (identical)
```

---

# `$ mason make` w/custom output directory 🗂

```sh
$ mason make hello --name Felix -o ./out
✓ Made brick hello (41ms)
✓ Generated 1 file:
  /me/mason_playground/out/HELLO.md (new)
```

---

# `$ mason make` conflicts ❗️

```sh
$ mason make hello --name Dash
conflict /me/mason_playground/HELLO.md
Overwrite HELLO.md? (Yyna)
```

---

# `$ mason make` conflicts ❗️

```sh
$ mason make hello --name Dash
conflict /me/mason_playground/HELLO.md
Overwrite HELLO.md? (Yyna) y
✓ Made brick hello (32.5s)
✓ Generated 1 file:
  /me/mason_playground/HELLO.md (new)
```

---

# The updated `HELLO.md` ✨

```md
Hello Dash! 👋
```

---

# Conflict Resolution Strategies

> _By default, `mason` will prompt on each file conflict_

Options:

- y - yes, overwrite (default)
- Y - yes, overwrite this and all others
- n - no, do not overwrite
- a - append to existing file

---

# `$ mason make` w/conflict resolution

```sh
# ❓ Always prompt when there is a file conflict (default)
$ mason make hello --name Dash --on-conflict prompt

# 🖊 Always overwrite when there is a file conflict
$ mason make hello --name Dash --on-conflict overwrite

# ✌️ Always skip when there is a file conflict
$ mason make hello --name Dash --on-conflict skip

# ➕ Always append when there is a file conflict
$ mason make hello --name Dash --on-conflict append
```

---

# Chapter 1 Complete 📕 🥳

- ✅ Install Mason CLI
- ✅ Initialize Mason in a Workspace
- ✅ Install a brick
- ✅ Use a brick

---

# Chapter 1 Summary 📕 📝

```
# 🎯 Activate from https://pub.dev
$ dart pub global activate mason_cli

# 📁 Initialize mason in the current workspace
$ mason init

# ☁️ Install all bricks defined in `mason.yaml`
$ mason get

# 🚧 Generate code from a brick
$ mason make hello
```

---

# Chapter 2: Creating a Brick 📗

- ☑️ Generating a new brick
- ☑️ Anatomy of a brick
- ☑️ Brick template syntax
- ☑️ Hooks

---

# Chapter 3: Brick Management 📘

- ☑️ Searching for bricks
- ☑️ Adding bricks
- ☑️ Removing bricks
- ☑️ Upgrading bricks

---

# Chapter 4: Publishing Bricks 📙

- ☑️ Intro to BrickHub
- ☑️ Signing up
- ☑️ Logging in
- ☑️ Publishing a brick
- ☑️ Logging out

---

# IDE Integration ⚡️

---

# Community Bricks 🌟

---

# Let's Recap

✅ Produce consistent code efficiently

✅ Code must be customizable

✅ Should be reusable and extensible

✅ Should be accessible to team/community

---

# Roadmap 🗺

---

# Thank You!

# 🙏

### Twitter @felangelov

### Github @felangel

---

# The Smallest Unit: A Brick 🧱

---

# Creating a Brick

```
$ mason new
```

---

# Anatomy of a Brick

- `brick.yaml`
- `__brick__`
- hooks (optional)

---

# Intro to Mustache 🥸

- Syntax
- Lambdas
- Partials
- Conditionals
- Loops

---

# What's inside a `brick.yaml`?

---

# Variables Types

---

# Intro to Hooks

- pre gen
- post gen

---

# Brick Management

## (the new state management)

---

# Brick Scopes

- Local vs Global

---

# Adding Bricks

- `path`
- `git`
- `remote`

---

# Removing Bricks

---

# Listing Bricks

---

# Brick Cache Management

---

# Generating Code via `mason make`

---

# Bundling

- Universal vs Dart Bundles

---

# Programmatic Code Generation with `package:mason`

- `package:very_good_cli`
- `package:dart_frog_cli`

---

# Putting it all together

---

# Mason VSCode Extension

---

# Intro to BrickHub

- Discover
- Consume
- Publish

---

# Brick Discovery

---

# Brick Consumption

---

# Publishing a Brick

---

# New Features

- https://brickhub.dev/bricks/feature_brick
- https://brickhub.dev/bricks/model
- https://brickhub.dev/bricks/service
- https://brickhub.dev/bricks/app_ui

---

# New Packages

- https://brickhub.dev/bricks/very_good_dart_package
- https://brickhub.dev/bricks/very_good_flutter_package
- https://brickhub.dev/bricks/app_ui
- https://brickhub.dev/bricks/widgetbook_starter

---

# New Applications

- https://brickhub.dev/bricks/very_good_core
- https://brickhub.dev/bricks/very_good_dart_cli
- https://brickhub.dev/bricks/amplify_starter
- https://brickhub.dev/bricks/flutterfire_starter
- https://brickhub.dev/bricks/macosui_starter

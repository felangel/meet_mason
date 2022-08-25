autoscale: true
footer: @felangelov - Flutter Vikings 2022
slidenumbers: true

# Meet Mason 🧱

### Introduction Templating and Custom Code Generation

![inline](https://raw.githubusercontent.com/felangel/mason/master/assets/mason_demo.gif)

### Felix Angelov @ Very Good Ventures

---

# About Me 🕶️🦄

![inline](./assets/github.png)![inline 40%](./assets/vgv_lockup.png)

### [https://verygood.ventures](https://verygood.ventures)

---

# Story Time 🧑‍🏫

- Joined a new team
- Assigned to a new feature

![inline](./assets/team.png)

---

# Story Time 🧑‍🏫

- So I did what any developer would do...

![inline](./assets/copy_paste.png)

---

# Story Time 🧑‍🏫

- And opened a pull request...

![inline](./assets/create_pull_request.png)

---

# Story Time 🧑‍🏫

![inline](./assets/pull_request_rejected.png)

- Rejected 🙅‍♂️
- I copied a "legacy" feature 😭

---

# Story Time 🧑‍🏫

[.column]

- 🗒 Back to square one...
- ⌛️ Lots of wasted time...
- 😤 Both sides frustrated...

[.column]

![inline](./assets/rejected_pull_request_reaction.png)

---

# The Problems

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

🧐 Custom Tooling (CLIs, IDE Extensions, etc.)

---

# Better Idea 🧠

- Spend the next year building a tool to automate this

![inline](assets/automate_meme.webp)

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

# `$ mason init` 📁

**Create a locally scoped workspace for working with bricks**

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

**Defines the available bricks for a specific workspace**

- similar to `pubspec.yaml`
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

**Install all bricks registered in the nearest parent `mason.yaml`**

- Analogous to `dart pub get`
- Generated `mason-lock.json`
- Bricks are cached locally for offline use
  - add `.mason` to `.gitignore`

---

# `$ mason get` in action

[.column]

```sh
$ mason get
✓ Getting bricks (22ms)
```

[.column]

[.code-highlight: 2-3]

```
├── .mason
├── mason-lock.json
└── mason.yaml
```

---

# `$ mason list` 🗒

**List all installed bricks`**

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

**Generate code from a brick**

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

**By default, `mason` will prompt on each file conflict**

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

# `$ mason new` ⛏

**Create a new brick template**

- creates a brick in the current directory
  - generates a `brick.yaml`
  - generates a `__brick__` directory
- includes `README`, `LICENSE`, and `CHANGELOG`

---

# `$ mason new` in action

```sh
$ mason new example
✓ Created new brick: example (74ms)
✓ Generated 5 file(s):
  /me/mason_playground/example/brick.yaml (new)
  /me/mason_playground/example/README.md (new)
  /me/mason_playground/example/CHANGELOG.md (new)
  /me/mason_playground/example/LICENSE (new)
  /me/mason_playground/example/__brick__/HELLO.md (new)
```

---

# Chapter 2: Checkpoint 📕 🏁

- ✅ Generating a new brick
- ☑️ Anatomy of a brick
- ☑️ Brick template syntax
- ☑️ Hooks

---

[.code-highlight: 5-6]

# Anatomy of a Brick 🧱

[.column]

```
.
├── CHANGELOG.md
├── LICENSE
├── README.md
├── __brick__
└── brick.yaml
```

[.column]

- **`__brick__`**
  - brick template
- **`brick.yaml`**
  - brick metadata (`pubspec.yaml`)

---

# Anatomy of the `brick.yaml`

**Defines the metadata for a specific brick**

[.column]

```yaml
name: example
description: An example brick
version: "0.1.0+1"

environment:
  mason: ">=0.1.0-dev <0.1.0"

vars:
  name:
    type: string
    description: Your name.
    default: Dash
    prompt: What is your name?
```

[.column]

- can contain zero or more variables
- variable types include:
  - `string`, `number`, `boolean`, `enum`, `array`

---

# Variable Type: Array

[.column]

```yaml
vars:
  flavors:
    type: array
    description: Supported flavors
    prompt: What flavors would you like to generate?
    defaults:
      - development
      - production
    values:
      - development
      - integration
      - staging
      - production
```

[.column]

```
$ mason make example
? What flavors would you like to generate?
❯ ◉  development
  ◯  integration
  ◯  staging
  ◉  production
```

---

# Variable Type: Enum

[.column]

```yaml
vars:
  license:
    type: enum
    default: MIT license
    prompt: "Choose a License:"
    values:
      - "Apache License 2.0"
      - 'BSD 3-Clause "New" or "Revised" license'
      - "GNU General Public License (GPL)"
      - "MIT license"
      - "Mozilla Public License 2.0"
```

[.column]

```
$ mason make example
? Choose a License:
  ◯  Apache License 2.0
  ◯  BSD 3-Clause "New" or "Revised" license
  ◯  GNU General Public License (GPL)
❯ ◉  MIT license
  ◯  Mozilla Public License 2.0
```

---

[.code-highlight: 5-7]

# Putting it Together 🧩

[.column]

```
.
├── CHANGELOG.md
├── LICENSE
├── README.md
├── __brick__
│   └── HELLO.md
└── brick.yaml
```

[.column]

##### `__brick__/HELLO.md`

```md
Hello {{name}}! 👋
```

##### `brick.yaml`

```yaml
name: hello
description: An example brick
version: "0.1.0+1"

vars:
  name:
    type: string
    description: Your name.
    prompt: What is your name?
```

[.column]

```sh
$ mason make hello
? What is your name? Vikings
```

##### `HELLO.md`

```md
Hello Vikings! 👋
```

---

# Chapter 2: Checkpoint 📕 🏁

- ✅ Generating a new brick
- ✅ Anatomy of a brick
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

- Multiple Template Engine Support
- Template Extensions
- Multiple Publishers

---

# Thank You!

# 🙏

### Twitter @felangelov

### GitHub @felangel

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

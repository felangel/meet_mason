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

```
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

# Let's Recap

✅ Produce consistent code efficiently

✅ Code must be customizable

✅ Should be reusable and extensible

✅ Should be accessible to team/community

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

---

# What's Next?

---

# Thank You!

# 🙏

### Twitter @felangelov

### Github @felangel

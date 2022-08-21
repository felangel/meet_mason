footer: @felangelov - Flutter Vikings 2022
slidenumbers: true

# Meet Mason 🧱

### Introduction Templating and Custom Code Generation

![inline](https://raw.githubusercontent.com/felangel/mason/master/assets/mason_demo.gif)

### Felix Angelov @ Very Good Ventures

---

# Very Good Ventures, Chicago 🕶️🦄

![inline](./assets/github.png)![inline 10%](./assets/unicorn-vgv-black.png)

### [https://verygood.ventures](https://verygood.ventures)

---

# Scenario A: Enterprise/Large Team

---

# Scenario B: Consulting/Freelance

---

# Scenario C: Hobbyist/Student

---

# Identifying the Problem(s)

❓ Produce consistent code efficiently

❓ Code must be customizable

❓ Should be reusable and extensible

❓ Should be accessible to team/community

---

# Some Possible Solutions...

🧐 Copy + Paste

🧐 GitHub Templates

🧐 VSCode/IntelliJ Snippets

🧐 Gists

---

# Meet Mason 🧱

![inline](assets/mason_ecosystem.png)

---

# Mason CLI 🧑‍💻

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

# Creating a Local Workspace 📁

```
$ mason init
✓ Initializing (49ms)
✓ Getting bricks (0.5s)
✓ Generated 1 file(s):
  /me/mason_playground/mason.yaml (new)
```

---

# Closer Look at `mason.yaml` 👀

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
  #     url: https://github.com/felangel/mason.git
  #     path: bricks/widget
```

---

# Listing Locally Installed Bricks 🧱

[.column]

```sh
# You can also use `mason list`.
$ mason ls
/me/mason_playground
└── hello 0.1.0+1 -> registry.brickhub.dev
```

---

# `mason make`

```sh
$ mason make hello
? What is your name? (Dash)
```

---

# `mason make`

```sh
$ mason make hello
? What is your name? (Dash) Felix
✓ Made brick hello (51ms)
✓ Generated 1 file:
  /me/mason_playground/HELLO.md (new)
```

---

# Questions?

---

# Thank You!

# 🙏

### Twitter @felangelov

### Github @felangel

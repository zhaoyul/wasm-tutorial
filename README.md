# wasm-tutorial

WebAssembly tutorial workspace.

This repository is currently a tutorial scaffold: it contains the top-level
documentation, but it does not yet ship lesson source code or runnable examples.
The goal of this README is to make that state obvious, explain how the repo
should grow, and give future lessons a consistent structure.

## Current Status

- The repository is intentionally minimal right now.
- There is nothing to install, build, or run from the repository root yet.
- Each future lesson or example should include its own exact prerequisites and
  commands.

If you expected runnable code and only found this README, that is the current
state of the project rather than a local setup mistake.

## Who This Repo Is For

- Learners who want step-by-step WebAssembly examples.
- Maintainers adding new lessons or example projects.
- Reviewers who need a clear contract for how tutorial material should be laid
  out and documented.

## Prerequisites

To work with the repository in its current state, you only need:

- `git` to clone the repository
- A text editor or IDE to read and edit lesson material
- A modern browser to test examples once they are added

Additional toolchains such as Rust, Go, TinyGo, Zig, Node.js, or a C/C++
compiler should only be treated as prerequisites when a specific lesson says so.
Do not assume one global toolchain for the entire repo unless the project
decides to standardize on it later.

## Clone The Repository

```bash
git clone https://github.com/zhaoyul/wasm-tutorial.git
cd wasm-tutorial
```

## Install / Build / Run

At the moment, the root of this repository does not define a project-wide
install, build, or run flow.

Use this rule instead:

1. Read the lesson-level README first.
2. Install only the toolchain required by that lesson.
3. Run the exact build and serve commands documented next to that example.

When lesson content is added, every runnable tutorial should document all of the
following in its own README:

- prerequisites
- dependency installation
- build command
- local run or serve command
- expected output
- cleanup steps if build artifacts are generated

See [docs/lesson-template.md](docs/lesson-template.md) for the recommended
format.

## Recommended Tutorial Structure

Keep lessons self-contained. A reader should be able to open one lesson
directory and find everything needed to understand and run it.

Suggested layout:

```text
wasm-tutorial/
├── README.md
├── docs/
│   ├── lesson-template.md
│   └── troubleshooting.md
├── lessons/
│   ├── 01-introduction/
│   │   └── README.md
│   └── 02-your-topic/
│       └── README.md
└── examples/
    ├── 01-introduction/
    │   ├── README.md
    │   └── <example files>
    └── 02-your-topic/
        ├── README.md
        └── <example files>
```

Recommended conventions:

- Use numbered lesson directories so the reading order is obvious.
- Keep prose in `lessons/` and runnable assets in `examples/` when both are
  needed.
- If a lesson and its example are small, colocating everything in one directory
  is also acceptable, but the README must still include exact setup steps.
- Prefer one concept per lesson instead of large mixed examples.
- Document expected output with screenshots, terminal output, or browser output
  when possible.

## Writing A New Lesson

When adding a lesson:

1. Create a short lesson overview.
2. State the exact prerequisites with versions where they matter.
3. Provide copy-pastable install, build, and run commands.
4. Explain what files the learner should inspect.
5. Call out expected output and common failure modes.
6. Link back to this README if the lesson introduces a new shared convention.

Use [docs/lesson-template.md](docs/lesson-template.md) as the starting point.

## Troubleshooting

Common issues that show up in WebAssembly tutorials are collected in
[docs/troubleshooting.md](docs/troubleshooting.md).

Short version:

- If a command is missing, check the lesson README for a required toolchain.
- If a `.wasm` file will not load in the browser, serve it over HTTP instead of
  opening files directly with `file://`.
- If browser output looks stale, clear generated artifacts and rebuild.
- If the example starts but cannot fetch assets, verify relative paths and MIME
  handling in your local server.

## Documentation Quality Bar

Before considering a lesson ready, confirm that:

- a fresh clone can follow the lesson without guessing commands
- prerequisites are named explicitly
- install, build, and run steps are separate and ordered
- expected output is described
- troubleshooting notes cover the most likely local setup failures

That quality bar matters more than lesson count. A small tutorial with precise
instructions is more useful than a large tutorial that leaves setup ambiguous.

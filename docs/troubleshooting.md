# Troubleshooting

These are common failure modes for WebAssembly tutorials. They are deliberately
generic so they stay useful even before the repository standardizes on one
language or toolchain.

## There Is Nothing To Build From The Repo Root

This is expected in the current state of the repository. The root README is a
project guide, not a runnable example. Use a lesson-level or example-level
README once tutorial content is added.

## `command not found`

Cause:

- A lesson depends on a toolchain that is not installed locally.

What to check:

- Re-read that lesson's prerequisites section.
- Verify the tool is on your `PATH`.
- Confirm the version matches the lesson if the commands are version-sensitive.

## The Browser Refuses To Load The `.wasm` File

Cause:

- Opening an example directly with `file://` instead of serving it over HTTP.

What to do:

- Start the local server documented by the lesson.
- Reload the page through `http://localhost/...`.
- Check the browser devtools network tab for 404 or MIME-type errors.

## The Page Loads But Nothing Happens

Cause:

- JavaScript glue code, asset paths, or initialization steps are incorrect.

What to check:

- Browser console errors
- Relative paths to `.wasm`, JavaScript, CSS, or other assets
- Whether the lesson requires a generated file that has not been rebuilt

## Output Looks Stale After Rebuilding

Cause:

- The browser is caching old assets, or the lesson writes output into a
  generated directory that was not cleaned first.

What to do:

- Hard-refresh the browser.
- Remove generated artifacts for that lesson.
- Re-run the documented build command from a clean state.

## A Local Server Starts But Assets Return 404

Cause:

- The server root does not match the example directory structure.

What to check:

- Start the server from the directory the lesson expects.
- Verify output file names and relative paths.
- Confirm the build step created the files that the browser is requesting.

## Toolchain-Specific Issues

If a lesson relies on Rust, Go, TinyGo, Zig, Node.js, or another language
ecosystem, add a lesson-specific troubleshooting section there instead of trying
to keep every toolchain caveat in this shared file. The shared file should stay
focused on issues that repeat across lessons.

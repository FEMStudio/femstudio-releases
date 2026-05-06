# FEM Studio — Releases

This repository hosts downloadable binaries of **FEM Studio**, a modern
desktop GUI for the [Elmer FEM solver](http://www.elmerfem.org/).

> **Naming note.** The project's brand name is "FEM Studio" (with a space).
> The binary itself is called `ElmerStudio` — that's the name you'll see
> on downloaded files, in the application's title bar, and in
> `--version` output. Same software, two presentations: the brand for
> conversations and websites, the technical name for files and processes.

The source code is maintained in a separate, private repository.
**FEM Studio is closed-source but free to use** — see
[`LICENSE.md`](LICENSE.md) for the full terms.

## Latest downloads

Grab the right file for your platform from the
[latest release](https://github.com/FEMStudio/femstudio-releases/releases/latest):

| Platform | File | Notes |
|---|---|---|
| Linux (modern distros) | `ElmerStudio-x86_64.AppImage` | One file. `chmod +x`, run. Tested on Ubuntu 24.04+. |
| Linux (any modern distro) | `ElmerStudio-linux-x86_64.tar.gz` | Extract anywhere, run `./ElmerStudio/ElmerStudio`. |
| Windows 10/11 (installer) | `ElmerStudio-Setup.exe` | Standard Windows installer. |
| Windows 10/11 (portable) | `ElmerStudio-windows-x64.zip` | Extract, run `ElmerStudio.exe`. No install. |

> **Linux tip:** If you're on Ubuntu 24.04+, install the runtime libraries once:
> `sudo apt install libegl1 libxcb-cursor0 libxkbcommon-x11-0 libfuse2`

## What is this?

FEM Studio is a modernised graphical frontend for Elmer FEM. It started
as a personal tool — built because Elmer is excellent but the existing
GUI hadn't kept up with modern Qt or modern desktop UX. Now it's
released for anyone who finds it useful.

For more details, screenshots, and a feature comparison, visit the
project page: <https://masoudmim.github.io/femstudio/>

## Reporting issues

Bug reports and feature requests are welcome via this repository's
[Issues tab](https://github.com/FEMStudio/femstudio-releases/issues),
even though the source isn't here. Please include:

- Your OS and version (e.g. "Ubuntu 24.04", "Windows 11 23H2")
- The FEM Studio version (Help → About in the app, or run with `--version`)
- What you were doing when the issue happened
- The exact error message if there was one

## License

FEM Studio is free to use for any purpose, including commercial work.
You may not redistribute the binary or reverse-engineer it. See
`LICENSE.md` for the full terms.

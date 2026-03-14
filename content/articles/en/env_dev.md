---
name: env_dev.md
title: Development environments for Rust
summary: Setting up a development environment with Zed and/or VSCodium (or VSCode)
date: 2025-10-13
icon: zed.svg
---

This article presents the steps to set up a complete and operational development environment for Rust using either:
- [VSCodium](https://vscodium.com/): open source version without telemetry of [VSCode](https://code.visualstudio.com/)
- [Zed](https://zed.dev/): an editor developed in Rust 🦀

> This article focuses on installation for a Linux system but also applies to MacOS. For Windows there is a specific version of rustup with [specific prerequisites](https://rust-lang.github.io/rustup/installation/windows.html) but it is often simpler to work in [WSL remote](#sec_wsl_windows).

> On Linux, the steps have been validated on Debian 12 and Ubuntu 24.04 distributions.

Happy reading and happy getting started with Rust.

# Rust

## Prerequisites

Rust relies on different compilers (C/C++) depending on the target platform:
- Linux: cc (alias for gcc or clang)
- MacOS: clang
- Windows: msvc C++ or gcc (MinGW)

On Linux (Ubuntu, Debian), the simplest way to ensure these prerequisites is to install build-essential:
```sh
sudo apt update
sudo apt install build-essential
```

To install Rust, the simplest way is to use curl which must therefore also be available on the machine:
- apt:
```sh
sudo apt install curl
```
- snap:
```sh
sudo snap install curl
```
- on macOS
```sh
sudo brew install curl
```

## Installation

The official installation documentation is available [here](https://www.rust-lang.org/tools/install).

The main components of Rust are:
- **rustup**: command line tool to manage the installation/uninstallation and update of Rust
- **rustc**: the Rust compiler
- **cargo**: the package manager

Other components are available and important in the Rust ecosystem but we will see them later.

To install Rust, simply run the command below (this downloads a `rustup-init.sh` script and executes it).
```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
Choose the standard installation.
At the end of the installation, you will find in the home directory:
- a new `.rustup` directory containing information about the Rust installation (config, download cache...)
- a new `.cargo` directory containing, among other things, a `bin` directory where all essential executables (cargo, rustc, clippy, ...) are present.
As indicated by the message at the end of installation, the `$HOME/.cargo/bin` directory must be in the PATH. The installation script takes care of this (in .bashrc and .profile under bash for example). Using the command `source ~/.cargo/env` may be necessary for it to take effect in the current installation shell (otherwise start another shell).

To verify that everything is installed, run the command
```sh
cargo version
```

## Hello world {#sec_hello_world}

To verify the installation works, let's do the classic "Hello World".
With the command
```sh
cargo new hello_world
```
cargo creates a hello_world directory containing:
- a Cargo.toml project configuration file
- a src directory containing a main.rs file with the classic "hello world"

Go to the hello_world directory and run the command
```sh
cargo run
```
Cargo compiles the code and runs it to display a beautiful "Hello, world".

The Rust command line environment is operational 🏆.

## Updating

Updating to the latest version of Rust is very simple, just run the command:
```sh
rustup update stable
```
The `stable` parameter upgrades to the latest stable version, but other versions are possible (`rustup update --help`).

## Uninstalling

To uninstall Rust, the best way is to use the command:
```sh
rustup self uninstall
```
It can be done manually by performing the same operations as this command, namely
- deleting the `.cargo` and `.rustup` directories from home
- removing the modifications made to profile files (.bashrc and .profile for example)

# Codium

The official [VSCodium](https://vscodium.com/) website provides all the information for [installation](https://vscodium.com/#install).
On Debian and Ubuntu, the best solution is to download the codium_x.y.z.deb file then install with the command
```sh
sudo apt install ./codium_x.y.z.deb
```

## Workspace

[VSCode workspaces](https://code.visualstudio.com/docs/editing/workspaces/workspaces) are very useful for defining debug configurations, tasks and other settings.

Indeed, using a [workspace file](https://code.visualstudio.com/docs/editing/workspaces/multi-root-workspaces#_workspace-file) (.code-workspace extension) allows you to centralize and share (by versioning this file) a set of elements (debug, extensions, tasks, ...) available directly when opening the file (using the "Open Workspace from file..." menu in VSCod(e|ium)).

Here is some information about this JSON format file:
- "folders": contains all project directories
- "tasks": contains all tasks defined for the project. This JSON element has the same format as the [tasks.json](https://code.visualstudio.com/docs/debugtest/tasks?originUrl=/docs/debugtest/debugging-configuration) file
- "settings": contains project settings. This JSON element has the same format as the [settings.json](https://code.visualstudio.com/docs/configure/settings?originUrl=%2Fdocs%2Fconfigure%2Fthemes#_settings-json-file) file
- "settings/launch": sub-element of "settings" containing all execution configurations (debug, release). This JSON element has the same format as the [launch.json](https://code.visualstudio.com/docs/debugtest/debugging-configuration) file
- "extensions": contains extension information and mainly the "recommendations" sub-element useful for listing extensions to install.

For Rust this is important to:
- Specify the extension to install [rust-analyzer](https://code.visualstudio.com/docs/languages/rust) which easily integrates the Rust language into VSCodium
```json
"extensions": {
		"recommendations": [
			"rust-lang.rust-analyzer", //extension for using rust in VScodium
			"vadimcn.vscode-lldb", //extension for debugging rust in VSCodium		]
	}
```
- Define actions for easy code debugging:
  - with tasks for compilation
```json
 "tasks": {
		"version": "2.0.0",
		"tasks": [
			{
				"label": "cargo build",
				"command": "cargo build",
				"type": "shell",
				"group": "build"
			}
		]
	},
```
  - and the debug configuration
```json
"configurations": [
				{ //configuration for debugging
					"name": "Debug Rust Program",
					"type": "lldb",
					"request": "launch",
					"program": "${workspaceFolder}/target/debug/hello_world",
					"args": [],
					"cwd": "${workspaceFolder}",
					"preLaunchTask": "cargo build",
				}
			]
```

The source code of the hello_world project with a ready-to-use workspace is available on the examples repo https://github.com/rouillelefait/examples in the hello_world directory. By opening the workspace "hello_world.code-workspace" in VSCod(e|ium) it will:
- suggest installing the 2 recommended extensions
- directly provide a "Debug Rust Program" debug environment

Note: after opening the workspace, the extension installation suggestion appears after a few seconds. If it doesn't, the extensions management tab displays the list of recommendations.

If everything goes well, compilation and debugging in VSCodium are immediately operational.

# Zed

The official [Zed](https://zed.dev/) website provides all the information for [installing](https://zed.dev/download) it.
On Linux, it comes down to running the command, just like for Rust:
```sh
curl -f https://zed.dev/install.sh | sh
```

This editor is truly amazing for several reasons:
- it is very performant
- it is immediately configured to compile/debug Rust
- it allows collaborative work
- it allows direct integration of LLM engines
- ....
- and it is written in Rust, and even if that's not a guarantee of quality, it's in the spirit of Rouille le fait. It is based on the graphics library [gpui](https://www.gpui.rs/) also developed by the Zed team and which is worth checking out if you have Rust development projects (desktop only) with a performant graphical interface.

I will most certainly write a dedicated article about Zed when my knowledge level is sufficient to share it.

To test Zed with the hello_world example from the repo https://github.com/rouillelefait/examples, simply open the hello_world directory.
Open the file src/main.rs and click the small arrow in the margin of the `fn main()` line to run or debug the project.


# Windows with WSL{#sec_wsl_windows}

For Windows users, I recommend... switching to Linux, it's much better. If it's complicated at first, persevere, it's like Rust, it changes a lot at the beginning but in the end the gain is significant in every way (performance, security, ...).

If it's really not possible, use [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) to have a Linux environment under Windows. With a Debian or Ubuntu under WSL, the Rust installation steps are exactly the same as under Linux.

For the IDE, on Windows you can use the [WSL remote](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) extension for VSCode which allows you to work in WSL (Linux) from VSCode installed on Windows. This extension seems to have some issues with VSCodium.

Now that Zed is stable on Windows, it is the ideal choice with a very performant integration allowing you to work in WSL distributions without needing a dedicated extension.

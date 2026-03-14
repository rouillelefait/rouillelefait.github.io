---
name: env_dev.md
title: Environnements de développement pour rust
summary: Mettre en place un environnement de développement avec Zed et/ou VSCodium (ou VSCode)
date: 2025-10-13
icon: zed.svg
---

Cet article présente les étapes pour mettre en place un environnement de développement complet et opérationnel pour Rust en utilisant soit:
- [VSCodium](https://vscodium.com/) : version open source sans télémetrie de [VSCode](https://code.visualstudio.com/)
- [Zed](https://zed.dev/) : environnement développé en Rust 🦀

> Cet article se concentre sur l'installation pour un système linux mais cela s'applique également pour MacOS. Pour windows il existe une version spécifique de rustup avec des [prérequis spécifiques](https://rust-lang.github.io/rustup/installation/windows.html) mais il est souvent plus simple de travailler en [WSL remote](#sec_wsl_windows).

> Sous linux les étapes ont été validées sur les distributions Debian 12 et Ubuntu 24.04.

Bonne lecture et bon démarrage en Rust.

# Rust

## Prérequis

Rust se base sur différents compilateurs (C/C++) en fonction de la plateforme cible visée :
- Linux : cc (alias vers gcc ou clang)
- MacOS : clang
- Windows : msv C++ ou gcc (MinGW)

Sous linux (Ubuntu, Debian), le plus simple pour assurer ces prérequis est d'installer build-essential :
```sh
sudo apt update
sudo apt install build-essential
```

Pour install Rust le plus simple est d'utiliser curl qui doit donc également être disponible sur le post:
- apt :
```sh
sudo apt install curl
```
- snap :
```sh
sudo snap install curl
```
- sous macOS
```sh
sudo brew install curl
```

## Installation

La documentation officielle d'installation est disponible [ici](https://www.rust-lang.org/fr/tools/install).

Les composants principaux de Rust sont :
- **rustup** : outils en ligne de commande pour gérer l'installation/désinstallation et mise à jour de Rust
- **rustc** : le compilateur Rust
- **cargo** : le gestionnaire de package

D'autres composants sont disponibles et importants dans l'écosystème Rust mais nous les verrons plus tard.

Pour installer rust il suffit d'éxecuter la commmande ci-dessous (cela télécharge un script `rustup-init.sh` et l'éxecute).
```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
Choisir l'installation standard.
A la fin de l'installation, on retrouve dans le répertoire home :
- un nouveau répertoire `.rustup`  contenant des informations sur l'installation de rust (config, cache de téléchargement...)
- un nouveau répertoire `.cargo` contenant, entre autre, un repertoire `bin` dans lequel tous les executables essentiels (cargo, rustc, clippy, ...) sont présents.
Comme l'indique le message en fin d'installation, il faut que le répertoire '$HOME/.cargo/bin' soit dans le PATH. Le script d'installation fait le nécéssaire (dans .bashrc  et .profile sous bash par exemple). L'utilisation la commande `source ~/.cargo/env` peut être nécessaire pour la prise en compte dans le shell courant d'installation (sinon démarrer un autre shell).

Pour vérifier que tout est installé, lancer la commande
```sh
cargo version
```

## Hello world {#sec_hello_world}

Pour vérifier le fonctionnement de l'installation passons au classique "Hello World".
Avec la commande
```sh
cargo new hello_world
```
cargo crée un répertoire hello_world dans lequel on trouve:
- un fichier Cargo.toml de configuration du projet
- un répertoire src contenant un fichier main.rs avec le classique "hello world"

Aller dans le répertoire hello_world et lancer la commande
```sh
cargo run
```
Cargo compile le code et l'éxecute pour afficher un beau "Hello, world".

L'environnement Rust en ligne de commande est opérationnel 🏆.

## Mise à jour

La mise à jour vers la dernière version de rust est très simple, il suffit d'éxecuter la commande :
```sh
rustup update stable
```
Le paramètre `stable` permet de passer à la dernière version stable, mais d'autres versions sont possibles (`rustup update --help`).

## Désinstallation

Pour désinstaller Rust le mieux est d'utiliser la commande :
```sh
rustup self unistall
```
C'est faisable manuellement en réalisant les mêmes opérations que cette commande à savoir
- supprimer les répertoires `.cargo` et `.rustup` de home
- enlever les modifications faite dans les fichiers de profile (.bashrc et .profile par exemple)

# Codium

Le site officiel de [VSCodium](https://vscodium.com/) donne toutes les informations pour l'[installation](https://vscodium.com/#install).
Sous debian et ubuntu, la meilleure solution reste de télécharger le fichier codium_x.y.z.deb puis d'installer avec la commande
```sh
sudo apt install ./codium_x.y.z.deb
```

## Workspace

Les [workspace VSCode](https://code.visualstudio.com/docs/editing/workspaces/workspaces) sont très utiles pour définir des configurations de debug, tâches et autre réglages.

En effet l'utilisation d'un [fichier de workspace](https://code.visualstudio.com/docs/editing/workspaces/multi-root-workspaces#_workspace-file) (extension .code-workspace) permet de centraliser et de partager (en versionnant ce fichier) un ensemble d'élements (debug, extension, tasks,... ) disponibles directement à l'ouverture du fichier (en utilisant le menu "Open Workspace from file..." de VSCod(e|ium)).

Voici quelques informations sur ce fichier au format Json:
- "folders" : contient l'ensemble des répertoires du projet
- "tasks" : contient l'ensemble des tâches définies pour le projet. Cet élement json a le même format que le fichier [tasks.json](https://code.visualstudio.com/docs/debugtest/tasks?originUrl=/docs/debugtest/debugging-configuration)
- "settings" : contient les paramètres du projet. Cet élément json a le même format que le fichier [settings.json](https://code.visualstudio.com/docs/configure/settings?originUrl=%2Fdocs%2Fconfigure%2Fthemes#_settings-json-file)
- "settings/launch" : sous élement de "settings" contenant l'ensemble des configurationss d'éxecution (debug, release). Cet élément json a le même format que le fichier [launch.json](https://code.visualstudio.com/docs/debugtest/debugging-configuration)
- "extensions" : contient les informations sur les extensions et principalement le sous élement "recommendations" bien utile pour lister les extensions à installer.

Pour Rust c'est important pour :
- Préciser l'extension à installer [rust-analyzer](https://code.visualstudio.com/docs/languages/rust) qui permet d'intégrer facilement le language Rust dans VSCodium
```json
"extensions": {
		"recommendations": [
			"rust-lang.rust-analyzer", //extension for using rust in VScodium
			"vadimcn.vscode-lldb", //extension for debugging rust in VSCodium		]
	}
```
- Définir les actions pour débugguer le code facilement :
  - avec des tâches pour la compilation
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
  - et la configuration pour le debug
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

Le code source du projet hello_world avec un workspace prêt à l'emploi est disponible sur le repo d'exemples https://github.com/rouillelefait/examples dans le répertoire hello_world. En ouvrant le workspace "hello_world.code-workspace" dans VSCod(e|ium) celui va :
- proposer l'installation des 2 extensions recommandées
- mettre à disposition directement un environnement de debug "Debug Rust Program"

Remarque : après ouverture du workspace, la proposition d'installation des extensions apparait au bout de qq secondes. Si jamais ce n'est pas le cas, l'onglet de gestion des extensions vous affiche la liste des recommandations.

Si tout se passe bien, la compilation et le debug dans VSCodium sont directement opérationnels.

# Zed

Le site officiel de [Zed](https://zed.dev/) donne toutes les informations pour l'[installer](https://zed.dev/download).
Sous linux ça se résume comme pour rust à lancer la commande
```sh
curl -f https://zed.dev/install.sh | sh
```

Cet éditeur est vraiment génial pour plusieurs raisons :
- il est très performant
- il est immédiatement configuré pour compiler/debugger du Rust
- il permet de travailler en collaboratif
- il permet d'intégrer directement des moteurs llm
- ....
- et il est écrit en Rust et même si c'est pas un gage de qualité, c'est dans l'esprit de Rouille le fait. Il est basé sur la librarie graphique [gpui](https://www.gpui.rs/) développé également par l'équide de Zed et qui mérite d'y jeter un oeil si vous avez des projets de développement en Rust (pour desktop uniquement) avec une interface graphique performante.

Je ferai très certainement un article dédié à Zed quand mon niveau de connaissance sera suffisant pour le partager.

Pour tester Zed avec l'exemple hello_world du repo https://github.com/rouillelefait/examples, il suffit d'ouvrir le répertoire hello_world.
Ouvrir le fichier src/main.rs et cliquer sur la petite flèche dans la marge de la ligne `fn main()` pour lancer ou debugger le projet.


# Windows avec WSL{#sec_wsl_windows}

Pour les adeptes de Windows, je conseille... de basculer sous linux, c'est beaucoup mieux. Si c'est compliqué au début, persévérer, c'est comme Rust, ça change beaucoup au début mais au final le gain est important à tous points de vue (performance, sécurité,...).

Si vraiment ce n'est pas possible, utiliser [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) pour avoir un environnement linux sous windows. Avec une Debian ou une Ubuntu sous wsl, les étapes d'installation de Rust sont exactement les mêmes que sous linux.

Pour l'IDE, Zed n'est pas encore stable sous windows donc utiliser VSCode. L'extension [WSl remote](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) de VSCode permet de travailler dans WSL (linux) depuis VSCode installé sous windows. Cette extension semble poser quelques problèmes de fonctionnement avec VSCodium.

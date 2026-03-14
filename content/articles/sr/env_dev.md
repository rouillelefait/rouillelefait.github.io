---
name: env_dev.md
title: Razvojna okruženja za Rust
summary: Postavljanje razvojnog okruženja sa Zed i/ili VSCodium (ili VSCode)
date: 2025-10-13
icon: zed.svg
---

Ovaj članak predstavlja korake za postavljanje kompletnog i operativnog razvojnog okruženja za Rust koristeći:
- [VSCodium](https://vscodium.com/): verziju otvorenog koda bez telemetrije od [VSCode](https://code.visualstudio.com/)
- [Zed](https://zed.dev/): editor razvijen u Rust-u 🦀

> Ovaj članak se fokusira na instalaciju za Linux sistem, ali se takođe primenjuje na MacOS. Za Windows postoji specifična verzija rustup-a sa [specifičnim preduslovima](https://rust-lang.github.io/rustup/installation/windows.html), ali je često jednostavnije raditi u [WSL remote](#sec_wsl_windows).

> Na Linux-u, koraci su validirani na distribucijama Debian 12 i Ubuntu 24.04.

Prijatno čitanje i srećan početak sa Rust-om.

# Rust

## Preduslovi

Rust se oslanja na različite kompajlere (C/C++) u zavisnosti od ciljne platforme:
- Linux: cc (alias za gcc ili clang)
- MacOS: clang
- Windows: msvc C++ ili gcc (MinGW)

Na Linux-u (Ubuntu, Debian), najjednostavniji način da se obezbede ovi preduslovi je instalacija build-essential:
```sh
sudo apt update
sudo apt install build-essential
```

Za instalaciju Rust-a najjednostavnije je koristiti curl koji takođe mora biti dostupan na mašini:
- apt:
```sh
sudo apt install curl
```
- snap:
```sh
sudo snap install curl
```
- na macOS-u
```sh
sudo brew install curl
```

## Instalacija

Zvanična dokumentacija za instalaciju je dostupna [ovde](https://www.rust-lang.org/tools/install).

Glavne komponente Rust-a su:
- **rustup**: alat komandne linije za upravljanje instalacijom/deinstalacijom i ažuriranjem Rust-a
- **rustc**: Rust kompajler
- **cargo**: menadžer paketa

Druge komponente su dostupne i važne u Rust ekosistemu, ali ćemo ih videti kasnije.

Za instalaciju Rust-a, jednostavno pokrenite komandu ispod (ovo preuzima skriptu `rustup-init.sh` i izvršava je).
```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
Izaberite standardnu instalaciju.
Na kraju instalacije, u home direktorijumu ćete pronaći:
- novi `.rustup` direktorijum koji sadrži informacije o Rust instalaciji (konfiguracija, keš preuzimanja...)
- novi `.cargo` direktorijum koji sadrži, između ostalog, `bin` direktorijum gde su prisutni svi esencijalni izvršni fajlovi (cargo, rustc, clippy, ...).
Kao što je navedeno u poruci na kraju instalacije, direktorijum `$HOME/.cargo/bin` mora biti u PATH-u. Instalaciona skripta se o tome stara (u .bashrc i .profile pod bash-om na primer). Korišćenje komande `source ~/.cargo/env` može biti neophodno da bi se primenilo u trenutnom shell-u instalacije (inače pokrenite drugi shell).

Za verifikaciju da je sve instalirano, pokrenite komandu
```sh
cargo version
```

## Hello world {#sec_hello_world}

Da bismo verifikovali da instalacija funkcioniše, uradimo klasični "Hello World".
Sa komandom
```sh
cargo new hello_world
```
cargo kreira hello_world direktorijum koji sadrži:
- Cargo.toml konfiguracioni fajl projekta
- src direktorijum koji sadrži main.rs fajl sa klasičnim "hello world"

Idite u hello_world direktorijum i pokrenite komandu
```sh
cargo run
```
Cargo kompajlira kod i izvršava ga da prikaže lep "Hello, world".

Rust okruženje komandne linije je operativno 🏆.

## Ažuriranje

Ažuriranje na najnoviju verziju Rust-a je veoma jednostavno, samo pokrenite komandu:
```sh
rustup update stable
```
Parametar `stable` nadograđuje na najnoviju stabilnu verziju, ali su moguće i druge verzije (`rustup update --help`).

## Deinstalacija

Za deinstalaciju Rust-a, najbolje je koristiti komandu:
```sh
rustup self uninstall
```
Može se uraditi ručno izvođenjem istih operacija kao ova komanda, naime
- brisanje `.cargo` i `.rustup` direktorijuma iz home-a
- uklanjanje modifikacija napravljenih u profil fajlovima (.bashrc i .profile na primer)

# Codium

Zvanični sajt [VSCodium](https://vscodium.com/) pruža sve informacije za [instalaciju](https://vscodium.com/#install).
Na Debian-u i Ubuntu-u, najbolje rešenje je preuzeti codium_x.y.z.deb fajl, a zatim instalirati komandom
```sh
sudo apt install ./codium_x.y.z.deb
```

## Workspace

[VSCode workspace-ovi](https://code.visualstudio.com/docs/editing/workspaces/workspaces) su veoma korisni za definisanje konfiguracija za debug, taskove i druga podešavanja.

Zaista, korišćenje [workspace fajla](https://code.visualstudio.com/docs/editing/workspaces/multi-root-workspaces#_workspace-file) (ekstenzija .code-workspace) omogućava centralizovanje i deljenje (verzionisanjem ovog fajla) skupa elemenata (debug, ekstenzije, taskovi, ...) dostupnih direktno pri otvaranju fajla (koristeći meni "Open Workspace from file..." u VSCod(e|ium)).

Evo nekih informacija o ovom fajlu u JSON formatu:
- "folders": sadrži sve direktorijume projekta
- "tasks": sadrži sve taskove definisane za projekat
- "settings": sadrži podešavanja projekta
- "settings/launch": podelement "settings" koji sadrži sve konfiguracije izvršavanja (debug, release)
- "extensions": sadrži informacije o ekstenzijama i uglavnom podelement "recommendations" koristan za listanje ekstenzija za instalaciju.

Za Rust je ovo važno za:
- Specifikovanje ekstenzije za instalaciju [rust-analyzer](https://code.visualstudio.com/docs/languages/rust) koja lako integriše Rust jezik u VSCodium
```json
"extensions": {
		"recommendations": [
			"rust-lang.rust-analyzer",
			"vadimcn.vscode-lldb"
		]
	}
```
- Definisanje akcija za lako debugovanje koda:
  - sa taskovima za kompilaciju
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
  - i konfiguracija za debug
```json
"configurations": [
				{
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

Izvorni kod hello_world projekta sa gotovim workspace-om je dostupan na repo-u primera https://github.com/rouillelefait/examples u hello_world direktorijumu. Otvaranjem workspace-a "hello_world.code-workspace" u VSCod(e|ium), on će:
- predložiti instalaciju 2 preporučene ekstenzije
- direktno obezbediti "Debug Rust Program" debug okruženje

Napomena: nakon otvaranja workspace-a, predlog za instalaciju ekstenzija se pojavljuje nakon nekoliko sekundi. Ako se ne pojavi, tab za upravljanje ekstenzijama prikazuje listu preporuka.

Ako sve prođe dobro, kompilacija i debugovanje u VSCodium-u su odmah operativni.

# Zed

Zvanični sajt [Zed](https://zed.dev/) pruža sve informacije za [instalaciju](https://zed.dev/download).
Na Linux-u se svodi na pokretanje komande, baš kao i za Rust:
```sh
curl -f https://zed.dev/install.sh | sh
```

Ovaj editor je zaista neverovatna za nekoliko razloga:
- veoma je performantan
- odmah je konfigurisan za kompajliranje/debugovanje Rust-a
- omogućava kolaborativni rad
- omogućava direktnu integraciju LLM motora
- ....
- i napisan je u Rust-u, i čak i ako to nije garancija kvaliteta, to je u duhu Rouille le fait. Baziran je na grafičkoj biblioteci [gpui](https://www.gpui.rs/) koju je takođe razvio Zed tim i koja zaslužuje pogled ako imate Rust razvojne projekte (samo desktop) sa performantnim grafičkim interfejsom.

Sigurno ću napisati posvećen članak o Zed-u kada moj nivo znanja bude dovoljan da ga podelim.

Za testiranje Zed-a sa hello_world primerom iz repo-a https://github.com/rouillelefait/examples, jednostavno otvorite hello_world direktorijum.
Otvorite fajl src/main.rs i kliknite na malu strelicu na margini linije `fn main()` za pokretanje ili debugovanje projekta.


# Windows sa WSL{#sec_wsl_windows}

Za korisnike Windows-a, preporučujem... prelazak na Linux, mnogo je bolje. Ako je komplikovano na početku, istrajte, to je kao Rust, mnogo se menja na početku ali na kraju je dobitak značajan u svakom pogledu (performanse, bezbednost, ...).

Ako zaista nije moguće, koristite [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) za Linux okruženje pod Windows-om. Sa Debian-om ili Ubuntu-om pod WSL-om, koraci instalacije Rust-a su potpuno isti kao pod Linux-om.

Za IDE, na Windows-u možete koristiti [WSL remote](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) ekstenziju za VSCode koja omogućava rad u WSL-u (Linux) iz VSCode-a instaliranog na Windows-u. Ova ekstenzija izgleda ima nekih problema sa funkcionisanjem u VSCodium-u.

Sada kada je Zed stabilan na Windows-u, to je idealan izbor sa veoma performantnom integracijom koja omogućava rad u WSL distribucijama bez potrebe za posvećenom ekstenzijom.

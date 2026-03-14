---
name: rust.md
title: les ressources de base
summary: pour apprendre les bases du langage et ses spécificités
icon: cuddlyferris.svg
index: 1
date: 2025-10-12
---

# Préambule

La courbe d'apprentissage de Rust est longue et les concepts de base sont difficiles à appréhender. Contrairement à la majorité des langages, compiler son premier programme, même pour un exemple simple, est compliqué et on se confronte rapidement à des messages d'erreur du compilateur souvent incompréhensibles au départ.

Deux solutions s'offrent à vous :
1. Prendre le temps de lire des documents pour avoir une vision globale du langage et de ses concepts avant de se lancer dans du code
2. Se lancer dans le code et progresser au fur et à mesure des difficultés rencontrées en :
    - faisant du "reverse engineering" en s'appuyant sur les erreurs remontées par le compilateur
    - cherchant de l'information au fur et à mesure des problèmes rencontrés : site officiel, vidéo, partie d'un ouvrage, interrogation d'une IA,...

Personnellement (donc subjectivement), je pense que Rust est un langage qui nécessite de commencer obligatoirement par le point 1. pour ne pas abandonner en se cassant les dents tout de suite sur du code qui va remonter des erreurs rapidement décourageantes. Les paradigmes de Rust (borrow checker, lifetime, ... ) sont tellement différents des autres langages qu'il faut un minimum de lecture pour les appréhender avant de commencer.

Ensuite, une fois les concepts essentiels assimilés (même partiellement), on peut mieux comprendre les erreurs du compilateur et alors le passage à l'étape 2 devient le meilleur moyen de progresser. Faites alors des allers-retours entre écriture de code et lecture plus approfondie pour appréhender les concepts progressivement.


# Documentation officielle

Le site officiel de [Rust](https://www.rust-lang.org/) ( et sa version [française](https://www.rust-lang.org/fr/) ) est une source d'information incontournable.

On y trouve de la documentation générale sur le langage :
- comment [installer Rust](https://www.rust-lang.org/fr/tools/install)
- le [livre](https://doc.rust-lang.org/book/) de référence disponible également en [français](https://jimskapt.github.io/rust-book-fr/) (traduction non officielle)
Ce livre est également disponible à l'[achat](https://nostarch.com/rust-programming-language-2nd-edition) en version pdf ou papier
De la documentation plus spécifique sur :
- la [bibliothèque standard](https://doc.rust-lang.org/std/index.html)
- [cargo](https://doc.rust-lang.org/cargo)
- [rustdoc](https://doc.rust-lang.org/rustdoc/index.html)
- une page d'information sur les [outils](https://www.rust-lang.org/fr/tools)

# Outils d'apprentissage

- [rustlings](https://github.com/rust-lang/rustlings) : des exercices pour accompagner le livre officiel
- [Rust by Example](https://doc.rust-lang.org/rust-by-example/) : pour appréhender les concepts de base avec du code
- [playground](https://play.rust-lang.org/) : pour tester rapidement des bouts de code

Le site officiel reste la source d'information à laquelle il faut se référer mais ce n'est pas la source d'information que je trouve systématiquement la plus pédagogique.

# Livres

## "Programming Rust, Fast, Safe Systems Development"

Disponible dans sa [2ème édition](https://www.oreilly.com/library/view/programming-rust-2nd/9781492052586/), une [3ème édition](https://www.oreilly.com/library/view/programming-rust-3rd/9781098176228/) semble prévue apparemment pour Juin 2026.

Ce livre est très bien organisé, il permet une lecture progressive avec beaucoup de pédagogie.

Si vous avez le courage, je vous conseille fortement une première lecture quasi complète (sauf async programming et la suite) avant de se lancer dans le code. Pas grave si tout n'est pas assimilé du premier coup mais cela donne une vision claire et structurée des concepts essentiels.

Ensuite, étape par étape, ce livre reste une référence pour revoir les concepts avec une table des matières très bien structurée.

## "Rust for rustaceans" *(niveau avancé)*

Disponible [ici](https://nostarch.com/rust-rustaceans) avec [une page web dédiée](https://rust-for-rustaceans.com/)

Ce livre expose des notions très avancées de la programmation en Rust avec la vision d'un développeur très expérimenté.

À lire uniquement dans un second temps car les concepts exposés sont exigeants sur la connaissance du langage. Ce n'est pas un livre pour débuter mais une excellente ressource une fois les bases bien maîtrisées.

L'auteur [Jon Gjengset](https://thesquareplanet.com/) est un Rust enthusiast proposant beaucoup de ressources (voir section Vidéos ci-dessous).

# Vidéos

- [Jon Gjengset](https://www.youtube.com/c/JonGjengset) : des vidéos très approfondies sur des sujets avancés, ainsi qu'une [interview](https://www.youtube.com/watch?v=nOSxuaDgl3s) très intéressante sur sa vision de Rust et de l'IA que je partage
- [Let's Get Rusty](https://www.youtube.com/@letsgetrusty) : idéal pour les débutants, suit le livre officiel chapitre par chapitre

# Communauté

- [Forum officiel](https://users.rust-lang.org/) : pour poser des questions et échanger avec la communauté
- [r/rust](https://www.reddit.com/r/rust/) : le subreddit Rust, très actif
- [Discord Rust](https://discord.gg/rust-lang) : pour de l'aide en temps réel

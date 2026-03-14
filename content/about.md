---
title : A propos
---
Après plusieurs décennies de développement et de conception logicielle dans de nombreux langages (ASM, Pascal, C/C++, Python, Go, ...), **j'ai découvert Rust et son écosystème en 2024**.

Je me suis plongé rapidement dans ce langage que je trouve fascinant, mais pourquoi ?

# Un langage compliqué ?

Oui **Rust a une courbe d'apprentissage assez raide** et se mérite car il utilise des paradigmes différents des langages habituels. Par contre, une fois apprivoisé, même avec un premier niveau de compétences, le langage est tout aussi efficace et les éléments qui ne sont pas maîtrisés à 100% peuvent être contournés avec du code peut-être moins performant mais effectif. Et au fur et à mesure que l'on monte en compétence, la façon d'écrire du code change et devient de plus en plus "rusty" et efficace.

# Un langage exigeant ?

Oui Rust est exigeant sur la compréhension exacte de ce que l'on fait. **Impossible de laisser de côté pour plus tard un problème** de mémoire ou de partage de données entre threads. Le compilateur ne laisse pas passer et c'est là la principale force de Rust.

Au-delà de tous les aspects de sécurité qui sont souvent mis en avant, cette force de Rust a un impact important sur tous les projets.
Difficile voire impossible de faire un plat de spaghettis, non pas que le langage ne le permette pas si on le souhaite vraiment, mais la compréhension de tous les aspects du code impose naturellement d'aller vers une conception de plus en plus propre à mesure que le projet grandit.

# Un langage reposant ?

Oui, au final, Rust est reposant. On peut s'appuyer fortement sur le compilateur pour assurer tous les aspects sur lesquels une analyse a priori est souvent complexe pour notre cerveau.

Typiquement, les dépassements mémoire, les conditions de concurrence, interblocages (deadlocks) et autres bugs qui se reproduisent une fois sur 100 dans des conditions très spécifiques sont plus faciles à éviter en Rust.
Même si des outils comme [Valgrind](https://valgrind.org/) permettent d'aider sur des langages standards comme C/C++, **Rust permet d'éviter ou à défaut de limiter fortement ces problématiques dès la compilation**.

Lors de revue de code pas la peine de rechercher ce type d'erreur car on sait que **Rust ne laissera pas passer**. On peut alors se concentrer sur l'algorithmique et l'architecture car le compilateur aura fait le travail "bas niveau".

# Un langage apprécié ?

Oui, Rust est [le langage le plus apprécié](https://survey.stackoverflow.co/2024/technology#2-programming-scripting-and-markup-languages) ... par les développeurs qui persévèrent dans son apprentissage.

# Un écosystème complet ?

Oui, **l'écosystème de Rust est complet** avec, entre autres, cargo pour la gestion de package, des tests unitaires et d'intégration gérés nativement, une génération de documentation, des outils d'audit.

Et avec une communauté importante et enthousiaste qui développe de nombreux [crates](https://crates.io/), Rust permet de tout faire avec beaucoup d'efficacité, de performance et de sécurité. Certes il reste encore pas mal de travail pour être à la hauteur d'autres écosystèmes plus matures mais ce n'est qu'une question de temps.

J'espère que ce site pourra vous en convaincre et vous aidera à découvrir, apprécier et utiliser Rust dans tous vos projets.


> **Utilisation de l'IA** : Certaines parties de ce site web (texte et code source) et plus spécifiquement toutes les traductions en anglais et serbe, ont été réalisées à l'aide de l'IA, parfois avec une relecture humaine mais ne garantissant pas à 100% la qualité de ces traductions.
> Certains exemples de code source sur le repository [github](https://github.com/rouillelefait/) sont également générés avec de l'IA, parfois très partiellement pour aller plus vite sur certains aspects, parfois de manière plus importante voire complètement dans une approche orientée IA (Spec Driven Development par exemple). À chaque fois cette information est précisée dans le repository concerné.

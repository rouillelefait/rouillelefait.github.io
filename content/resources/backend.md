---
name: backend.md
title: créer des API backend en Rust
summary: ressources pour développer des backends web basés sur des API REST ou GraphQL
icon: backend.png
---

Rust est [opérationnel pour le développement web](https://www.arewewebyet.org/) avec des crates pour faire des serveurs d'API, gérer des bases de données, s'intégrer dans des environnements SaaS,..., tout ce qu'il faut pour du backend.

Voici quelques ressources et informations sur les frameworks permettant de construire des serveurs HTTP et des API REST ou GraphQL. Pas de ressources sur les solutions fullstack avec hydration, SSR (Server Side Rendering) ou autre technologie similaire, on se concentre ici uniquement sur la partie service HTTP et mise à disposition d'API.

> Pour développer un backend en Rust il est essentiel de connaître la programmation async (essentiellement avec le crate [tokio](https://tokio.rs/)) de Rust. C'est en effet un des domaines où cette technologie excelle et où il est presque impensable de ne pas l'utiliser.

# Framework backend

De nombreuses ressources de comparaison sont disponibles sur le net sur les principaux frameworks (listés également [ici](https://www.arewewebyet.org/topics/frameworks/) ):
- [actix-web](https://actix.rs/)
- [axum](https://github.com/tokio-rs/axum)
- [rocket](https://rocket.rs/)
- [poem](https://github.com/poem-web/poem)

Globalement tous ces frameworks, sauf certains orientés pour des usages précis (minimaliste par exemple pour [tide](https://github.com/http-rs/tide)), ont des fonctionnalités proches et des performances similaires. Donc sauf pour des usages particuliers ils feront tous l'affaire en fonction des préférences de chacun.

# OpenApi

Lors du développement d'une API, la spécification et la documentation sont des points essentiels pour assurer entre autres que la collaboration FrontEnd/BackEnd se passe bien.

L'initiative [OpenApi](https://www.openapis.org/) permet de définir un standard pour la spécification des API et [swagger](https://swagger.io/) des outils associés notamment pour visualiser la documentation et tester les API.

Les approches de développement sont :
- schema-first : utilisation d'un outil pour générer du code source à partir de la spécification de l'API
- code-first : documentation de l'API à partir du code source

Deux frameworks existent en Rust pour gérer la norme OpenAPI :
- [utoipa](https://github.com/juhaku/utoipa) : code-first permettant de générer de la documentation à partir du code pour différents frameworks web (actix-web,axum, rocket)
- [poem OpenApi](https://github.com/poem-web/poem/tree/master/poem-openapi) directement intégré au framework [poem](https://github.com/poem-web/poem)

Accessoirement un outil de [génération de code Rust](https://openapi-generator.tech/docs/generators/rust), développé en Node.js donc sans réel intérêt comparé à des crates pur Rust et intégrables avec les frameworks de backend.


**Sans hésitation, [poem](https://github.com/poem-web/poem) est aujourd'hui la meilleure solution pour développer une API OpenApi.**

Entre schéma-first et code-first, les macros et les différents services mis à disposition dans Poem OpenAPI permettent d'écrire du code clair, avec un boilerplate généré automatiquement. Optionnellement une interface Swagger permettant de visualiser la documentation et de tester l'API peut être intégrée à l'application en quelques lignes.

Le github de poem contient un nombre important d'[exemples](https://github.com/poem-web/poem/tree/master/examples/openapi).

# GraphQL

[GraphQL](https://graphql.org/) présente des avantages sur REST (OpenAPI) principalement dans le requêtage structuré qui permet à un client de ne demander et donc recevoir que ce dont il a besoin.

En Rust, 2 frameworks existent :
- [async-graphql](https://docs.rs/async-graphql/latest/async_graphql/) avec une approche "code first" et s'intègre avec la majorité des framework web. 
- [juniper](https://github.com/graphql-rust/juniper) également "code first", stable et mature mais moins maintenu

Encore une fois l'intégration **d'async-graphql avec [Poem](https://async-graphql.github.io/async-graphql/en/integrations_to_poem.html) est d'excellente qualité** ce qui permet à Poem de gérer aussi bien du GraphQL que du REST dans le même environnement et toujours avec la possibilité d'exposer la documentation GraphQL facilement. 

Un [exemple](https://github.com/poem-web/poem/tree/master/examples/poem/async-graphql) d'intégration de Poem et GraphQL

---
name: backend.md
title: Kreiranje backend API-ja u Rust-u
summary: resursi za razvoj web backend-ova zasnovanih na REST ili GraphQL API-jima
icon: backend.png
---

Rust je [spreman za web razvoj](https://www.arewewebyet.org/) sa crate-ovima za pravljenje API servera, upravljanje bazama podataka, integraciju u SaaS okruženja,..., sve što je potrebno za backend.

Evo nekoliko resursa i informacija o framework-ovima za izgradnju HTTP servera i REST ili GraphQL API-ja. Nema resursa o fullstack rešenjima sa hidracijom, SSR-om (Server Side Rendering) ili sličnim tehnologijama — fokusiramo se ovde isključivo na HTTP servise i pružanje API-ja.

> Za razvoj backend-a u Rust-u, neophodno je poznavati async programiranje (uglavnom sa [tokio](https://tokio.rs/) crate-om). Ovo je zaista jedna od oblasti gde ova tehnologija briljira i gde je gotovo nezamislivo ne koristiti je.

# Backend framework-ovi

Mnogi resursi za poređenje su dostupni na internetu o glavnim framework-ovima (takođe navedeni [ovde](https://www.arewewebyet.org/topics/frameworks/)):
- [actix-web](https://actix.rs/)
- [axum](https://github.com/tokio-rs/axum)
- [rocket](https://rocket.rs/)
- [poem](https://github.com/poem-web/poem)

Generalno, svi ovi framework-ovi, osim nekih dizajniranih za specifične slučajeve upotrebe (minimalistički na primer kao [tide](https://github.com/http-rs/tide)), imaju slične funkcionalnosti i uporedive performanse. Dakle, osim za posebne potrebe, svaki od njih će poslužiti u zavisnosti od ličnih preferencija.

# OpenAPI

Prilikom razvoja API-ja, specifikacija i dokumentacija su ključne tačke za obezbeđivanje, između ostalog, da saradnja FrontEnd/BackEnd funkcioniše dobro.

Inicijativa [OpenAPI](https://www.openapis.org/) definiše standard za specifikaciju API-ja, a [Swagger](https://swagger.io/) obezbeđuje povezane alate, posebno za vizualizaciju dokumentacije i testiranje API-ja.

Pristupi razvoju su:
- schema-first: korišćenje alata za generisanje izvornog koda iz specifikacije API-ja
- code-first: dokumentovanje API-ja iz izvornog koda

Dva framework-a postoje u Rust-u za upravljanje OpenAPI standardom:
- [utoipa](https://github.com/juhaku/utoipa): code-first, generiše dokumentaciju iz koda za različite web framework-ove (actix-web, axum, rocket)
- [poem OpenAPI](https://github.com/poem-web/poem/tree/master/poem-openapi) direktno integrisan u [poem](https://github.com/poem-web/poem) framework

Dodatno, postoji alat za [generisanje Rust koda](https://openapi-generator.tech/docs/generators/rust), razvijen u Node.js-u, pa bez stvarnog interesa u poređenju sa čistim Rust crate-ovima koji se integrišu sa backend framework-ovima.


**Bez oklevanja, [poem](https://github.com/poem-web/poem) je danas najbolje rešenje za razvoj OpenAPI API-ja.**

Između schema-first i code-first, makroi i različiti servisi koje pruža Poem OpenAPI omogućavaju pisanje čistog koda sa automatski generisanim boilerplate-om. Opciono, Swagger interfejs za vizualizaciju dokumentacije i testiranje API-ja može se integrisati u aplikaciju u samo nekoliko linija.

GitHub stranica poem-a sadrži veliki broj [primera](https://github.com/poem-web/poem/tree/master/examples/openapi).

# GraphQL

[GraphQL](https://graphql.org/) nudi prednosti u odnosu na REST (OpenAPI) uglavnom kroz strukturirano upitivanje koje omogućava klijentu da zatraži i samim tim primi samo ono što mu je potrebno.

U Rust-u, 2 framework-a postoje:
- [async-graphql](https://docs.rs/async-graphql/latest/async_graphql/) sa pristupom "code first", integriše se sa većinom web framework-ova.
- [juniper](https://github.com/graphql-rust/juniper) takođe "code first", stabilan i zreo ali manje aktivno održavan

Još jednom, integracija **async-graphql sa [Poem](https://async-graphql.github.io/async-graphql/en/integrations_to_poem.html)-om je odličnog kvaliteta**, što omogućava Poem-u da upravlja kako GraphQL-om tako i REST-om u istom okruženju, uvek sa mogućnošću lakog izlaganja GraphQL dokumentacije.

[Primer](https://github.com/poem-web/poem/tree/master/examples/poem/async-graphql) integracije Poem-a i GraphQL-a

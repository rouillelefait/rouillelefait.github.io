---
name: backend.md
title: Building backend APIs in Rust
summary: resources for developing web backends based on REST or GraphQL APIs
---

Rust is [ready for web development](https://www.arewewebyet.org/) with crates for building API servers, managing databases, integrating into SaaS environments,... everything needed for backend development.

Here are some resources and information about frameworks for building HTTP servers and REST or GraphQL APIs. No resources on fullstack solutions with hydration, SSR (Server Side Rendering) or similar technologies — we focus here solely on HTTP services and API provisioning.

> To develop a backend in Rust, it is essential to understand async programming (mainly with the [tokio](https://tokio.rs/) crate). This is indeed one of the areas where this technology excels and where it is almost unthinkable not to use it.

# Backend frameworks

Many comparison resources are available online about the main frameworks (also listed [here](https://www.arewewebyet.org/topics/frameworks/)):
- [actix-web](https://actix.rs/)
- [axum](https://github.com/tokio-rs/axum)
- [rocket](https://rocket.rs/)
- [poem](https://github.com/poem-web/poem)

Overall, all these frameworks, except some designed for specific use cases (minimalist for example like [tide](https://github.com/http-rs/tide)), have similar features and comparable performance. So unless you have particular needs, any of them will do depending on personal preferences.

# OpenAPI

When developing an API, specification and documentation are essential to ensure among other things that FrontEnd/BackEnd collaboration goes smoothly.

The [OpenAPI](https://www.openapis.org/) initiative defines a standard for API specification and [Swagger](https://swagger.io/) provides associated tools, notably for viewing documentation and testing APIs.

The development approaches are:
- schema-first: using a tool to generate source code from the API specification
- code-first: documenting the API from the source code

Two frameworks exist in Rust to handle the OpenAPI standard:
- [utoipa](https://github.com/juhaku/utoipa): code-first, generates documentation from code for various web frameworks (actix-web, axum, rocket)
- [poem OpenAPI](https://github.com/poem-web/poem/tree/master/poem-openapi) directly integrated into the [poem](https://github.com/poem-web/poem) framework

Additionally, a [Rust code generation](https://openapi-generator.tech/docs/generators/rust) tool exists, developed in Node.js, so of little real interest compared to pure Rust crates that integrate with backend frameworks.


**Without hesitation, [poem](https://github.com/poem-web/poem) is today the best solution for developing an OpenAPI API.**

Between schema-first and code-first, the macros and various services provided by Poem OpenAPI allow writing clean code with automatically generated boilerplate. Optionally, a Swagger interface for viewing documentation and testing the API can be integrated into the application in just a few lines.

Poem's GitHub contains a large number of [examples](https://github.com/poem-web/poem/tree/master/examples/openapi).

# GraphQL

[GraphQL](https://graphql.org/) offers advantages over REST (OpenAPI) mainly through structured querying that allows a client to request and therefore receive only what it needs.

In Rust, 2 frameworks exist:
- [async-graphql](https://docs.rs/async-graphql/latest/async_graphql/) with a "code first" approach, integrates with most web frameworks.
- [juniper](https://github.com/graphql-rust/juniper) also "code first", stable and mature but less actively maintained

Once again, the integration of **async-graphql with [Poem](https://async-graphql.github.io/async-graphql/en/integrations_to_poem.html) is of excellent quality**, allowing Poem to handle both GraphQL and REST in the same environment, always with the ability to easily expose GraphQL documentation.

An [example](https://github.com/poem-web/poem/tree/master/examples/poem/async-graphql) of Poem and GraphQL integration

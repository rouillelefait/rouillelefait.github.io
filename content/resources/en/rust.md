---
name: rust.md
title: Essential resources
summary: to learn the basics of the language and its specificities
icon: cuddlyferris.svg
index: 1
date: 2025-10-12
---

# Preamble

Rust's learning curve is long and the basic concepts are difficult to grasp. Unlike most languages, compiling your first program, even for a simple example, is complicated and you quickly encounter compiler error messages that are often incomprehensible at first.

Two approaches are available to you:
1. Take the time to read documentation to get an overview of the language and its concepts before diving into code
2. Jump straight into code and progress as difficulties arise by:
    - doing "reverse engineering" based on errors reported by the compiler
    - searching for information as problems arise: official site, videos, parts of a book, asking an AI, ...

Personally (and therefore subjectively), I think Rust is a language that absolutely requires starting with point 1, so as not to give up by immediately breaking your teeth on code that will quickly produce discouraging errors. Rust's paradigms (borrow checker, lifetime, ...) are so different from other languages that a minimum of reading is needed to understand them before starting.

Then, once the essential concepts are assimilated (even partially), you can better understand the compiler's errors and transitioning to step 2 becomes the best way to progress. Go back and forth between writing code and deeper reading to grasp concepts progressively.


# Official documentation

The official [Rust](https://www.rust-lang.org/) website is an essential source of information.

You'll find general documentation about the language:
- how to [install Rust](https://www.rust-lang.org/tools/install)
- the reference [book](https://doc.rust-lang.org/book/)
This book is also available for [purchase](https://nostarch.com/rust-programming-language-2nd-edition) in PDF or paper format
More specific documentation on:
- the [standard library](https://doc.rust-lang.org/std/index.html)
- [cargo](https://doc.rust-lang.org/cargo)
- [rustdoc](https://doc.rust-lang.org/rustdoc/index.html)
- an information page about [tools](https://www.rust-lang.org/tools)

# Learning tools

- [rustlings](https://github.com/rust-lang/rustlings): exercises to accompany the official book
- [Rust by Example](https://doc.rust-lang.org/rust-by-example/): learn basic concepts through code
- [playground](https://play.rust-lang.org/): quickly test code snippets

The official site remains the reference source of information but it's not the source I find systematically the most pedagogical.

# Books

## "Programming Rust, Fast, Safe Systems Development"

Available in its [2nd edition](https://www.oreilly.com/library/view/programming-rust-2nd/9781492052586/), a [3rd edition](https://www.oreilly.com/library/view/programming-rust-3rd/9781098176228/) apparently planned for June 2026.

This book is very well organized, allowing progressive reading with great pedagogy.

If you have the courage, I strongly recommend an almost complete first reading (except async programming and beyond) before diving into code. It's fine if everything isn't absorbed on the first pass, but it gives a clear and structured vision of the essential concepts.

Then, step by step, this book remains a reference for reviewing concepts with a very well-structured table of contents.

## "Rust for Rustaceans" *(advanced level)*

Available [here](https://nostarch.com/rust-rustaceans) with [a dedicated web page](https://rust-for-rustaceans.com/)

This book presents very advanced notions of Rust programming from the perspective of a very experienced developer.

To be read only as a second step as the concepts presented require strong knowledge of the language. This is not a book for beginners but an excellent resource once the basics are well mastered.

The author [Jon Gjengset](https://thesquareplanet.com/) is a Rust enthusiast offering many resources (see Videos section below).

# Videos

- [Jon Gjengset](https://www.youtube.com/c/JonGjengset): in-depth videos on advanced topics, as well as a very interesting [interview](https://www.youtube.com/watch?v=nOSxuaDgl3s) about his vision of Rust and AI, which I share
- [Let's Get Rusty](https://www.youtube.com/@letsgetrusty): ideal for beginners, follows the official book chapter by chapter

# Community

- [Official forum](https://users.rust-lang.org/): to ask questions and exchange with the community
- [r/rust](https://www.reddit.com/r/rust/): the Rust subreddit, very active
- [Rust Discord](https://discord.gg/rust-lang): for real-time help

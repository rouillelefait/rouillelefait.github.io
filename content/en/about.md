---
title : About
---
After several decades of software development and design in many languages (ASM, Pascal, C/C++, Python, Go, ...), **I discovered Rust and its ecosystem in 2024**.

I quickly immersed myself in this language that I find fascinating, but why?

# A complicated language?

Yes, **Rust has a fairly steep learning curve** and must be earned because it uses paradigms different from conventional languages. However, once tamed, even with a basic level of skill, the language is just as effective and features that aren't fully mastered can be worked around with code that may be less performant but still functional. And as you gain experience, the way you write code evolves and becomes increasingly "rusty" and efficient.

# A demanding language?

Yes, Rust is demanding about the precise understanding of what you're doing. **It's impossible to set aside a memory problem or data sharing issue between threads for later**. The compiler won't let it pass, and that is Rust's greatest strength.

Beyond all the security aspects that are often highlighted, this strength of Rust has a significant impact on all projects.
It's difficult, even impossible, to create a plate of spaghetti code — not that the language wouldn't allow it if you really wanted to, but understanding all aspects of the code naturally drives you toward an increasingly clean design as the project grows.

# A relaxing language?

Yes, ultimately, Rust is relaxing. You can rely heavily on the compiler to handle all the aspects where a priori analysis is often complex for our brains.

Typically, buffer overflows, race conditions, deadlocks, and other bugs that reproduce once in a hundred times under very specific conditions are easier to avoid in Rust.
Even though tools like [Valgrind](https://valgrind.org/) can help with standard languages like C/C++, **Rust allows you to avoid or at least significantly limit these issues at compile time**.

During code reviews, there's no need to look for this type of error because we know that **Rust won't let it pass**. We can then focus on algorithms and architecture because the compiler has done the "low-level" work.

# A beloved language?

Yes, Rust is [the most admired language](https://survey.stackoverflow.co/2024/technology#2-programming-scripting-and-markup-languages) ... by developers who persevere in learning it.

# A complete ecosystem?

Yes, **Rust's ecosystem is complete** with, among other things, Cargo for package management, natively managed unit and integration tests, documentation generation, and audit tools.

And with a large and enthusiastic community developing many [crates](https://crates.io/), Rust enables you to do everything with great efficiency, performance, and safety. Admittedly, there is still quite a bit of work to match other more mature ecosystems, but it's only a matter of time.

I hope this site will convince you and help you discover, appreciate, and use Rust in all your projects.


> **Use of AI**: Some parts of this website (text and source code) and more specifically all translations into English and Serbian, were produced with the help of AI, sometimes with human review but without guaranteeing 100% translation quality.
> Some source code examples on the [github](https://github.com/rouillelefait/) repository were also generated with AI, sometimes very partially to speed up certain aspects, sometimes more extensively or even entirely in an AI-driven approach (Spec Driven Development for example). Each time, this information is specified in the relevant repository.

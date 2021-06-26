# Book

## Introduction

- General introduction (for inspiration, can look at these resources)
  - [Rust CLI Book](https://rust-cli.github.io/book/index.html)
  - [Cargo Book](https://doc.rust-lang.org/cargo/index.html)
  - [The book](https://doc.rust-lang.org/book/ch00-00-introduction.html)
- Purpose of the book
  - To give an introduction to error handling in Rust
  - To give practical solutions to error handling design
    - Discussing different design decisions and tradeoffs
  - Share best practices for error handling in different scenarios

## Introduction to error handling

- What is error handling
  - Jane - [Error Handling is not all about errors](https://youtu.be/WzC7H83aDZc) (from minute 3:30).
    - Defining errors
    - Propagating errors and gathering context
    - Reacting errors
    - Discarding errors
    - Reporting errors and gathered context
- What is the purpose of errors?
  - Communication
    - All about expressing intent to the developer i.e this was supposed to happen but it failed and
      as a result this other thing happened
    - Preventing UB (but at the application level - i.e stopping invalid data or weird scenarios from
      occurring because of mishandled errors)
    - Giving enough context to failures to diagnose and debug rapidly
- Anatomy of errors (captured in what is error handling but could be separated or reiterated)
  - Creating
  - Propagating
  - Reporting
  - Discarding
  - Promoting (recoverable → irrecoverable)
  - Reacting

## Basic error handling in Rust

- Could replace basic with another word

- How Rust does error handling - do we need this since it's in The book? Possibly just to augment the
  discussion from the book or just rehash it to make this book complete in its own right.
  - Augmented material we could add:
    - Some of the benefits of returning errors (e.g explicit, communicates intent) - discuss without
      turning into a war
  - General content if we dive into subject material
    - Plenty of [material](https://github.com/rust-lang/project-error-handling/issues/24) to draw from
    - No exceptions
    - Result type for recoverable errors
    - Panic for irrecoverable errors
    - Bubbling errors
    - Convenience functions/syntax (`?`, `unwrap`, ...)

- Minigrep: our application for the book
  - Intro to `minigrep`
  - Light discussion on its purpose
- Basic error handling constructs shown
  - Result
  - Panic

## Error Design Patterns

- Overview of the ground we are going to cover
  - Why are custom errors important?
  - Why is designing errors important?
  - One liner for each type of design pattern
- Mention we're using `minigrep` as the application we are developing against
- [Failure book](https://rust-lang-nursery.github.io/failure/guidance.html) gives an overview
  of design patterns
  - Tie these in with more concrete examples (possibly through the implementation of `mini grep`)

- Error design
  - What are the contents needed for a useful error
  - What the error should inform you of - does it empower you to make relevant changes?
  - When to interpret error vs pass on through

## 3rd party libs

Up till now, we did everything manually. Run through the design patterns using 3rd party libs to ease
the burden
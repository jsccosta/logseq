- Built using Rust
- This is a binary build
-
# Node Components
- A toyDB node consists of three main components:
	- Storage engine: stores data and manages transactions, on disk and in memory.
	- Raft consensus engine: handles cluster coordination and state machine replication.
	- SQL engine: parses, plans, and executes SQL statements for clients.
-
# Day 1
### rustfmt
	- A tool for formatting Rust code according to style guidelines.
- **Clippy**
	- Linter for rust
- A shared reference type is written &type, or &'a type when you need to specify an explicit lifetime.
- Understood & is for shared reference but did not understand what is the difference between type and 'a in Rust language
- The 'a reads ‘the lifetime a’. Technically, every reference has some lifetime associated with it, but the compiler lets you elide (i.e. omit, see "Lifetime Elision") them in common cases.
-
-
- I found this and this and this and this that explains my question.
- The 'a reads ‘the lifetime a’. Technically, every reference has some lifetime associated with it, but the compiler lets you elide (i.e. omit, see "Lifetime Elision") them in common cases.
- fn bar<'a>(...)
- A function can have ‘generic parameters’ between the <>s, of which lifetimes are one kind. The <> is used to declare lifetimes. This says that bar has one lifetime, 'a.
- Rust has two main types of strings: &str and String. The &str are called ‘string slices’. A string slice has a fixed size, and cannot be mutated. It is a reference to a sequence of UTF-8 bytes.
- let greeting = "Hello there."; // greeting: &'static str
- "Hello there." is a string literal and its type is &'static str. A string literal is a string slice that is statically allocated, meaning that it’s saved inside our compiled program, and exists for the entire duration it runs. The greeting binding is a reference to this statically allocated string. Any function expecting a string slice will also accept a string literal.
- [Rust types explanation](https://stackoverflow.com/questions/47640550/what-is-a-in-rust-language)
-
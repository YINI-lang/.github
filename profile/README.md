# YINI-lang

**YINI** is a human-readable, INI-inspired configuration format with clear nested sections, explicit structure, and predictable parsing.

It is designed for configuration files that should be easy to read, easy to write, and straightforward for parsers and tools to process.

```yini
@yini

^ App
name = "Demo App"
version = "1.0.0"
debug = false

^^ Server
host = "localhost"
port = 8080

/END
```

## Project status

YINI is currently in active development.

The language specification is approaching its first stable `1.0.0` release, and parser implementations are being developed and tested against a shared test suite.

The project is still young, so feedback, bug reports, parser comparisons, and careful review are very welcome.

## Goals

YINI focuses on:

* Clear and readable configuration files.
* Explicit nested sections.
* Predictable parsing rules.
* Minimal syntax surprises.
* Human-friendly and parser-friendly structure.
* Practical use in real applications and tools.

YINI is not intended to be clever or magical. The goal is a small, understandable configuration format with enough structure for serious use.

## Main repositories

* **[YINI-spec](https://github.com/YINI-lang/YINI-spec)** — the YINI language specification and grammar.
* **[yini-parser-typescript](https://github.com/YINI-lang/yini-parser-typescript)** — official Node.js / TypeScript parser implementation.
* **[yini-parser-python](https://github.com/YINI-lang/yini-parser-python)** — official Python parser implementation.
* **[yini-cli](https://github.com/YINI-lang/yini-cli)** — command-line tooling for validating and working with YINI files.
* **[yini-demo-apps](https://github.com/YINI-lang/yini-demo-apps)** — small demo applications showing how YINI can be used in real projects.
* **[syntax-highlighting](https://github.com/YINI-lang/syntax-highlighting)** — syntax highlighting definitions for editors that support TextMate grammars.
* **[yini-homepage](https://github.com/YINI-lang/yini-homepage)** — homepage and documentation site for YINI.

The shared parser test suite, **yini-test**, is currently private while it is being prepared.

## Try YINI

You can try YINI through the parser packages and examples:

* TypeScript / Node.js parser.
* Python parser.
* CLI tools.
* Demo applications.

Documentation and examples are available at:

[yini-lang.org](https://yini-lang.org/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme)

## Contributing

Contributions are welcome, especially:

* Specification feedback.
* Parser bug reports.
* Test cases.
* Documentation improvements.
* Examples and integrations.
* Review of edge cases before `1.0.0`.

If you notice something unclear, surprising, inconsistent, or difficult to implement, please open an issue or discussion.

## Philosophy

YINI is built around a simple idea:

> Configuration should be clear to humans and predictable for tools.

The format favors explicit structure over hidden behavior, readability over cleverness, and consistency over shortcuts.

---

**^YINI ≡**

> A clear, structured, human-friendly configuration format.

[yini-lang.org](https://yini-lang.org/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme_footer) · [YINI on GitHub](https://github.com/YINI-lang)

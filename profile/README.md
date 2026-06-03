# YINI-lang

**YINI** is an INI-inspired, indentation-insensitive configuration format with clear nested sections, explicit structure, and predictable parsing.

It is designed for configuration files that should be easy to read, easy to write, and straightforward for parsers and tools to process.

**In simple terms:** YINI is a file format for storing application settings, similar in purpose to INI, JSON, YAML, or TOML configuration files. It is meant for settings such as app names, ports, feature flags, paths, database options, and tool configuration — but with a syntax that aims to stay readable, explicit, and predictable.

```ini
@yini

^ Application
name = 'Demo Application'
version = '1.0.0'
debug = yes

^^ Server
host = 'localhost'
port = 8080

^^^ Logging
level = 'info'
file = './app.log'
```

This represents the same kind of configuration data as this JSON:

```json
{
    "Application": {
        "name": "Demo Application",
        "version": "1.0.0",
        "debug": true,
        "Server": {
            "host": "localhost",
            "port": 8080,
            "Logging": {
                "level": "info",
                "file": "./app.log"
            }
        }
    }
}
```

Or this YAML:

```yaml
Application:
    name: Demo Application
    version: "1.0.0"
    debug: true
    Server:
        host: localhost
        port: 8080
        Logging:
            level: info
            file: ./app.log
```

Or this TOML:

```toml
[Application]
name = "Demo Application"
version = "1.0.0"
debug = true

[Application.Server]
host = "localhost"
port = 8080

[Application.Server.Logging]
level = "info"
file = "./app.log"
```

## Project status

The spec is in release candidate state and the core parsers are being validated against a shared test suite. Feedback, bug reports, and careful review are very welcome before 1.0.0 is finalised.

## Goals and design choices

YINI focuses on:

* **Clear and readable configuration files** — with `key = value` assignments, similar to classic INI files.
* **Explicit nested sections** — with repeated section markers, similar in spirit to Markdown headings.
* **Indentation-insensitive structure** — indentation is optional and may be used for readability, but does not define nesting.
* **Predictable parsing rules** — the same input should produce the same structure across implementations.
* **Minimal syntax surprises** — YINI prefers explicit rules over implicit rules or magic.
* **Human-friendly and parser-friendly structure** — files should be readable for people and straightforward for tools to process.
* **Practical use in real applications and tools** — YINI is intended for application settings, CLI tools, service configuration, and project metadata.

YINI is not intended to be clever or magical. The goal is a small, understandable configuration format with enough structure for serious use.

## Main repositories

* **[YINI-spec](https://github.com/YINI-lang/YINI-spec)** — the YINI language specification and grammar.
* **[yini-parser-typescript](https://github.com/YINI-lang/yini-parser-typescript)** — official Node.js / TypeScript parser implementation.
* **[yini-parser-python](https://github.com/YINI-lang/yini-parser-python)** — official Python parser implementation.
* **[yini-cli](https://github.com/YINI-lang/yini-cli)** — command-line tooling for validating and working with YINI files.
* **[yini-demo-apps](https://github.com/YINI-lang/yini-demo-apps)** — small demo applications showing how YINI can be used in real projects.
* **[syntax-highlighting](https://github.com/YINI-lang/syntax-highlighting)** — syntax highlighting definitions for editors that support TextMate grammars.
* **[yini-homepage](https://github.com/YINI-lang/yini-homepage)** — homepage and documentation site for YINI.

The shared parser test suite, **yini-test**, is currently private while it is being prepared for public use.

## Try YINI

The easiest way to understand YINI is to look at a small configuration file and parse it with one of the available tools.

You can try YINI through:

* The [TypeScript / Node.js](https://yini-lang.org/tools/yini-parser-ts/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme) parser.
* The [Python](https://yini-lang.org/tools/yini-parser-python/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme) parser.
* The [command-line](https://yini-lang.org/tools/yini-cli/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme) tool.
* [Small demo app](https://github.com/YINI-lang/yini-demo-apps) examples using YINI.
* [Third-party and other YINI tools](https://github.com/YINI-lang/YINI-spec/wiki/Get-YINI-Tools).
* Or jump to [Getting Started](https://yini-lang.org/use-yini/get-started/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme) guide on the YINI website.

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

## License

Released under MIT or Apache License 2.0 depending on the exact repository.

---

**^YINI ≡**

> A clear, structured, human-friendly configuration format.

[yini-lang.org](https://yini-lang.org/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme_footer)

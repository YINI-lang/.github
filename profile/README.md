# YINI-lang

**YINI** is an INI-inspired, indentation-insensitive configuration format with clear nested sections, explicit structure, and predictable parsing.

It is designed for configuration files that should be easy to read, easy to write, and straightforward for parsers and tools to process.

> Configuration should be clear to humans and predictable for tools.

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

## Try it now

```bash
# Python parser
pip install yini-parser

# Node.js / TypeScript parser
npm install yini-parser
```

Parse your first YINI file:

```bash
# Command-line tool
npx yini-cli parse config.yini

# Python
python -c "from yini_parser import load; print(load('config.yini'))"
```

Or jump to the [Getting Started](https://yini-lang.org/use-yini/get-started/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme_try) guide.

---

The above YINI represents the same kind of configuration data as this JSON:

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

## Why does YINI exist?

Many existing configuration formats are useful, but each comes with trade-offs:

* **INI** is simple, but often too flat.
  > **YINI keeps `key = value`, but adds nested sections.**
* **JSON** is explicit, but punctuation-heavy to edit by hand.
  > **YINI keeps structured values with less required punctuation.**
* **YAML** is flexible, but indentation can affect meaning.
  > **YINI uses section markers instead of whitespace to define structure.**
* **XML** is structured, but verbose for configuration.
  > **YINI supports hierarchy without opening and closing tags.**
* **TOML** is configuration-oriented, but deeply nested tables can become harder to scan.
  > **YINI makes nesting visible through repeated section markers.**

YINI is designed as a practical middle ground: familiar `key = value` configuration with explicit nested sections, useful data types, indentation-insensitive structure, and predictable parsing rules.

> The goal is not to replace every configuration format.

YINI is intentionally JSON-friendly: JSON remains a strong choice for data exchange, APIs, generated output, and many existing tools. YINI focuses on human-authored configuration, and `yini-cli` can convert YINI files to JSON when JSON is the better format for the next step.

## Who is YINI for?

YINI may be a good fit for:

- Developers building greenfield projects, internal tools, CLIs, services, or applications where they control the configuration stack.
- Projects that want human-edited configuration with comments, useful data types, and clear nested structure.
- Teams that like `key = value` simplicity, but need more structure than flat INI-style files.
- Tool authors and contributors interested in parsers, validation, test cases, examples, or documentation.

YINI is still an early-stage project, so it is best suited for experimentation, controlled projects, and internal tooling. Early adopters who are comfortable giving feedback are especially welcome — some tools are still in beta, and the 1.0.0 final release is not yet out.

## Project status

The YINI specification is currently in release candidate state 6. The core parser implementations are being validated against a shared test suite before the first stable `1.0.0` release.

Feedback, bug reports, parser comparisons, suggestions, and reviews are very welcome.

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
* **[yini-test](https://github.com/YINI-lang/yini-test)** — shared parser test suite for validating YINI parser implementations.
* **[yini-parser-typescript](https://github.com/YINI-lang/yini-parser-typescript)** — official Node.js / TypeScript parser implementation.
* **[yini-parser-python](https://github.com/YINI-lang/yini-parser-python)** — official Python parser implementation.
* **[yini-cli](https://github.com/YINI-lang/yini-cli)** — command-line tooling for validating and working with YINI files.
* **[yini-demo-apps](https://github.com/YINI-lang/yini-demo-apps)** — small demo applications showing how YINI can be used in real projects.
* **[syntax-highlighting](https://github.com/YINI-lang/syntax-highlighting)** — syntax highlighting definitions for editors that support TextMate grammars.
* **[yini-homepage](https://github.com/YINI-lang/yini-homepage)** — homepage and documentation site for YINI.

## More ways to explore YINI

The easiest way to understand YINI is to look at a small configuration file and parse it with one of the available tools.

You can try YINI through:

* The [TypeScript / Node.js](https://yini-lang.org/tools/yini-parser-ts/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme) parser.
* The [Python](https://yini-lang.org/tools/yini-parser-python/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme) parser.
* The [command-line](https://yini-lang.org/tools/yini-cli/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme) tool.
* [Small demo apps](https://github.com/YINI-lang/yini-demo-apps) using YINI.
* [Third-party and other YINI tools](https://github.com/YINI-lang/YINI-spec/wiki/Get-YINI-Tools).
* Or jump to the [Getting Started](https://yini-lang.org/use-yini/get-started/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme) guide on the YINI website.

Documentation and examples are available at:

**Homepage:** [yini-lang.org](https://yini-lang.org/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme)

## Contributing

Contributions are welcome, especially:

* Specification feedback.
* Parser bug reports.
* Test cases.
* Documentation improvements.
* Examples and integrations.
* Review of edge cases before `1.0.0`.

If you notice something unclear, surprising, inconsistent, or difficult to implement, please open an issue or discussion.

YINI is a early-stage project, so early feedback and real-world testing are especially valuable.

## Philosophy

YINI is built around a simple idea:

> Configuration should be clear to humans and predictable for tools.

The format favors explicit structure over hidden behavior, readability over cleverness, and consistency over shortcuts.

---

## License

Released under **MIT** or **Apache License 2.0** depending on the exact repository.

YINI repositories are released under the license shown in each repository:

| Repository             | License |
|------------------------|---------|
| YINI-spec              | Apache License 2.0 |
| yini-test              | Apache License 2.0 |
| yini-parser-typescript | Apache License 2.0 |
| yini-parser-python     | Apache License 2.0 |
| yini-cli               | Apache License 2.0 |
| yini-demo-apps         | MIT License |
| syntax-highlighting    | MIT License |
| yini-homepage          | MIT License |

---

> A clear, structured, human-friendly configuration format.

[yini-lang.org](https://yini-lang.org/?utm_source=github&utm_medium=referral&utm_campaign=yini_page&utm_content=readme_footer)

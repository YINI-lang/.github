# YINI-lang

**YINI** is an INI-inspired format for human-edited configuration. It uses familiar `key = value` assignments, supports nested sections and typed values, and does not use indentation to define structure.

```ini
@yini

^ Application
name    = 'Demo Application'
version = '1.0.0'
debug   = YES              // true works too

^^ Server
host = 'localhost'
port = 8080

^^^ Logging
level = 'info'
file  = './app.log'
```

Each section header starts with `^`; repeating it sets the nesting level (`^` is top-level, `^^` is a child, and `^^^` is a grandchild). Indentation is optional and does not affect the structure.

## Try it now

Try the example in the [YINI Playground](https://yini-lang.org/playground/?utm_source=github&utm_campaign=yini_page&utm_content=readme_try&utm_medium=referral), or save it as `config.yini` and use one of the tools below.

### Command line

Requires Node.js. Parse the file and print the result as JSON:

```bash
npx yini-cli parse config.yini
```

### Python

Install the Python parser, then parse the file:

```bash
pip install yini-parser
python -c "from yini_parser import load; print(load('config.yini'))"
```

### Node.js / TypeScript

To use YINI in your application, install the Node.js / TypeScript parser:

```bash
npm install yini-parser
```

See the [parser documentation](https://yini-lang.org/tools/yini-parser-ts/?utm_source=github&utm_campaign=yini_page&utm_content=readme&utm_medium=referral) for usage examples.

For a walkthrough, see the [Getting Started](https://yini-lang.org/use-yini/get-started/?utm_source=github&utm_campaign=yini_page&utm_content=readme_try&utm_medium=referral) guide. Go users can start with [yini-parser-go](https://github.com/YINI-lang/yini-parser-go) (alpha).

<details>
<summary>Compare the example with JSON, YAML, TOML, XML, and INI</summary>

The YINI example above represents the same kind of configuration data as this JSON:

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

Or this XML:

```xml
<Application>
    <name>Demo Application</name>
    <version>1.0.0</version>
    <debug>true</debug>
    <Server>
        <host>localhost</host>
        <port>8080</port>
        <Logging>
            <level>info</level>
            <file>./app.log</file>
        </Logging>
    </Server>
</Application>
```

In XML, the consuming application or schema defines how text values such as `true` and `8080` are interpreted.

Or this INI:

```ini
[Application]
name = Demo Application
version = 1.0.0
debug = true

[Application.Server]
host = localhost
port = 8080

[Application.Server.Logging]
level = info
file = ./app.log
```

In this INI example, dotted section names are a naming convention rather than built-in nesting. The consuming application determines how to interpret the section names and convert text values to numbers or booleans.

</details>

## Why does YINI exist?

YINI combines INI-style assignments with explicit nesting, comments, and typed values. Its section markers show the structure even when indentation changes. It is intended for configuration people write and review; established formats may fit better when a project already depends on their tooling.

## Who is YINI for?

If you write or maintain configuration that people edit by hand, YINI may be useful to explore for an app, service, or internal tool. If you're comparing formats or building tooling, you're welcome here too. Feel free to try the example, ask a question, or share what you find.

## Project status

The [YINI specification](https://yini-lang.org/refs/specification/?utm_source=github&utm_campaign=yini_page&utm_content=readme&utm_medium=referral) is at `1.0.0-RC.6`; the final `1.0.0` format release is still ahead. The TypeScript parser and CLI are available, the Python parser is in beta, and the Go parser is in alpha. YINI is best suited to experimentation and controlled projects for now. Check each tool's release notes and test it against your needs before adopting it.

## Main repositories

* **[YINI-spec](https://github.com/YINI-lang/YINI-spec)** — the YINI language specification and grammar.
* **[yini-test-suite](https://github.com/YINI-lang/yini-test-suite)** — shared parser test suite for validating YINI parser implementations.
* **[yini-parser-typescript](https://github.com/YINI-lang/yini-parser-typescript)** — official Node.js / TypeScript parser implementation.
* **[yini-parser-python](https://github.com/YINI-lang/yini-parser-python)** — official Python parser implementation.
* **[yini-parser-go](https://github.com/YINI-lang/yini-parser-go)** — official Go parser implementation (alpha).
* **[yini-cli](https://github.com/YINI-lang/yini-cli)** — command-line tooling for validating and working with YINI files.
* **[yini-demo-apps](https://github.com/YINI-lang/yini-demo-apps)** — small demo applications showing how YINI can be used in real projects.
* **[syntax-highlighting](https://github.com/YINI-lang/syntax-highlighting)** — syntax highlighting definitions for editors that support TextMate grammars.
* **[yini-homepage](https://github.com/YINI-lang/yini-homepage)** — homepage and documentation site for YINI.

For documentation and examples, visit [yini-lang.org](https://yini-lang.org/?utm_source=github&utm_campaign=yini_page&utm_content=readme&utm_medium=referral). See also [third-party and other YINI tools](https://github.com/YINI-lang/YINI-spec/wiki/Get-YINI-Tools).

## Questions and feedback

Questions are welcome. For help with YINI syntax, usage, or the project, start a thread in [YINI-lang Discussions](https://github.com/orgs/YINI-lang/discussions). If you find a parser or tool bug, open an issue in that repository. For specification errors or unclear rules, use [YINI-spec issues](https://github.com/YINI-lang/YINI-spec/issues).

## Contributing

Contributions are welcome, including test cases, documentation fixes, examples, and review of specification edge cases. Start with the relevant repository's README or issues.

## Philosophy

YINI is built around a simple idea:

> Configuration should be clear to humans and predictable for tools.

The format favors explicit structure over hidden behavior, readability over cleverness, and consistency over shortcuts.

---

## License

Licenses vary by repository. See each repository’s `LICENSE` file for the applicable terms.

<details>
<summary>Licenses by repository</summary>

| Repository             | License |
|------------------------|---------|
| YINI-spec              | Apache License 2.0 |
| yini-test-suite        | Apache License 2.0 |
| yini-parser-typescript | Apache License 2.0 |
| yini-parser-python     | Apache License 2.0 |
| yini-parser-go         | MIT License |
| yini-cli               | Apache License 2.0 |
| yini-demo-apps         | MIT License |
| syntax-highlighting    | MIT License |
| yini-homepage          | MIT License |

</details>

---

[yini-lang.org](https://yini-lang.org/?utm_source=github&utm_campaign=yini_page&utm_content=readme_footer&utm_medium=referral)

# BCL-32 core (Linux)

[![License: GPL-3.0-or-later](https://img.shields.io/badge/license-GPL--3.0--or--later-blue.svg)](LICENSE)

**BCL-32** is an interpreter for the **Basic Command Language 32** (kernel 1.2): a small,
text-based scripting language. This repository contains the **core for Linux only**: the
`bcl` interpreter, a man page, examples and the language manual. Native modules
(`.bll`) are distributed separately.

## The language in a nutshell

- A single data type: **string**. Arithmetic goes through `CALC` (real and complex numbers,
  bases 2/8/10/16).
- **1-based** indexes. Lists use `{}` for elements that contain spaces. Associative arrays.
- Two control structures: `IF … THEN … END` and the loop `IF … DO … LOOP`
  (with `BREAK`/`NEXT`). Plus procedures, `TRY … CATCH`, `GLOBAL`, `INCR`.
- `LOAD`/`SOURCE`, a module search path (`BCL_LIBS`) and a startup file (`$HOME/.bcl.rc`).

```bcl
SET age(ann) 31
SET age(lou) 27
PUTS "average: [CALC ($age(ann) + $age(lou)) / 2]"

PROC factorial WITH n DO
    IF $n <= 1 THEN
        RETURN 1
    END
    RETURN [CALC $n * [factorial [CALC $n - 1]]]
END
PUTS "5! = [factorial 5]"
```

## Build

Requirements: `gcc` and `make` (and optionally the `readline` development headers for
line editing in the interactive session). Nothing else.

```sh
make                       # builds bin/bcl
./bin/bcl --version
./bin/bcl examples/01_hola.bcl
./bin/bcl                  # interactive session
```

## Install

```sh
make install PREFIX=$HOME/.local     # binary, man pages (en, es), examples, docs
make uninstall PREFIX=$HOME/.local
```

`PREFIX` defaults to `/usr/local`; `DESTDIR` is honored for packaging. After installing,
`man bcl` shows the manual page (`LANG=es_ES.UTF-8 man bcl` in Spanish where available).

## Documentation

| | English | Español |
|---|---|---|
| Language manual | [`doc/manual.md`](doc/manual.md) | [`doc/manual.es.md`](doc/manual.es.md) |
| Man page | `man/bcl.1` | `man/es/bcl.1` |

Examples are in [`examples/`](examples) (bilingual comments).

## Layout

```
src/ include/   the interpreter: lexer → parser → eval → cmd (+ calc, evtsys)
examples/       nine small programs
man/            man page (English; Spanish in man/es/)
doc/            language manual (English and Spanish)
```

## License

GNU General Public License v3 or later — see [`LICENSE`](LICENSE). Scripts you write in BCL
are not covered by the GPL. The example programs may be freely reused in your own programs.

## Status

Development of this repository is closed: it is published as a finished snapshot and does not accept contributions.

# bun-tutorial

## Kaizen Bun Crash Course

### Ref

- [YT Kaizen Codes 2023-09-06 Bun Crash Course 2023 with HTMX example](https://www.youtube.com/watch?v=zNE5H6nOeCI)

  2.87K subscribers
  8,803 views Premiered Sep 6, 2023
  Bun Crash Course with HTMX todo app example at the end. This video was inspired by the release of Bun 1.0 on 7 September 2023.

Repository of crash course - https://github.com/Eckhardt-D/bun-cra...

Repository of example app - https://github.com/Eckhardt-D/bun-htm...

Bun - https://bun.sh
HTMX - https://htmx.org
Hyperscript - https://hyperscript.org
Pico CSS for the Styling - https://picocss.com
Elysia - https://elysiajs.com
Hono - https://hono.dev

---

A Bun Tutorial on the HTTP, WebSockets, CLI, File I/O and more. Followed by a simple Todo App built in Bun.

--

TIMESTAMPS
00:00 What we build at the end & installing
03:28 Bun CLI init, run & create
08:54 Bun build API and bunx CLI
14:28 Bun HTTP/HTTPS server
19:34 Bun WebSockets
24:10 Bun File I/O
35:48 Bun SQlite Database
38:06 Bun FileSystemRouter
41:00 Bun Test Runner
44:28 Bun HTMX app

### 00:00 What we build at the end & installing

- Install bun: see [bun home page](https://bun.sh/)
- `curl -fsSL https://bun.sh/install | bash`

```bash
victor@victorpc:KaizenCodes$ bun -v
1.0.0
victor@victorpc:KaizenCodes$ bun upgrade
Congrats! You're already on the latest version of bun (which is v1.0.0)
```

- [Bun Docs Quickstart](https://bun.sh/docs/quickstart)

### 03:28 Bun CLI init, run & create

```bash
victor@victorpc:KaizenCodes$ pwd
/home/victor/Work/Learn/Bun/KaizenCodes
victor@victorpc:KaizenCodes$ mkdir bun-tutorial
victor@victorpc:KaizenCodes$ cd bun-tutorial/
victor@victorpc:bun-tutorial$ bun init
bun init helps you get started with a minimal project and tries to guess sensible defaults. Press ^C anytime to quit

package name (bun-tutorial):
entry point (index.ts): src/index.ts

Done! A package.json file was saved in the current directory.
 + src/index.ts
 + .gitignore
 + tsconfig.json (for editor auto-complete)
 + README.md

To get started, run:
  bun run src/index.ts

code .

victor@victorpc:bun-tutorial$ bun run src/index.ts
Hello via Bun!
```

- TS just runs right out of the box
- running script

```bash
victor@victorpc:bun-tutorial$ bun run
bun-tutorial scripts:

 bun run dev
   bun run src/index.ts

1 scripts

victor@victorpc:bun-tutorial$ bun run dev
$ bun run src/index.ts
Hello via Bun!
```

- [bun create](https://bun.sh/docs/templates) from templates:

```text
bun create <template> [<destination>]

Assuming you don't have a local template with the same name, this command will download and execute the create-<template> package from npm. The following two commands will behave identically:

bun create remix

bunx create-remix
```

### 08:54 Bun build API and bunx CLI

### 14:28 Bun HTTP/HTTPS server

- http/https-server-01
- in one terminal:

```bash
bun run src/index.ts

# end with Ctrl-C
^C
victor@victorpc:bun-tutorial$
```

- in another terminal while server is running

```bash
victor@victorpc:bun-tutorial$ curl http://localhost:3000
http://localhost:3000/
victor@victorpc:bun-tutorial$ curl http://localhost:3000/hello
http://localhost:3000/hello
victor@victorpc:bun-tutorial$
```

### 19:34 Bun WebSockets

### 24:10 Bun File I/O

### 35:48 Bun SQlite Database

### 38:06 Bun FileSystemRouter

### 41:00 Bun Test Runner

### 44:28 Bun HTMX app

## bun install

To install dependencies:

```bash
bun install
```

To run:

```bash
bun run src/index.ts
```

This project was created using `bun init` in bun v1.0.0. [Bun](https://bun.sh) is a fast all-in-one JavaScript runtime.

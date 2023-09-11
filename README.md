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

- commit

```bash
victor@victorpc:bun-tutorial$ git log --stat
commit e8b0b6508c10061c9713716cb3c1894fd0be8799 (HEAD -> master)
Author: victorkane <victorkane@gmail.com>
Date:   Mon Sep 11 17:54:36 2023 -0300

    feat: http/https-server-01

 README.md    | 50 ++++++++++++++++++++++++++++++++++++++++++++++-
 package.json |  3 +++
 src/index.ts |  9 ++++++++-
 3 files changed, 60 insertions(+), 2 deletions(-)
```

- http/https-server-02 force error
- terminal one:

```bash
bun run src/index.ts

# end with Ctrl-C
^C
victor@victorpc:bun-tutorial$
```

- terminal two:

```bash
victor@victorpc:bun-tutorial$ curl http://localhost:3000/hello
oops!!
```

- terminal one:

```bash
victor@victorpc:bun-tutorial$ bun run src/index.ts
1 | import { type ServeOptions } from "bun"
2 |
3 | Bun.serve({
4 |   fetch(request: Request) {
5 |     throw new Error("bad request")
              ^
error: bad request
      at fetch (/home/victor/Work/Learn/Bun/KaizenCodes/bun-tutorial/src/index.ts:5:10)

^C
victor@victorpc:bun-tutorial$

# end with Ctrl-C
^C
victor@victorpc:bun-tutorial$
```

- By supplying https certificates, the code rem'd out in `src/index.ts` can serve to directly use https urls instead of http urls

### 19:34 Bun WebSockets

- http/https-server-03-websocket
- see `src/websocket.ts`
- Open a terminal in the project directory and open a websocket connection

```bash
victor@victorpc:bun-tutorial$ ls
bun.lockb  node_modules  package.json  README.md  src  tsconfig.json
victor@victorpc:bun-tutorial$ bun run src/websocket.ts

```

- Leaving that websocket connection open, in a browser code console, type

```ts
const ws2 = new WebSocket("ws://localhost:3000")
undefined
ws2.addEventListener("message", (data) => console.log(data))
undefined
ws2.send("Hello")
undefined
```

- The message is shown in the first terminal:

```bash
victor@victorpc:bun-tutorial$ ls
bun.lockb  node_modules  package.json  README.md  src  tsconfig.json
victor@victorpc:bun-tutorial$ bun run src/websocket.ts
A new client connected  # after new WebSocket `w2` created
Hello                   # after message sent
```

- Browser console also adds `MessageEvent` object it receives from the Bun websocket server

```text
MessageEvent {isTrusted: true, data: 'Hello from Bun WS', origin: 'ws://localhost:3000', lastEventId: '', source: null, …}
isTrusted
:
true
bubbles
:
false
cancelBubble
:
false
cancelable
:
false
composed
:
false
currentTarget
:
WebSocket {url: 'ws://localhost:3000/', readyState: 1, bufferedAmount: 0, onopen: null, onerror: null, …}
data
:
"Hello from Bun WS"
defaultPrevented
:
false
eventPhase
:
0
lastEventId
:
""
origin
:
"ws://localhost:3000"
ports
:
[]
returnValue
:
true
source
:
null
srcElement
:
WebSocket {url: 'ws://localhost:3000/', readyState: 1, bufferedAmount: 0, onopen: null, onerror: null, …}
target
:
WebSocket {url: 'ws://localhost:3000/', readyState: 1, bufferedAmount: 0, onopen: null, onerror: null, …}
timeStamp
:
159837.5
type
:
"message"
userActivation
:
null
[[Prototype]]
:
MessageEvent
```

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

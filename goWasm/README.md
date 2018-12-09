# Golang and WebAssembly - 29 Nov 2018
Slides and examples from a talk originally delivered on 29th of November, 2018 at [Golang Bristol Meetup](https://www.meetup.com/es-ES/golang-bristol/). By [Jorge Marin](https://github.com/chipironcin).

Examples taken from [Go WebAssembly Tutorial - Building a Calculator Tutorial](https://tutorialedge.net/golang/go-webassembly-tutorial/) by [Elliot Forbes](https://twitter.com/Elliot_F).

## Description
Assuming we are using Golang v1.11.2.

### 1_print
Prints something to the console.

1. Compile to wasm
2. Download wasm_exec.js
3. Run with go_js_wasm_exec (nodejs)
4. Start webserver
5. Navigate to localhost:2015/wasm_exec.html
6. Open the web inspector
7. Click the Run button

### 2_registerFunctions
Use Javascript functions to call wasm code.

1. Compile to wasm
2. Download wasm_exec.js
4. Start webserver
5. Navigate to localhost:2015/wasm_exec.html
6. Open the web inspector
7. Click the buttons

### 3_evaluatingDom
Read values form the DOM and act on them.

1. Compile to wasm
2. Download wasm_exec.js
4. Start webserver
5. Navigate to localhost:2015/wasm_exec.html
6. Open the web inspector
7. Fill values
8. Click the buttons

### 4_manipulatingDom
Display output to the webpage.

1. Compile to wasm
2. Download wasm_exec.js
4. Start webserver
5. Navigate to localhost:2015/wasm_exec.html
6. Open the web inspector
7. Fill values
8. Click the buttons

## Apendix
### Download helpers
curl -SsL "https://raw.githubusercontent.com/golang/go/go1.11.2/misc/wasm/go_js_wasm_exec" > go_js_wasm_exec

curl -SsL "https://raw.githubusercontent.com/golang/go/go1.11.2/misc/wasm/wasm_exec.html" > wasm_exec.html
curl -SsL "https://raw.githubusercontent.com/golang/go/go1.11.2/misc/wasm/wasm_exec.js" > wasm_exec.js

### Start a webserver in the current folder
docker run --rm -p 2015:2015 -v $(pwd):/srv abiosoft/caddy

### Compile golang into wasm
docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp -e GOARCH=wasm -e GOOS=js golang:1.11.2 go build -o test.wasm main.go

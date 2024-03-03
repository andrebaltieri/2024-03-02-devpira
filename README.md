# Demo 01 - Compilando Rust para Assembly
```
cargo new hello_rust
cd hello_rust
cargo build --release
cargo rustc --release -- --emit asm
# hello_rust/target/release/deps/hello_rust-914f3b082d833d50.s
```

# Demo 02 - Stack Based Virtual Machine em Rust
[https://github.com/andrebaltieri/rust-virtual-machine](https://github.com/andrebaltieri/rust-virtual-machine)

# Demo 03 - Intermediate Language
Rider > Tools > IL Viewer

# Demo 04 - WAT para WASM
```
(module
  (func $i (import "imports" "imported_func") (param i32))
  (func (export "exported_func")
    i32.const 42
    call $i
  )
)
```

```
https://webassembly.github.io/wabt/demo/wat2wasm/
```

[wat2wasm demo](https://webassembly.github.io/wabt/demo/wat2wasm/)

# Demo 05 - Rodando WASM via Browser
```
cargo new hello_wasm --lib
cd hello_wasm
cargo add wasm-bindgen
```

```rust
// The wasm-pack uses wasm-bindgen to build and generate JavaScript binding file.
// Import the wasm-bindgen crate.
use wasm_bindgen::prelude::*;

// Our Add function
// wasm-pack requires "exported" functions
// to include #[wasm_bindgen]
#[wasm_bindgen]
pub fn add(a: i32, b: i32) -> i32 {
  return a + b;
}
```

# Demo 06 - Rodando WASM via Terminal
```
wasmedge --version
wasmedge version 0.13.5

cd package
wasmedge --reactor rust_wasm_bg.wasm add 10 10
```

# Demo 07 - Rust para WASM
```
cargo new rust_wasm
```

```rust
fn main() {
    let num1: u32 = 10;
    let num2: u32 = 20;

    let result1 = num1 * num2;
    let result2 = num1 * num2 * 2;
    let result3 = result1 + result2;

    println!("Resultado: {}", result3);
}
```

# Demo 08 - Rodando WASM via Docker
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/965c4ce7-910d-412b-ba96-948fb8a7b26b/8c7685c9-722c-44a2-9ad2-cc0776098a3a/Untitled.png)

```
docker buildx build --platform wasi/wasm -t rust-wasm .
```

```
docker run --rm --runtime=io.containerd.wasmedge.v1 --platform=wasi/wasm rust-wasm:latest
```

```
hello world!
```
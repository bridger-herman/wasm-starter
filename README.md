# Rust WebAssembly starter code

(Theoretically) makes setting up a Rust+WebAssembly static site easier

## Steps for setup
1. Modify `build.sh` to output the correct wasm file:
```
wasm-bindgen ./target/wasm32-unknown-unknown/release/<YOUR_PROJECT_NAME.wasm> --out-dir ./assets/pkg --web --no-typescript
```


2. Change the locations of all the paths pointing to the wasm (where
   `your_project` is the name of the wasm file you output in step 1):
```
// index.js
import { example_wasm_fn } from './pkg/your_project.js'; // Example import

// importWasm.js
import { default as init } from './pkg/your_project.js';
// ...
wasm = await init('./assets/pkg/your_project_bg.wasm');
```

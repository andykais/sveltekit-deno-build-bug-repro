# deno sveltekit repro

## Setup
```
git clone git@github.com:andykais/sveltekit-deno-build-bug-repro.git
cd sveltekit-deno-build-bug-repro
deno task build
```

## Relevant versions
npm packages:
- `@sveltejs/kit`: `^2.0.0`
- `svelte`: `^5.0.0`
deno --version output:
```
deno 2.0.6 (stable, release, aarch64-apple-darwin)
v8 12.9.202.13-rusty
typescript 5.6.2
```

## `deno task build` output
```
Task build deno run -A --unstable-ffi --check npm:vite build && cd build && deno check mod.ts
Check file:///Users/andrew.kaiser/Code/andykais/forager/web/vite.config.ts.timestamp-1731337302345-545334dcf47c9.mjs
10:01:43 AM [vite-plugin-svelte] WARNING: The following packages have a svelte field in their package.json but no exports condition for svelte.

simple-svelte-autocomplete@2.5.2

Please see https://github.com/sveltejs/vite-plugin-svelte/blob/main/docs/faq.md#missing-exports-condition for details.
vite v5.4.6 building SSR bundle for production...
✓ 138 modules transformed.
Check file:///Users/andrew.kaiser/Code/andykais/forager/web/.svelte-kit/output/server/manifest-full.js
10:01:44 AM [vite-plugin-svelte] WARNING: The following packages have a svelte field in their package.json but no exports condition for svelte.

simple-svelte-autocomplete@2.5.2

Please see https://github.com/sveltejs/vite-plugin-svelte/blob/main/docs/faq.md#missing-exports-condition for details.
vite v5.4.6 building for production...
✓ 220 modules transformed.
.svelte-kit/output/client/_app/version.json                                    0.03 kB │ gzip:  0.05 kB
.svelte-kit/output/client/.vite/manifest.json                                  3.53 kB │ gzip:  0.64 kB
.svelte-kit/output/client/_app/immutable/assets/3.IfsinvDF.css                 0.59 kB │ gzip:  0.32 kB
.svelte-kit/output/client/_app/immutable/assets/0.0wKzBujP.css                 7.20 kB │ gzip:  2.06 kB
.svelte-kit/output/client/_app/immutable/entry/start.CZxGg5Hu.js               0.07 kB │ gzip:  0.08 kB
.svelte-kit/output/client/_app/immutable/chunks/misc.CeToUyeG.js               0.20 kB │ gzip:  0.18 kB
.svelte-kit/output/client/_app/immutable/chunks/lifecycle.Dq56zdb8.js          0.35 kB │ gzip:  0.24 kB
.svelte-kit/output/client/_app/immutable/nodes/0.RZmSd6Dt.js                   0.43 kB │ gzip:  0.32 kB
.svelte-kit/output/client/_app/immutable/chunks/disclose-version.BvK4xJ9g.js   1.19 kB │ gzip:  0.63 kB
.svelte-kit/output/client/_app/immutable/nodes/1.BAvJqHCY.js                   1.23 kB │ gzip:  0.64 kB
.svelte-kit/output/client/_app/immutable/chunks/2.CPcubMtF.js                  3.56 kB │ gzip:  1.80 kB
.svelte-kit/output/client/_app/immutable/chunks/index-client.CNp89A59.js       4.78 kB │ gzip:  2.18 kB
.svelte-kit/output/client/_app/immutable/entry/app.BcJGrDM_.js                 5.63 kB │ gzip:  2.65 kB
.svelte-kit/output/client/_app/immutable/chunks/runtime.6vKbvIId.js           11.54 kB │ gzip:  4.80 kB
.svelte-kit/output/client/_app/immutable/chunks/entry.BKKRM6zs.js             27.43 kB │ gzip: 10.92 kB
.svelte-kit/output/client/_app/immutable/nodes/3.zNfzFnFG.js                  73.60 kB │ gzip: 25.92 kB
✓ built in 415ms
Check file:///Users/andrew.kaiser/Code/andykais/forager/web/.svelte-kit/output/server/manifest-full.js
error: Uncaught (in worker "") (in promise) TypeError: Module not found "file:///Users/andrew.kaiser/Code/andykais/forager/web/.svelte-kit/output/runtime/control.js".
    at file:///Users/andrew.kaiser/Code/andykais/forager/web/.svelte-kit/output/server/index.js:65:23
    at async prerender (file:///Users/andrew.kaiser/Code/andykais/forager/web/node_modules/.deno/@sveltejs+kit@2.5.28/node_modules/@sveltejs/kit/src/core/postbuild/prerender.js:36:21)
    at async file:///Users/andrew.kaiser/Code/andykais/forager/web/node_modules/.deno/@sveltejs+kit@2.5.28/node_modules/@sveltejs/kit/src/utils/fork.js:23:16
error: Uncaught (in promise) Error: Unhandled error. ([Object: null prototype] {
  message: 'Uncaught (in promise) TypeError: Module not found "file:///Users/andrew.kaiser/Code/andykais/forager/web/.svelte-kit/output/runtime/control.js".\n' +
    '    at \x1b[0m\x1b[36mfile:///Users/andrew.kaiser/Code/andykais/forager/web/.svelte-kit/output/server/index.js\x1b[0m:\x1b[0m\x1b[33m65\x1b[0m:\x1b[0m\x1b[33m23\x1b[0m',
  fileName: 'file:///Users/andrew.kaiser/Code/andykais/forager/web/node_modules/.deno/@sveltejs+kit@2.5.28/node_modules/@sveltejs/kit/src/core/postbuild/prerender.js',
  lineNumber: 36,
  columnNumber: 21
})
    at NodeWorker.emit (ext:deno_node/_events.mjs:381:17)
    at NodeWorker.#handleError (node:worker_threads:117:10)
    at NodeWorker.#pollControl (node:worker_threads:137:30)
    at eventLoopTick (ext:core/01_core.js:175:7)
```

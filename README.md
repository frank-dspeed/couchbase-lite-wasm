# couchbase-lite-wasm
This is Couchbase Lite Compiled to WASM Implemented via WICG/direct-sockets contains examples for demo

## How does the Couchbase Cluster Sync Work?
This is using the direct-sockets API which is partially available in Chrome M100++++ under certain conditions.

- Installed PWA-s with a whitelisted origin (see chrome://flags -> Restricted API Origins)
- "isolated_storage": true declared in manifest.json
- Http policy headers present:
  - ```Cross-Origin-Opener-Policy: same-origin```
  - ```Cross-Origin-Embedder-Policy: require-corp```
- Non-managed Chrome OS (or possibly Mac/Windows, cannot guarantee though)

you don't need to specify --enable-blink-features=... or --enable-features=... -- these will be deduced from --restricted-api-origins=... and applied accordingly. but if so:
```
--enable-blink-features=DirectSockets --enable-features=DirectSockets --restricted-api-origins=https://localhost:8443
```

## Examples and Hosting/Access Patterns
1. wrapper around couchbase-lite-wasm to provide a read-only HTTP-Range-request based virtual file system for SQLite. It allows hosting an SQLite database on a static file hoster and querying that database from the browser without fully downloading it.
2. direct-sockets Experimental Chromium API to directly connect binary to a Couchbase Cluster 
3. Putting the Database into localStorage sessionStorage indexDB
4. couchbase-web a couchbase-lite-wasm fork that uses indexDB to store the deltas

## Based on the Rust Bindings we Create the WASM Builds
https://github.com/couchbaselabs/couchbase-lite-rust

instructions:
```
cargo
```

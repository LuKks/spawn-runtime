# spawn-runtime

Run prebuilt binary based on the process platform and arch

```
npm i spawn-runtime
```

## Usage

`bin/thing`

```js
#!/usr/bin/env node
require('spawn-runtime')('thing-runtime', __filename)
```

Executes `bin[thing]` from `node_modules/thing-runtime-linux-x64/package.json`

## API

#### `spawnRuntime(name, referrer, [opts])`

Execs the `bin` that matches the basename of `referrer`, from:

`node_modules/{name}-{platform}-{arch}/package.json`

## License

Apache-2.0

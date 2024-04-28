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

## Export the path

Optionally, the binary path can also be exported to spawn it via code:

`index.js`

```js
const runtime = require('spawn-runtime')
module.exports = runtime('thing-runtime', 'thing', { spawn: false })
```

`another-project/app.js`

```js
const { spawn } = require('child_process')
const thingPath = require('../index.js')

const thing = spawn(thingPath, ...)
```

## API

#### `runtime(name, referrer, [options])`

Execs the `bin` that matches the basename of `referrer`, from:

`node_modules/{name}-{platform}-{arch}/package.json`

Available `options`:

```js
{
  platform: process.platform,
  arch: process.arch,
  spawn: true // Disable it to return the actual binary path instead
}
```

## License

Apache-2.0

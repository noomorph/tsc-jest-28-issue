## Reproduction

1. Try with DefinitelyTyped:

```sh
cd definitely-typed
npm i
npm test # runs TSC
```

Result:

```plain text
> definitely-typed@1.0.0 test
> tsc
```

The compilation passes.

2. Now try with Jest 28:

```sh
cd vanilla-jest-28
npm i
npm test # runs TSC
```

Result:

```plain text
> definitely-typed@1.0.0 test
> tsc

globals.test.ts(1,1): error TS2593: Cannot find name 'describe'. Do you need to install type definitions for a test runner? Try `npm i --save-dev @types/jest` or `npm i --save-dev @types/mocha` and then add 'jest' or 'mocha' to the types field in your tsconfig.
globals.test.ts(2,3): error TS2304: Cannot find name 'beforeEach'.
globals.test.ts(6,3): error TS2593: Cannot find name 'it'. Do you need to install type definitions for a test runner? Try `npm i --save-dev @types/jest` or `npm i --save-dev @types/mocha` and then add 'jest' or 'mocha' to the types field in your tsconfig.
```

## Debug info

Let's make sure that both projects are configured correctly and
take the typing files as expected by using a debug command:

```sh
npx tsc --listFilesOnly
```

You will see below that the both find the specified typings.

### DefinitelyTyped

```plain text
.../definitely-typed/node_modules/typescript/lib/lib.es5.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2015.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2016.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.dom.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.dom.iterable.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.webworker.importscripts.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.scripthost.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2015.core.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2015.collection.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2015.generator.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2015.iterable.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2015.promise.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2015.proxy.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2015.reflect.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2015.symbol.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2015.symbol.wellknown.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2016.array.include.d.ts
.../definitely-typed/node_modules/typescript/lib/lib.es2016.full.d.ts
.../definitely-typed/globals.test.ts
.../definitely-typed/node_modules/chalk/index.d.ts
.../definitely-typed/node_modules/jest-diff/build/cleanupSemantic.d.ts
.../definitely-typed/node_modules/pretty-format/build/types.d.ts
.../definitely-typed/node_modules/pretty-format/build/index.d.ts
.../definitely-typed/node_modules/jest-diff/build/types.d.ts
.../definitely-typed/node_modules/jest-diff/build/diffLines.d.ts
.../definitely-typed/node_modules/jest-diff/build/printDiffs.d.ts
.../definitely-typed/node_modules/jest-diff/build/index.d.ts
.../definitely-typed/node_modules/jest-matcher-utils/build/index.d.ts
.../definitely-typed/node_modules/@types/jest/index.d.ts
```

### Vanilla Jest 28

```diff
../vanilla-jest-28/node_modules/typescript/lib/lib.es5.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2015.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2016.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2017.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2018.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2019.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2020.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.dom.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.dom.iterable.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.webworker.importscripts.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.scripthost.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2015.core.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2015.collection.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2015.generator.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2015.iterable.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2015.promise.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2015.proxy.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2015.reflect.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2015.symbol.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2015.symbol.wellknown.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2016.array.include.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2017.object.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2017.sharedmemory.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2017.string.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2017.intl.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2017.typedarrays.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2018.asyncgenerator.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2018.asynciterable.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2018.intl.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2018.promise.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2018.regexp.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2019.array.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2019.object.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2019.string.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2019.symbol.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2020.bigint.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2020.promise.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2020.sharedmemory.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2020.string.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2020.symbol.wellknown.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2020.intl.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.esnext.intl.d.ts
../vanilla-jest-28/node_modules/typescript/lib/lib.es2016.full.d.ts
../vanilla-jest-28/globals.test.ts
../vanilla-jest-28/node_modules/@types/node/assert.d.ts
../vanilla-jest-28/node_modules/@types/node/assert/strict.d.ts
../vanilla-jest-28/node_modules/@types/node/globals.d.ts
../vanilla-jest-28/node_modules/@types/node/async_hooks.d.ts
../vanilla-jest-28/node_modules/@types/node/buffer.d.ts
../vanilla-jest-28/node_modules/@types/node/child_process.d.ts
../vanilla-jest-28/node_modules/@types/node/cluster.d.ts
../vanilla-jest-28/node_modules/@types/node/console.d.ts
../vanilla-jest-28/node_modules/@types/node/constants.d.ts
../vanilla-jest-28/node_modules/@types/node/crypto.d.ts
../vanilla-jest-28/node_modules/@types/node/dgram.d.ts
../vanilla-jest-28/node_modules/@types/node/diagnostics_channel.d.ts
../vanilla-jest-28/node_modules/@types/node/dns.d.ts
../vanilla-jest-28/node_modules/@types/node/dns/promises.d.ts
../vanilla-jest-28/node_modules/@types/node/domain.d.ts
../vanilla-jest-28/node_modules/@types/node/events.d.ts
../vanilla-jest-28/node_modules/@types/node/fs.d.ts
../vanilla-jest-28/node_modules/@types/node/fs/promises.d.ts
../vanilla-jest-28/node_modules/@types/node/http.d.ts
../vanilla-jest-28/node_modules/@types/node/http2.d.ts
../vanilla-jest-28/node_modules/@types/node/https.d.ts
../vanilla-jest-28/node_modules/@types/node/inspector.d.ts
../vanilla-jest-28/node_modules/@types/node/module.d.ts
../vanilla-jest-28/node_modules/@types/node/net.d.ts
../vanilla-jest-28/node_modules/@types/node/os.d.ts
../vanilla-jest-28/node_modules/@types/node/path.d.ts
../vanilla-jest-28/node_modules/@types/node/perf_hooks.d.ts
../vanilla-jest-28/node_modules/@types/node/process.d.ts
../vanilla-jest-28/node_modules/@types/node/punycode.d.ts
../vanilla-jest-28/node_modules/@types/node/querystring.d.ts
../vanilla-jest-28/node_modules/@types/node/readline.d.ts
../vanilla-jest-28/node_modules/@types/node/repl.d.ts
../vanilla-jest-28/node_modules/@types/node/stream.d.ts
../vanilla-jest-28/node_modules/@types/node/stream/promises.d.ts
../vanilla-jest-28/node_modules/@types/node/stream/consumers.d.ts
../vanilla-jest-28/node_modules/@types/node/stream/web.d.ts
../vanilla-jest-28/node_modules/@types/node/string_decoder.d.ts
../vanilla-jest-28/node_modules/@types/node/timers.d.ts
../vanilla-jest-28/node_modules/@types/node/timers/promises.d.ts
../vanilla-jest-28/node_modules/@types/node/tls.d.ts
../vanilla-jest-28/node_modules/@types/node/trace_events.d.ts
../vanilla-jest-28/node_modules/@types/node/tty.d.ts
../vanilla-jest-28/node_modules/@types/node/url.d.ts
../vanilla-jest-28/node_modules/@types/node/util.d.ts
../vanilla-jest-28/node_modules/@types/node/v8.d.ts
../vanilla-jest-28/node_modules/@types/node/vm.d.ts
../vanilla-jest-28/node_modules/@types/node/wasi.d.ts
../vanilla-jest-28/node_modules/@types/node/worker_threads.d.ts
../vanilla-jest-28/node_modules/@types/node/zlib.d.ts
../vanilla-jest-28/node_modules/@types/node/globals.global.d.ts
../vanilla-jest-28/node_modules/@types/node/index.d.ts
../vanilla-jest-28/node_modules/@types/yargs-parser/index.d.ts
../vanilla-jest-28/node_modules/@types/yargs/index.d.ts
../vanilla-jest-28/node_modules/@types/istanbul-lib-coverage/index.d.ts
../vanilla-jest-28/node_modules/chalk/index.d.ts
../vanilla-jest-28/node_modules/@types/istanbul-lib-report/index.d.ts
../vanilla-jest-28/node_modules/@types/istanbul-reports/index.d.ts
../vanilla-jest-28/node_modules/@sinclair/typebox/typebox.d.ts
../vanilla-jest-28/node_modules/@jest/schemas/build/index.d.ts
../vanilla-jest-28/node_modules/@jest/types/build/index.d.ts
../vanilla-jest-28/node_modules/jest-mock/build/index.d.ts
../vanilla-jest-28/node_modules/@types/stack-utils/index.d.ts
../vanilla-jest-28/node_modules/jest-message-util/build/index.d.ts
../vanilla-jest-28/node_modules/@jest/fake-timers/build/index.d.ts
../vanilla-jest-28/node_modules/@jest/environment/build/index.d.ts
../vanilla-jest-28/node_modules/@types/graceful-fs/index.d.ts
../vanilla-jest-28/node_modules/jest-haste-map/build/index.d.ts
../vanilla-jest-28/node_modules/@jest/expect-utils/build/index.d.ts
../vanilla-jest-28/node_modules/expect/node_modules/pretty-format/build/index.d.ts
../vanilla-jest-28/node_modules/expect/node_modules/jest-diff/build/index.d.ts
../vanilla-jest-28/node_modules/expect/node_modules/jest-matcher-utils/build/index.d.ts
../vanilla-jest-28/node_modules/expect/build/index.d.ts
../vanilla-jest-28/node_modules/jest-snapshot/node_modules/pretty-format/build/index.d.ts
../vanilla-jest-28/node_modules/jest-snapshot/build/index.d.ts
../vanilla-jest-28/node_modules/@jest/expect/build/index.d.ts
../vanilla-jest-28/node_modules/@jest/globals/build/index.d.ts
```


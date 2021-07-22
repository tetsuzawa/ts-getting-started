# memo

## esmodules

package.jsonのtypeをcommonjs（or 書かない）にすると、srcでimportを使った場合エラーがでる。
```json
{
  "type": "commonjs",
  ...
}
```

```console
$ tree src/                                                                                                                   29.3s  Thu Jul 22 14:21:46 2021
src/
├── increment.ts
└── index.ts

0 directories, 2 files
```

```console
$ node dist/index.ts                                                                                                                  Thu Jul 22 14:21:00 2021
(node:8934) Warning: To load an ES module, set "type": "module" in the package.json or use the .mjs extension.
(Use `node --trace-warnings ...` to show where the warning was created)
/Users/t-takizawa/repo/ts-getting-started/dist/index.ts:1
import { increment } from "./increment";
^^^^^^

SyntaxError: Cannot use import statement outside a module
    at wrapSafe (internal/modules/cjs/loader.js:979:16)
    at Module._compile (internal/modules/cjs/loader.js:1027:27)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:1092:10)
    at Module.load (internal/modules/cjs/loader.js:928:32)
    at Function.Module._load (internal/modules/cjs/loader.js:769:14)
    at Function.executeUserEntryPoint [as runMain] (internal/modules/run_main.js:72:12)
    at internal/main/run_main_module.js:17:47
```

.mjsならエラーは出ない

`"type": "module"`は全ソースが対応してないから使いづらい。
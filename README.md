## What's the issue?

In this repo I'm using [pnpm](https://pnpm.io/) and [nx](https://nx.dev/)
together to try to do a monorepo to develop a lib related with
[remix.run](https://remix.run). In this repo I want to have the lib and also
some remix apps to play with the lib's code.

```
root-folder
  |-packages
  | |-package-1
  | |-package-2
  | |-...
  | |
  |-examples
    |-basic-example
    |-another-example
    |-...
    |
```

I'm using [this @nrwl/remix NX's plugin]\*(https://www.npmjs.com/package/@nrwl/remix) for creating Remix apps. Although I think this is not the issue.

## The issue

When I try to run test in any of the packages like this:

```
$ nx test foolib --verbose

```

I get this error:

```
/Users/me/code/unexpected-export/node_modules/.pnpm/@babel+types@7.17.0/node_modules/@babel/types/lib/ast-types/generated/index.js:1
export { createFileSessionStorage, unstable_createFileUploadHandler, unstable_createMemoryUploadHandler, unstable_parseMultipartFormData, } from "@remix-run/node";
^^^^^^

SyntaxError: Unexpected token 'export'
    at Object.compileFunction (node:vm:352:18)
    at wrapSafe (node:internal/modules/cjs/loader:1031:15)
    at Module._compile (node:internal/modules/cjs/loader:1065:27)
    at Object.Module._extensions..js (node:internal/modules/cjs/loader:1153:10)
    at Module.load (node:internal/modules/cjs/loader:981:32)
    at Function.Module._load (node:internal/modules/cjs/loader:822:12)
    at Module.require (node:internal/modules/cjs/loader:1005:19)
    at require (node:internal/modules/cjs/helpers:102:18)
    at Object.<anonymous> (/Users/andres/code/opensource/unexpected-export/node_modules/.pnpm/@babel+types@7.17.0/node_modules/@babel/types/lib/index.js:629:19)
    at Module._compile (node:internal/modules/cjs/loader:1101:14)
```

Wait, what? I'm not using at all Remix yet inside of the packages. In this case `foolib`.

For testing I'm using [jest]\*(https://jestjs.io/).

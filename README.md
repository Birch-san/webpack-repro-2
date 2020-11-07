### Webpack 5 importing "libraries bundled by webpack"

Variation on [previous repro](https://github.com/Birch-san/webpack-repro).

Differences compared to previous repro:

- Using `pnpm` to manage monorepo, instead of manually making symlinks
- Upgraded webpack to 5.4.0 (previously 5.0.0)
- Upgraded webpack-cli to 4.2.0 (previously 3.3.12)
- Didn't use `webpack-dev-server`

```bash
# install pnpm (if you don't have it already)
npm i -g pnpm
pnpm i --frozen-lockfile
pnpm run --filter='@my-cool-project/*' build
```

Then open [`web/index.html`](web/index.html) in a web browser.

You'll see the following logged:

```
Uncaught TypeError: __webpack_require__.r is not a function
    <anonymous> webpack://lib/./src/index.js?:1
    js file:///Users/birch/git/webpack-repro-2/web/dist/main.js:2
    __nested_webpack_require_3051__ file:///Users/birch/git/webpack-repro-2/web/dist/main.js:2
    factory file:///Users/birch/git/webpack-repro-2/web/dist/main.js:2
    factory file:///Users/birch/git/webpack-repro-2/web/dist/main.js:2
    247 file:///Users/birch/git/webpack-repro-2/web/dist/main.js:2
    __webpack_require__ file:///Users/birch/git/webpack-repro-2/web/dist/main.js:2
    <anonymous> file:///Users/birch/git/webpack-repro-2/web/dist/main.js:2
    <anonymous> file:///Users/birch/git/webpack-repro-2/web/dist/main.js:2
    <anonymous> file:///Users/birch/git/webpack-repro-2/web/dist/main.js:2
```
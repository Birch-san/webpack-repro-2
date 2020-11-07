### Webpack 5 importing "libraries bundled by webpack"

Variation on [previous repro](https://github.com/Birch-san/webpack-repro). This configuration **seems to work**.

Differences compared to previous repro:

- Using `pnpm` to manage monorepo, instead of manually making symlinks
- Upgraded webpack to 5.4.0 (previously 5.0.0)
- Upgraded webpack-cli to 4.2.0 (previously 3.3.12)
- Didn't use `webpack-dev-server`
- Deleted code from webpack.config.js pertaining to devServer and build mode (i.e. development/production)

```bash
# install pnpm (if you don't have it already)
npm i -g pnpm
pnpm i --frozen-lockfile
pnpm run --filter='@my-cool-project/*' build
```

Then open [`web/index.html`](web/index.html) in a web browser.  
You'll see `         hello world` logged into the console, which indicates that this **works** (whereas the [previous repro](https://github.com/Birch-san/webpack-repro) encountered an error instad).

So, maybe:

- Webpack 5.4.0 helps?
- Webpack-cli 4.2.0 helps?
  - Unlikely to matter
- Not using `webpack-dev-server` helps?
- Production (as opposed to development) bundle helps?
  - I've left this as defaults, so don't know which mode was used ultimately
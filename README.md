# heroku-buildpack-bun

Heroku buildpack for Bun.js

Largely copied from https://github.com/chibat/heroku-buildpack-deno

You can optionally control the specific version by setting the BUN_VERSION environment-level variable to an explicit version e.g. 1.0.14

Be aware that Heroku doesn't use a new enough version of the Linux kernel to support `io_uring`, which is needed for `Bun.write()`. Use `node:fs.writeFile()` instead.

## How do I use this?
This is a third party heroku buildpack, so you will need to follow [the instructions provided by Heroku](https://devcenter.heroku.com/articles/buildpacks#using-a-third-party-buildpack) to enable it for your app.
You will need to assign the buildpack via the `heroku buildpacks:set` command.

If your app's entrypoint is at `src/index.ts`, here's an example `Procfile` you could potentially use:

```Procfile
web: bun install --frozen-lockfile && bun src/index.ts
```

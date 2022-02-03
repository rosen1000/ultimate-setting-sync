# NPM great cli tools

## [pnpm](https://npmjs.com/package/pnpm)

Fast and Efficient replacement for npm

| Command         | Commend                      |
| --------------- | ---------------------------- |
| pnpm install    | install from package.json    |
| pnpm add \<pkg> | install package              |
| pnpm run \<cmd> | run script from package.json |
| pnpx \<pkg>     | execute cli package          |
| pnpm env \<cmd> | manage node.js version       |

`~/.npmrc`

```toml
shamefully-hoist=true
```

Instead of `nvm` use `pnpm env`

```sh
pnpm env use --global lts
```

## [degit](https://www.npmjs.com/package/degit)

Can use with npx/pnpx
Download git repo without the .git folder
Decreases folder size and increases download speed

```sh
npx degit https://github.com/jesseduffield/lazygit.git
```

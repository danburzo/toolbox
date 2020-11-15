# new mac, who dis?

Things useful for moving to a new machine.

To list all tools installed with Homebrew:

```bash
brew leaves
```

To list all global npm packages:

```bash
npm ls -g
```

(The yarn equivalent is `yarn global list`).

To see which binaries have been installed wit npm:

```bash
ls -l $(npm bin -g) | grep node_modules
```
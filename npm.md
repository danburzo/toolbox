## Weaning yourself off yarn

Here are plain npm alternatives to yarn commands. 

### Install a local package

```bash
# Instead of:
yarn add [--dev] <package>

# Write:
npm install [--save-dev] <package>
```

### Install a global package

```bash
# Instead of:
yarn global add <package>

# Write
npm install -g <package>
```

### Publish a package to npm

```bash
# Instead of:
yarn publish

# Write:
npm version [major|minor|patch]
npm publish
```

### Run a script

```bash
# Instead of:
yarn <script-name>

# Write:
npm run-script <script-name>
```

### Run a local binary

```bash
# Instead of:
yarn <bin-name>

# Write:
npx <bin-name>
```

Use the `--no-install` flag prevent `npx` from fetching a missing binary from the npm registry.
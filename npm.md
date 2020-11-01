## npm gotchas

### Glob expansion in scripts

When running `npm run <script-name>`, the attached command gets executed within the shell linked at `/bin/sh` rather than your current shell. A pattern such as:

```bash
{src,test}/**/*.js
```

...is expanded differently in GNU sh, versus bash or zsh, leading to subtle bugs. Instead, defer the glob expansion to the particular tool you're running, if it has this feature:

```js
{
	"scripts": {
		// Instead of:
		"lint": "eslint {src,test}/**/*.js",

		// Write it with quotes:
		"lint": "eslint '{src,test}/**/*.js'"
	}
}
```

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

# Or, shorter:
npm run <script-name>
```

### Run a local binary

```bash
# Instead of:
yarn <bin-name>

# Write:
npx <bin-name>
```

Use the `--no-install` flag prevent `npx` from fetching a missing binary from the npm registry.
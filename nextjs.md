# Learning Next.js 

## Deploy a Next.js website to GitHub pages

_Note: this is assuming you want to deploy a project page served off the `gh-pages` branch from a GitHub repo, using Yarn and the [`gh-pages`](https://npmjs.com/package/gh-pages) package._

Scripts to include in `package.json`:

```json
{
	"scripts": {
		"build": "next build",
		"export": "next export -d dist",
		"deploy": "yarn build && yarn export && gh-pages -d dist --dotfiles"
	}
}
```

`next export` generates a static HTML build of the website (`-d` option controls the output folder). Their docs have some [instructions for deploying to GH Pages](https://github.com/zeit/next.js/wiki/Deploying-a-Next.js-app-into-GitHub-Pages), from which we learn a few things.

__We need a `.nojekyll` file__ in the root of the bundle to [allow underscores in file/folder names](https://github.blog/2009-12-29-bypassing-jekyll-on-github-pages/). We'll create this empty file in the `static/` folder of our app.

For a project file, we'll need to __configure the prefix__ for fetching assets to include the repository name.

Here's what to include in `next.config.js`:

```js
const fs = require('fs');
const { join } = require('path');
const { promisify } = require('util');
const withCSS = require('@zeit/next-css');

const pkg = require('./package.json');

const copyFile = promisify(fs.copyFile);

module.exports = withCSS({
	/*
		`exportPathMap` allows us to copy static files over to the `outDir`
		when exporting the static HTML bundle.
	 */
	exportPathMap: async function(defaultPathMap, { dev, dir, outDir }) {
		if (dev) {
			return defaultPathMap;
		}
		// copy the .nojekyll file
		await copyFile(
			join(dir, 'static/.nojekyll'),
			join(outDir, '.nojekyll')
		);
		return defaultPathMap;
	},

	// When building for production 
	// (as is the case with a static HTML export),
	// include the repository name as a prefix 
	// Note: here we're reading the repo name from the `name`
	// field in package.json, YMMV on this one.
	assetPrefix: process.env.NODE_ENV === 'production' ? `/${pkg.name}` : ''
});
```

Finally, note that `gh-pages` won't push dotfiles by default, so we need to use the `--dotfiles` flag in our `deploy` script in `package.json`.

> You may also want to include `rm -rf .next` as the first command in your `yarn deploy` script, as Next.js will [not delete previous builds](https://github.com/zeit/next.js/issues/6009) and will cause files to accumulate on your `gh-pages` branch.


## Next.js + MDX

MDX is pretty cool to work with, and Next.js + MDX is a killer combo.

### Limitations

* I wish you could wrap Markdown content in HTML tags / components though. [Discussion here](https://github.com/mdx-js/mdx/issues/241).
* Next.js does not work out-of-the-box with collocated `.mdx` files (scattered around the source code), you need to have everything in the `pages/` folder. 
[Dynamic Routes](https://github.com/zeit/next.js/issues/7607) should be cool.
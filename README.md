*Looking for a shareable component template? Go here --> [sveltejs/component-template](https://github.com/sveltejs/component-template)*

---

# svelte app

This is a project template for [Svelte](https://svelte.dev) apps.

**It is a modified version of the [default template](https://github.com/sveltejs/template) with some pitfalls for github pages removed.**

To create a new project based on this template using [degit](https://github.com/Rich-Harris/degit):

```bash
npx degit DavidM42/svelte-github-pages-template svelte-app
cd svelte-app
```

or manually via git clone

```bash
git clone https://github.com/DavidM42/template.git svelte-app
cd svelte-app
rm -r .git
```

or use the template button on GitHub

*Note that you will need to have [Node.js](https://nodejs.org) installed.*


## Get started

Install the dependencies...

```bash
cd svelte-app
npm install
```

...then start [Rollup](https://rollupjs.org):

```bash
npm run dev
```

Navigate to [localhost:5000](http://localhost:5000). You should see your app running. Edit a component file in `src`, save it, and reload the page to see your changes.

By default, the server will only respond to requests from localhost. To allow connections from other computers, edit the `sirv` commands in package.json to include the option `--host 0.0.0.0`.

If you're using [Visual Studio Code](https://code.visualstudio.com/) we recommend installing the official extension [Svelte for VS Code](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode). If you are using other editors you may need to install a plugin in order to get syntax highlighting and intellisense.

## Building and running in production mode

To create an optimised version of the app:

```bash
npm run build
```

You can run the newly built app with `npm run start`. This uses [sirv](https://github.com/lukeed/sirv), which is included in your package.json's `dependencies` so that the app will work when you deploy to platforms like [Heroku](https://heroku.com).


## Single-page app mode

By default, sirv will only respond to requests that match files in `public`. This is to maximise compatibility with static fileservers, allowing you to deploy your app anywhere.

If you're building a single-page app (SPA) with multiple routes, sirv needs to be able to respond to requests for *any* path. You can make it so by editing the `"start"` command in package.json:

```js
"start": "sirv public --single"
```

## Using TypeScript

This template comes with a script to set up a TypeScript development environment, you can run it immediately after cloning the template with:

```bash
node scripts/setupTypeScript.js
```

Or remove the script via:

```bash
rm scripts/setupTypeScript.js
```

## Deploying to GitHub pages

Everything should be set up ready to deploy to GitHub pages **even when you want to use SPA routing**.
Just push to master of your own GitHub repo and the GitHub actions script will do the hard work for you.

If you use a custom domain (instead of the nested URL structure following the `username.github.io/project-name/` schema), you have to change

```javascript
var pathSegmentsToKeep = 1;
```

to

```javascript
var pathSegmentsToKeep = 0;
```

in `public/404.html`.

### Routing problems

As far as I know there is no good way of using svelte-router (client side routing) with a root URL containing a path already and still being able to develop it locally.

For this reason I advise to use a custom (sub-)domain if you plan on using svelte-router.
After provisioning the custom domain, you can change the static paths in `public/index.html` back to root based ones.

```html
<link rel='icon' type='image/png' href='favicon.png'>
<link rel='stylesheet' href='global.css'>
<link rel='stylesheet' href='build/bundle.css'>
<script defer src='build/bundle.js'></script>
<!-- TO -->
<link rel='icon' type='image/png' href='/favicon.png'>
<link rel='stylesheet' href='/global.css'>
<link rel='stylesheet' href='/build/bundle.css'>
<script defer src='/build/bundle.js'></script>
```

Following these changes your use of svelte-router in GitHub pages should hopefully work.

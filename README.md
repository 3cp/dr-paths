Demo for using requirejs config paths to map external modules

In gulpfile
```
const dr = dumber({
  paths: {
    // module "external/foo/bar" will load from http://localhost:9000/external/foo/bar.js
    external: 'http://localhost:9000/external'
  },
```

Then in code, you can load module "external/foo/bar" in any fashion.
* You can just loaded from `import {...} from 'external/foo/bar'`, requirejs will handle the
asynchronous loading.
* You can use dynamic `import('external/foo/bar').then(module => module.Bar)`.
* You can let aurelia-loader to handle resource marked by string `'external/foo/bar'` in
compose or router config.

-----
# dr-paths

An app using dumber bundler to build. More details in `gulpfile.js`.

## Run in dev mode, plus watch

    npm start

## Run in production mode, plus watch

It updates index.html with hashed file name.

    npm run start:prod

## Build in dev mode

Generates `dist/*-bundle.js`

    npm run build:dev

## Build in production mode

    npm run build

It builds `dist/*-bundle.[hash].js`, updates index.html with hashed js bundle file name. To deploy to production server, copy over both the generated `index.html` and all the `dist/*` files.

For example
```
index.html
dist/entry-bundle.12345.js
```
Copy to production root folder
```
root_folder/index.html
root_folder/dist/entry-bundle.12345.js
```
## To clear cache

Clear tracing cache. In rare situation, you might need to run clear-cache after upgrading to new version of dumber bundler.

    npm run clear-cache



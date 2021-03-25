---
title: make a markdown blog with next.js
---

## based on tutorial [here](https://jfelix.info/blog/how-to-make-a-static-blog-with-next-js)
## creating a Next.js project
### `yarn create next-app`
### `yarn create v1.22.10
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
success Installed "create-next-app@10.0.9" with binaries:
      - create-next-app
✔ What is your project named? … next-app
Creating a new Next.js app in /Users/manfredsteiner/Applications/next/next-app.

Installing react, react-dom, and next using yarn...

yarn add v1.22.10
info No lockfile found.
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 172 new dependencies.
info Direct dependencies
├─ next@10.0.9
├─ react-dom@17.0.2
└─ react@17.0.2
info All dependencies
├─ @babel/code-frame@7.12.11
├─ @babel/helper-validator-identifier@7.12.11
├─ @babel/highlight@7.13.10
├─ @babel/runtime@7.12.5
├─ @babel/types@7.8.3
├─ @hapi/accept@5.0.1
├─ @hapi/boom@9.1.2
├─ @next/env@10.0.9
├─ @next/polyfill-module@10.0.9
├─ @next/react-dev-overlay@10.0.9
├─ @next/react-refresh-utils@10.0.9
├─ @opentelemetry/api@0.14.0
├─ @opentelemetry/context-base@0.14.0
├─ anser@1.4.9
├─ ansi-regex@5.0.0
├─ ansi-styles@3.2.1
├─ anymatch@3.1.1
├─ asn1.js@5.4.1
├─ assert@1.5.0
├─ ast-types@0.13.2
├─ babel-plugin-syntax-jsx@6.18.0
├─ big.js@5.2.2
├─ binary-extensions@2.2.0
├─ braces@3.0.2
├─ brorand@1.1.0
├─ browserify-aes@1.2.0
├─ browserify-cipher@1.0.1
├─ browserify-des@1.0.2
├─ browserify-rsa@4.1.0
├─ browserify-sign@4.2.1
├─ browserify-zlib@0.2.0
├─ browserslist@4.16.1
├─ buffer-xor@1.0.3
├─ buffer@5.6.0
├─ builtin-status-codes@3.0.0
├─ bytes@3.1.0
├─ chalk@2.4.2
├─ chokidar@3.5.1
├─ classnames@2.2.6
├─ color-convert@1.9.3
├─ color-name@1.1.3
├─ commondir@1.0.1
├─ console-browserify@1.2.0
├─ constants-browserify@1.0.0
├─ convert-source-map@1.7.0
├─ core-util-is@1.0.2
├─ create-ecdh@4.0.4
├─ create-hmac@1.1.7
├─ crypto-browserify@3.12.0
├─ css.escape@1.5.1
├─ cssnano-preset-simple@1.2.2
├─ cssnano-simple@1.2.2
├─ data-uri-to-buffer@3.0.1
├─ debug@2.6.9
├─ depd@1.1.2
├─ des.js@1.0.1
├─ diffie-hellman@5.0.3
├─ domain-browser@1.2.0
├─ electron-to-chromium@1.3.699
├─ emojis-list@2.1.0
├─ escalade@3.1.1
├─ escape-string-regexp@1.0.5
├─ esutils@2.0.3
├─ etag@1.8.1
├─ events@3.3.0
├─ fill-range@7.0.1
├─ find-cache-dir@3.3.1
├─ find-up@4.1.0
├─ fsevents@2.3.2
├─ get-orientation@1.1.2
├─ glob-parent@5.1.2
├─ glob-to-regexp@0.4.1
├─ graceful-fs@4.2.6
├─ hash.js@1.1.7
├─ he@1.2.0
├─ hmac-drbg@1.0.1
├─ http-errors@1.7.3
├─ https-browserify@1.0.0
├─ iconv-lite@0.4.24
├─ is-binary-path@2.1.0
├─ is-extglob@2.1.1
├─ is-glob@4.0.1
├─ is-number@7.0.0
├─ isarray@1.0.0
├─ isobject@2.1.0
├─ jest-worker@24.9.0
├─ js-tokens@4.0.0
├─ json5@1.0.1
├─ line-column@1.0.2
├─ loader-utils@1.2.3
├─ locate-path@5.0.0
├─ lodash.sortby@4.7.0
├─ lodash@4.17.21
├─ loose-envify@1.4.0
├─ make-dir@3.1.0
├─ merge-stream@2.0.0
├─ miller-rabin@4.0.1
├─ minimist@1.2.5
├─ ms@2.0.0
├─ nanoid@3.1.22
├─ native-url@0.3.4
├─ next@10.0.9
├─ node-fetch@2.6.1
├─ node-html-parser@1.4.9
├─ node-libs-browser@2.2.1
├─ node-releases@1.1.71
├─ normalize-path@3.0.0
├─ os-browserify@0.3.0
├─ p-limit@3.1.0
├─ p-locate@4.1.0
├─ p-try@2.2.0
├─ pako@1.0.11
├─ parse-asn1@5.1.6
├─ path-browserify@1.0.1
├─ path-exists@4.0.0
├─ picomatch@2.2.2
├─ pkg-dir@4.2.0
├─ platform@1.3.6
├─ pnp-webpack-plugin@1.6.4
├─ process-nextick-args@2.0.1
├─ process@0.11.10
├─ prop-types@15.7.2
├─ public-encrypt@4.0.3
├─ punycode@1.4.1
├─ querystring-es3@0.2.1
├─ querystring@0.2.1
├─ randomfill@1.0.4
├─ raw-body@2.4.1
├─ react-dom@17.0.2
├─ react-is@16.13.1
├─ react-refresh@0.8.3
├─ react@17.0.2
├─ readable-stream@2.3.7
├─ readdirp@3.5.0
├─ regenerator-runtime@0.13.7
├─ safer-buffer@2.1.2
├─ scheduler@0.20.2
├─ semver@6.3.0
├─ setimmediate@1.0.5
├─ setprototypeof@1.1.1
├─ shell-quote@1.7.2
├─ stacktrace-parser@0.1.10
├─ statuses@1.5.0
├─ stream-browserify@3.0.0
├─ stream-http@2.8.3
├─ stream-parser@0.3.1
├─ string_decoder@1.3.0
├─ string-hash@1.1.3
├─ strip-ansi@6.0.0
├─ styled-jsx@3.3.2
├─ stylis-rule-sheet@0.0.10
├─ stylis@3.5.4
├─ timers-browserify@2.0.12
├─ to-arraybuffer@1.0.1
├─ to-fast-properties@2.0.0
├─ to-regex-range@5.0.1
├─ toidentifier@1.0.0
├─ tr46@1.0.1
├─ ts-pnp@1.2.0
├─ tty-browserify@0.0.0
├─ type-fest@0.7.1
├─ unpipe@1.0.0
├─ url@0.11.0
├─ use-subscription@1.5.1
├─ util-deprecate@1.0.2
├─ util@0.11.1
├─ vm-browserify@1.1.2
├─ watchpack@2.1.1
├─ webidl-conversions@4.0.2
├─ whatwg-url@7.1.0
├─ xtend@4.0.2
└─ yocto-queue@0.1.0
✨  Done in 9.88s.

Initialized a git repository.

Success! Created next-app at /Users/manfredsteiner/Applications/next/next-app
Inside that directory, you can run several commands:

  yarn dev
    Starts the development server.

  yarn build
    Builds the app for production.

  yarn start
    Runs the built app in production mode.

We suggest that you begin by typing:

  cd next-app
  yarn dev`
## run it
### `cd next-app`
`yarn dev`
### yarn run v1.22.10
$ next dev
ready - started server on 0.0.0.0:3000, url: http://localhost:3000
event - compiled successfully
event - build page: /next/dist/pages/_error
wait  - compiling...
event - compiled successfully
event - build page: /
wait  - compiling...
event - compiled successfully`
### ![image.png](../assets/pages_make a markdown blog with next.js_1616625115649_0.png)
### The app will be using gray-matter to parse frontmatter, react-markdown for converting markdown to HTML and displaying based on  next.js
---

## based on tutorial [here](https://jfelix.info/blog/how-to-make-a-static-blog-with-next-js)
## creating a Next.js project
### `yarn create next-app`
### `yarn create v1.22.10
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
success Installed "create-next-app@10.0.9" with binaries:
      - create-next-app
✔ What is your project named? … next-app
Creating a new Next.js app in /Users/manfredsteiner/Applications/next/next-app.

Installing react, react-dom, and next using yarn...

yarn add v1.22.10
info No lockfile found.
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 172 new dependencies.
info Direct dependencies
├─ next@10.0.9
├─ react-dom@17.0.2
└─ react@17.0.2
info All dependencies
├─ @babel/code-frame@7.12.11
├─ @babel/helper-validator-identifier@7.12.11
├─ @babel/highlight@7.13.10
├─ @babel/runtime@7.12.5
├─ @babel/types@7.8.3
├─ @hapi/accept@5.0.1
├─ @hapi/boom@9.1.2
├─ @next/env@10.0.9
├─ @next/polyfill-module@10.0.9
├─ @next/react-dev-overlay@10.0.9
├─ @next/react-refresh-utils@10.0.9
├─ @opentelemetry/api@0.14.0
├─ @opentelemetry/context-base@0.14.0
├─ anser@1.4.9
├─ ansi-regex@5.0.0
├─ ansi-styles@3.2.1
├─ anymatch@3.1.1
├─ asn1.js@5.4.1
├─ assert@1.5.0
├─ ast-types@0.13.2
├─ babel-plugin-syntax-jsx@6.18.0
├─ big.js@5.2.2
├─ binary-extensions@2.2.0
├─ braces@3.0.2
├─ brorand@1.1.0
├─ browserify-aes@1.2.0
├─ browserify-cipher@1.0.1
├─ browserify-des@1.0.2
├─ browserify-rsa@4.1.0
├─ browserify-sign@4.2.1
├─ browserify-zlib@0.2.0
├─ browserslist@4.16.1
├─ buffer-xor@1.0.3
├─ buffer@5.6.0
├─ builtin-status-codes@3.0.0
├─ bytes@3.1.0
├─ chalk@2.4.2
├─ chokidar@3.5.1
├─ classnames@2.2.6
├─ color-convert@1.9.3
├─ color-name@1.1.3
├─ commondir@1.0.1
├─ console-browserify@1.2.0
├─ constants-browserify@1.0.0
├─ convert-source-map@1.7.0
├─ core-util-is@1.0.2
├─ create-ecdh@4.0.4
├─ create-hmac@1.1.7
├─ crypto-browserify@3.12.0
├─ css.escape@1.5.1
├─ cssnano-preset-simple@1.2.2
├─ cssnano-simple@1.2.2
├─ data-uri-to-buffer@3.0.1
├─ debug@2.6.9
├─ depd@1.1.2
├─ des.js@1.0.1
├─ diffie-hellman@5.0.3
├─ domain-browser@1.2.0
├─ electron-to-chromium@1.3.699
├─ emojis-list@2.1.0
├─ escalade@3.1.1
├─ escape-string-regexp@1.0.5
├─ esutils@2.0.3
├─ etag@1.8.1
├─ events@3.3.0
├─ fill-range@7.0.1
├─ find-cache-dir@3.3.1
├─ find-up@4.1.0
├─ fsevents@2.3.2
├─ get-orientation@1.1.2
├─ glob-parent@5.1.2
├─ glob-to-regexp@0.4.1
├─ graceful-fs@4.2.6
├─ hash.js@1.1.7
├─ he@1.2.0
├─ hmac-drbg@1.0.1
├─ http-errors@1.7.3
├─ https-browserify@1.0.0
├─ iconv-lite@0.4.24
├─ is-binary-path@2.1.0
├─ is-extglob@2.1.1
├─ is-glob@4.0.1
├─ is-number@7.0.0
├─ isarray@1.0.0
├─ isobject@2.1.0
├─ jest-worker@24.9.0
├─ js-tokens@4.0.0
├─ json5@1.0.1
├─ line-column@1.0.2
├─ loader-utils@1.2.3
├─ locate-path@5.0.0
├─ lodash.sortby@4.7.0
├─ lodash@4.17.21
├─ loose-envify@1.4.0
├─ make-dir@3.1.0
├─ merge-stream@2.0.0
├─ miller-rabin@4.0.1
├─ minimist@1.2.5
├─ ms@2.0.0
├─ nanoid@3.1.22
├─ native-url@0.3.4
├─ next@10.0.9
├─ node-fetch@2.6.1
├─ node-html-parser@1.4.9
├─ node-libs-browser@2.2.1
├─ node-releases@1.1.71
├─ normalize-path@3.0.0
├─ os-browserify@0.3.0
├─ p-limit@3.1.0
├─ p-locate@4.1.0
├─ p-try@2.2.0
├─ pako@1.0.11
├─ parse-asn1@5.1.6
├─ path-browserify@1.0.1
├─ path-exists@4.0.0
├─ picomatch@2.2.2
├─ pkg-dir@4.2.0
├─ platform@1.3.6
├─ pnp-webpack-plugin@1.6.4
├─ process-n
##### file *styles/tailwind.css*
###### 
```javascript
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";
```
##### file *pages/_app.js*
###### 
```javascript
import "../styles/tailwind.css";
```
#### run it
##### ![image.png](../assets/pages_make a markdown blog with next.js_1616630022845_0.png){:height 150, :width 560}
##### The styling changed!
###

ilwindcss/utilities";
```
```javascript

```
ing react, react-dom, and next using yarn...

yarn add v1.22.10
info No lockfile found.
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 172 new dependencies.
info Direct dependencies
├─ next@10.0.9
├─ react-dom@17.0.2
└─ react@17.0.2
info All dependencies
├─ @babel/code-frame@7.12.11
├─ @babel/helper-validator-identifier@7.12.11
├─ @babel/highlight@7.13.10
├─ @babel/runtime@7.12.5
├─ @babel/types@7.8.3
├─ @hapi/accept@5.0.1
├─ @hapi/boom@9.1.2
├─ @next/env@10.0.9
├─ @next/polyfill-module@10.0.9
├─ @next/react-dev-overlay@10.0.9
├─ @next/react-refresh-utils@10.0.9
├─ @opentelemetry/api@0.14.0
├─ @opentelemetry/context-base@0.14.0
├─ anser@1.4.9
├─ ansi-regex@5.0.0
├─ ansi-styles@3.2.1
├─ anymatch@3.1.1
├─ asn1.js@5.4.1
├─ assert@1.5.0
├─ ast-types@0.13.2
├─ babel-plugin-syntax-jsx@6.18.0
├─ big.js@5.2.2
├─ binary-extensions@2.2.0
├─ braces@3.0.2
├─ brorand@1.1.0
├─ browserify-aes@1.2.0
├─ browserify-cipher@1.0.1
├─ browserify-des@1.0.2
├─ browserify-rsa@4.1.0
├─ browserify-sign@4.2.1
├─ browserify-zlib@0.2.0
├─ browserslist@4.16.1
├─ buffer-xor@1.0.3
├─ buffer@5.6.0
├─ builtin-status-codes@3.0.0
├─ bytes@3.1.0
├─ chalk@2.4.2
├─ chokidar@3.5.1
├─ classnames@2.2.6
├─ color-convert@1.9.3
├─ color-name@1.1.3
├─ commondir@1.0.1
├─ console-browserify@1.2.0
├─ constants-browserify@1.0.0
├─ convert-source-map@1.7.0
├─ core-util-is@1.0.2
├─ create-ecdh@4.0.4
├─ create-hmac@1.1.7
├─ crypto-browserify@3.12.0
├─ css.escape@1.5.1
├─ cssnano-preset-simple@1.2.2
├─ cssnano-simple@1.2.2
├─ data-uri-to-buffer@3.0.1
├─ debug@2.6.9
├─ depd@1.1.2
├─ des.js@1.0.1
├─ diffie-hellman@5.0.3
├─ domain-browser@1.2.0
├─ electron-to-chromium@1.3.699
├─ emojis-list@2.1.0
├─ escalade@3.1.1
├─ escape-string-regexp@1.0.5
├─ esutils@2.0.3
├─ etag@1.8.1
├─ events@3.3.0
├─ fill-range@7.0.1
├─ find-cache-dir@3.3.1
├─ find-up@4.1.0
├─ fsevents@2.3.2
├─ get-orientation@1.1.2
├─ glob-parent@5.1.2
├─ glob-to-regexp@0.4.1
├─ graceful-fs@4.2.6
├─ hash.js@1.1.7
├─ he@1.2.0
├─ hmac-drbg@1.0.1
├─ http-errors@1.7.3
├─ https-browserify@1.0.0
├─ iconv-lite@0.4.24
├─ is-binary-path@2.1.0
├─ is-extglob@2.1.1
├─ is-glob@4.0.1
├─ is-number@7.0.0
├─ isarray@1.0.0
├─ isobject@2.1.0
├─ jest-worker@24.9.0
├─ js-tokens@4.0.0
├─ json5@1.0.1
├─ line-column@1.0.2
├─ loader-utils@1.2.3
├─ locate-path@5.0.0
├─ lodash.sortby@4.7.0
├─ lodash@4.17.21
├─ loose-envify@1.4.0
├─ make-dir@3.1.0
├─ merge-stream@2.0.0
├─ miller-rabin@4.0.1
├─ minimist@1.2.5
├─ ms@2.0.0
├─ nanoid@3.1.22
├─ native-url@0.3.4
├─ next@10.0.9
├─ node-fetch@2.6.1
├─ node-html-parser@1.4.9
├─ node-libs-browser@2.2.1
├─ node-releases@1.1.71
├─ normalize-path@3.0.0
├─ os-browserify@0.3.0
├─ p-limit@3.1.0
├─ p-locate@4.1.0
├─ p-try@2.2.0
├─ pako@1.0.11
├─ parse-asn1@5.1.6
├─ path-browserify@1.0.1
├─ path-exists@4.0.0
├─ picomatch@2.2.2
├─ pkg-dir@4.2.0
├─ platform@1.3.6
├─ pnp-webpack-plugin@1.6.4
├─ process-nextick-args@2.0.1
├─ process@0.11.10
├─ prop-types@15.7.2
├─ public-encrypt@4.0.3
├─ punycode@1.4.1
├─ querystring-es3@0.2.1
├─ querystring@0.2.1
├─ randomfill@1.0.4
├─ raw-body@2.4.1
├─ react-dom@17.0.2
├─ react-is@16.13.1
├─ react-refresh@0.8.3
├─ react@17.0.2
├─ readable-stream@2.3.7
├─ readdirp@3.5.0
├─ regenerator-runtime@0.13.7
├─ safer-buffer@2.1.2
├─ scheduler@0.20.2
├─ semver@6.3.0
├─ setimmediate@1.0.5
├─ setprototypeof@1.1.1
├─ shell-quote@1.7.2
├─ stacktrace-parser@0.1.10
├─ statuses@1.5.0
├─ stream-browserify@3.0.0
├─ stream-http@2.8.3
├─ stream-parser@0.3.1
├─ string_decoder@1.3.0
├─ string-hash@1.1.3
├─ strip-ansi@6.0.0
├─ styled-jsx@3.3.2
├─ stylis-rule-sheet@0.0.10
├─ stylis@3.5.4
├─ timers-browserify@2.0.12
├─ to-arraybuffer@1.0.1
├─ to-fast-properties@2.0.0
├─ to-regex-range@5.0.1
├─ toidentifier@1.0.0
├─ tr46@1.0.1
├─ ts-pnp@1.2.0
├─ tty-browserify@0.0.0
├─ type-fest@0.7.1
├─ unpipe@1.0.0
├─ url@0.11.0
├─ use-subscription@1.5.1
├─ util-deprecate@1.0.2
├─ util@0.11.1
├─ vm-browserify@1.1.2
├─ watchpack@2.1.1
├─ webidl-conversions@4.0.2
├─ whatwg-url@7.1.0
├─ xtend@4.0.2
└─ yocto-queue@0.1.0
✨  Done in 9.88s.

Initialized a git repository.

Success! Created next-app at /Users/manfredsteiner/Applications/next/next-app
Inside that directory, you can run several commands:

  yarn dev
    Starts the development server.

  yarn build
    Builds the app for production.

  yarn start
    Runs the built app in production mode.

We suggest that you begin by typing:

  cd next-app
  yarn dev`
## run it
### `cd next-app`
`yarn dev`
### yarn run v1.22.10
$ next dev
ready - started server on 0.0.0.0:3000, url: http://localhost:3000
event - compiled successfully
event - build page: /next/dist/pages/_error
wait  - compiling...
event - compiled successfully
event - build page: /
wait  - compiling...
event - compiled successfully`
### ![image.png](../assets/pages_make a markdown blog with next.js_1616625115649_0.png)
### The app will be using gray-matter to parse frontmatter, react-markdown for converting markdown to HTML and displaying based on tailwind.css for styling.
#### Add these dependencies
yarn add -D gray-matter tailwindcss postcss-import autoprefixer``
yarn add react-markdown
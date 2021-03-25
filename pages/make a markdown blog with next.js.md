## Create a *next.js* application:
### `yarn create next-app`
###
```shell
yarn create v1.22.10
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
success Saved 174 new dependencies.
info Direct dependencies
├─ next@10.0.9
├─ react-dom@17.0.2
└─ react@17.0.2
info All dependencies
...
✨  Done in 8.74s.

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
  yarn dev

✨  Done in 16.25s.
```
## Run it
### `yarn dev`
### 
```shell
yarn run v1.22.10
$ next dev
ready - started server on 0.0.0.0:3000, url: http://localhost:3000
event - compiled successfully
event - build page: /
wait  - compiling...
event - compiled successfully
```
### ![image.png](../assets/pages_make a markdown blog with next.js_1616684421475_0.png){:height 351, :width 604}
## The application will be based on *gray-matter* to parse frontmatter, *react-markdown* for converting markdown to HTML and tailwindcss to style it.
## Adding these modules
### Adding react-markdown
#### `yarn add react-markdown`
#### 
```shell
yarn add v1.22.10
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning " > react-markdown@5.0.3" has unmet peer dependency "@types/react@>=16".
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 28 new dependencies.
info Direct dependencies
└─ react-markdown@5.0.3
info All dependencies
...
✨  Done in 5.25s.
```
### Adding *gray-matter*
#### `yarn add -D gray-matter`
#### 
```shell
yarn add v1.22.10
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 10 new dependencies.
info Direct dependencies
└─ gray-matter@4.0.2
info All dependencies
...
✨  Done in 3.25s.
```
### Adding *tailwindcss* and co
#### `yarn add -D tailwindcss postcss postcss-import autoprefixer`
####
```shell
yarn add v1.22.10
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 53 new dependencies.
info Direct dependencies
├─ autoprefixer@10.2.5
├─ postcss-import@14.0.0
├─ postcss@8.2.8
└─ tailwindcss@2.0.4
info All dependencies
...
✨  Done in 6.69s.
```
### Configure *tailwindcss*
#### `npx tailwindcss init -p`
#### 
```shell
   tailwindcss 2.0.4
  
   ✅ Created Tailwind config file: tailwind.config.js
   ✅ Created PostCSS config file: postcss.config.js
```
#### create a stylesheet *styles/tailwind.css*
####
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```
#### add the stylesheet to *pages/_app.js* and remove the default sheets
####
```javascript
import @styles/tailwind.css
```
#### create a *jsconfig.json* file for some shortcuts
#### 
```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@components/*": ["components/*"],
      "@utils/*": ["utils/*"],
      "@assets/*": ["assets/*"],
      "@styles/*": ["styles/*"],
      "@config/*": ["config/*"]
    }
  }
}
```
#### ![image.png](../assets/pages_make a markdown blog with next.js_1616686575113_0.png)
### create posts in *content/posts*
#### post
####
```markdown
---
title: First post
description: The first post is the most memorable one.
date: 2020-04-16
---

# h1
## h2
### h3

Normal text
```
### modify default *pages/index.js* to show our posts
###
```javascript
import fs from "fs";
import matter from "gray-matter";

export default function Home({ posts }) {
  return (
    <div>
       {posts.map(({ frontmatter: { title, description, date } }) => (
        <article key={title}>
          <header>
            <h3>{title}</h3>
            <span>{date}</span>
          </header>
          <section>
            <p>{description}</p>
          </section>
        </article>
      ))}
    </div>
  );
}

export async function getStaticProps() {
  const files = fs.readdirSync(`${process.cwd()}/content/posts`);

  const posts = files.map((filename) => {
    const markdownWithMetadata = fs
      .readFileSync(`content/posts/${filename}`)
      .toString();

    const { data } = matter(markdownWithMetadata);

    // Convert post date to format: Month day, Year
    const options = { year: "numeric", month: "long", day: "numeric" };
    const formattedDate = data.date.toLocaleDateString("en-US", options);

    const frontmatter = {
      ...data,
      date: formattedDate,
    };

    return {
      slug: filename.replace(".md", ""),
      frontmatter,
    };
  });

  return {
    props: {
      posts,
    },
  };
}
```
### ![image.png](../assets/pages_make a markdown blog with next.js_1616687186189_0.png)
### adding a Layout component *components/layout.js*
###
```javascript
import Link from "next/link";
import { useRouter } from "next/router";

export default function Layout({ children }) {
  const { pathname } = useRouter();
  const isRoot = pathname === "/";

  const header = isRoot ? (
    <h1 className="mb-8">
      <Link href="/">
        <a className="text-6xl font-black text-black no-underline">
          Next.Js Starter Blog
        </a>
      </Link>
    </h1>
  ) : (
    <h1 className="mb-2">
      <Link href="/">
        <a className="text-2xl font-black text-black no-underline">
          Next.Js Starter Blog
        </a>
      </Link>
    </h1>
  );

  return (
    <div className="max-w-screen-sm px-4 py-8 mx-auto">
      <header>{header}</header>
      <main>{children}</main>
      <footer>
        © {new Date().getFullYear()}, Built with{" "}
        <a href="https://nextjs.org/">Next.js</a> &#128293;
      </footer>
    </div>
  );
}
```
### add the layout to *pages/index.js*
### 
```javascript
//...
import Layout from "@components/layout";
//..
export default function Home({ posts }) {
  return (
    <Layout>
      {posts.map(({ frontmatter: { title, description, date }, slug }) => (
        <article key={slug}>
 //..
        </article>
      ))}
    </Layout>
  );
}

//..
```
### ![image.png](../assets/pages_make a markdown blog with next.js_1616687812886_0.png)
### Styling the blog index
###
```javascript
export default function Home({ posts }) {
  return (
    <Layout>
      {posts.map(({ frontmatter: { title, description, date } }) => (
        <article key={title}>
          <header>
            <h3 className="mb-1 text-3xl font-semibold text-orange-600">
              {title}
            </h3>
            <span className="mb-4 text-sm">{date}</span>
          </header>
          <section>
            <p className="mb-8">{description}</p>
          </section>
        </article>
      ))}
    </Layout>
  );
}
```
### ![image.png](../assets/pages_make a markdown blog with next.js_1616688031298_0.png)
### creating the post page in *pages/post/[slag].js*
###
```javascript
import React from "react";
import fs from "fs";
import path from "path";
import matter from "gray-matter";
import ReactMarkdown from "react-markdown/with-html";
import Layout from "@components/layout";

export default function Post({ content, frontmatter }) {
  return (
    <Layout>
      <article>
        <ReactMarkdown escapeHtml={false} source={content} />
      </article>
    </Layout>
  );
}

export async function getStaticPaths() {
  const files = fs.readdirSync("content/posts");

  const paths = files.map((filename) => ({
    params: {
      slug: filename.replace(".md", ""),
    },
  }));

  return {
    paths,
    fallback: false,
  };
}

export async function getStaticProps({ params: { slug } }) {
   const markdownWithMetadata = fs
    .readFileSync(path.join("content/posts", slug + ".md"))
    .toString();

  const { data, content } = matter(markdownWithMetadata);

  // Convert post date to format: Month day, Year
  const options = { year: "numeric", month: "long", day: "numeric" };
  const formattedDate = data.date.toLocaleDateString("en-US", options);

  const frontmatter = {
    ...data,
    date: formattedDate,
  };

  return {
    props: {
      content: `# ${data.title}\n${content}`,
      frontmatter,
    },
  };
}
```
### modify *pages/index.js* to add links
### 
```javascript
// ...
import Link from "next/link";

export default function Home({ posts }) {
  return (
    <Layout>
      {posts.map(({ frontmatter: { title, description, date }, slug }) => (
        <article key={slug}>
          <header>
            <h3 className="mb-2">
              <Link href={"/post/[slug]"} as={`/post/${slug}`}>
                <a className="text-3xl font-semibold text-orange-600 no-underline">
                  {title}
                </a>
              </Link>
            </h3>
            <span className="mb-4 text-xs">{date}</span>
          </header>
          <section>
            <p className="mb-8">{description}</p>
          </section>
        </article>
      ))}
    </Layout>
  );
}
```
### ![image.png](../assets/pages_make a markdown blog with next.js_1616689357717_0.png){:height 165, :width 604}
### Styling markdown with *Typography.js*
#### `yarn add typography react-typography`
####
```shell
yarn add v1.22.10
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning " > react-markdown@5.0.3" has unmet peer dependency "@types/react@>=16".
warning " > react-typography@0.16.19" has incorrect peer dependency "react@^0.14.0 || ^15.0.0 || ^16.0.0".
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 10 new dependencies.
info Direct dependencies
├─ react-typography@0.16.19
└─ typography@0.16.19
info All dependencies
...
✨  Done in 7.07s.
```
#### Install theme and fonts
#### `yarn add typography-theme-sutro typeface-merriweather typeface-open-sans`
####
```shell
yarn add v1.22.10
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning " > react-markdown@5.0.3" has unmet peer dependency "@types/react@>=16".
warning " > react-typography@0.16.19" has incorrect peer dependency "react@^0.14.0 || ^15.0.0 || ^16.0.0".
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 4 new dependencies.
info Direct dependencies
├─ typeface-merriweather@1.1.13
├─ typeface-open-sans@1.1.13
└─ typography-theme-sutro@0.16.19
info All dependencies
...
✨  Done in 7.08s.

```
#### create a typography configuration in *utils/typography.js*
####
```javascript
import Typography from "typography";
import SutroTheme from "typography-theme-sutro";

delete SutroTheme.googleFonts;

SutroTheme.overrideThemeStyles = ({ rhythm }, options) => ({
  "h1,h2,h3,h4,h5,h6": {
    marginTop: rhythm(1 / 2),
  },
  h1: {
    fontWeight: 900,
    letterSpacing: "-1px",
  },
});
SutroTheme.scaleRatio = 5 / 2;

// Hot reload typography in development.
if (process.env.NODE_ENV !== `production`) {
  typography.injectStyles();
}

export default typography;
```
#### create **pages/_document.js* to inject our typography styles
####
```javascript
import Document, { Head, Main, NextScript } from "next/document";
import { TypographyStyle } from "react-typography";
import typography from "../utils/typography";

export default class MyDocument extends Document {
  render() {
    return (
      <html>
        <Head>
          <TypographyStyle typography={typography} />
        </Head>
        <body>
          <Main />
          <NextScript />
        </body>
      </html>
    );
  }
}
```
#### import the typeface font into *pages/_app.js* by adding this line:
####
```javascript
// ...
import "typeface-lato";
// ...
```
#### Typography.js includes a CSS normalization that collides with tailwind's. Therefore disables tailwind's normalization in *tailwind.config.js**
####
```javascript
corePlugins: {
    preflight: false,
  },
```
####
---
title: make a markdown blog with
### Create a next.js project:
#### `yarn create next-app`
##### ```shell
yarn create v1.22.10
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
success Saved 175 new dependencies.
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
├─ bn.js@4.12.0
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
├─ cipher-base@1.0.4
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
├─ evp_bytestokey@1.0.3
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
✨  Done in 9.44s.

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
  yarn dev
```
### Run it
#### `yarn dev`
#### ```shell
yarn run v1.22.10
$ next dev
ready - started server on 0.0.0.0:3000, url: http://localhost:3000
####
```
#### ![image.png](../assets/pages_make a markdown blog with next.js_1616625115649_0.png)
### It will use *gray-matter* to parse frontmatter, *react-markdown* for converting markdown to HTML and *tailwindcss* to style it.
### Add these dependencies
####
`yarn  add -D gray-matter`
#####
```shell
yarn add v1.22.10
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 10 new dependencies.
info Direct dependencies
└─ gray-matter@4.0.2
info All dependencies
├─ argparse@1.0.10
├─ esprima@4.0.1
├─ extend-shallow@2.0.1
├─ gray-matter@4.0.2
├─ is-extendable@0.1.1
├─ js-yaml@3.14.1
├─ kind-of@6.0.3
├─ section-matter@1.0.0
├─ sprintf-js@1.0.3
└─ strip-bom-string@1.0.0
```
#####
`yarn add -D  tailwindcss postcss postcss-import autoprefixer
######
```shell
yarn add v1.22.10
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 53 new dependencies.
info Direct dependencies
├─ autoprefixer@10.2.5
├─ postcss-import@14.0.0
├─ postcss@8.2.8
└─ tailwindcss@2.0.4
info All dependencies
├─ @fullhuman/postcss-purgecss@3.1.3
├─ acorn-node@1.8.2
├─ acorn-walk@7.2.0
├─ acorn@7.4.1
├─ at-least-node@1.0.0
├─ autoprefixer@10.2.5
├─ balanced-match@1.0.0
├─ brace-expansion@1.1.11
├─ camelcase-css@2.0.1
├─ color-string@1.5.5
├─ color@3.1.3
├─ commander@6.2.1
├─ concat-map@0.0.1
├─ css-unit-converter@1.1.2
├─ cssesc@3.0.0
├─ defined@1.0.0
├─ detective@5.2.0
├─ didyoumean@1.2.1
├─ fraction.js@4.0.13
├─ fs-extra@9.1.0
├─ fs.realpath@1.0.0
├─ function-bind@1.1.1
├─ glob@7.1.6
├─ has@1.0.3
├─ html-tags@3.1.0
├─ indexes-of@1.0.1
├─ inflight@1.0.6
├─ is-arrayish@0.3.2
├─ is-core-module@2.2.0
├─ jsonfile@6.1.0
├─ lodash.toarray@4.4.0
├─ minimatch@3.0.4
├─ modern-normalize@1.0.0
├─ node-emoji@1.10.0
├─ normalize-range@0.1.2
├─ object-hash@2.1.1
├─ path-is-absolute@1.0.1
├─ path-parse@1.0.6
├─ pify@2.3.0
├─ postcss-functions@3.0.0
├─ postcss-import@14.0.0
├─ postcss-js@3.0.3
├─ postcss-nested@5.0.5
├─ postcss-selector-parser@6.0.4
├─ postcss@8.2.8
├─ pretty-hrtime@1.0.3
├─ purgecss@3.1.3
├─ read-cache@1.0.0
├─ reduce-css-calc@2.1.8
├─ resolve@1.20.0
├─ simple-swizzle@0.2.2
├─ tailwindcss@2.0.4
└─ uniq@1.0.1
```##### Initialize Tailwind by generating *tailwind.config.js* and *postcss.config.js* files:###### `npx tailwind init -p`
####### tailwindcss 2.0.4

   ✅ Created Tailwind config file: tailwind.config.js
   ✅ Created PostCSS config file: postcss.config.jst`
##### Configure Tailwind.css: file *postcss.config.js*
###### file *styles/tailwind.css*#######
```javascript
@tailwind base;
@tailwind components;
@tailwind utilities;
```
###### in file *pages/_app.js* add *styles/tailwind.css* and remove default css files:
#######
```javascript
import "../styles/tailwind.css";
```
##### run it
###### ![image.png](../assets/pages_make a markdown blog with next.js_1616630022845_0.png){:height 150, :width 560}
###### The styling changed!
#### Blog logic
##### Blog posts in *content/posts*
###### *first-post.md*
#######
```markdown
---
title: First post
description: The first post is the most memorable one.
date: 2020-04-16
---

# h1
## h2
### h3

Normal text
```
##### index.js with logic to show posts:
######
```javascript
import fs from "fs";
import matter from "gray-matter";

export default function Home({ posts }) {
  return (
    <div>
       {posts.map(({ frontmatter: { title, description, date } }) => (
        <article key={title}>
          <header>
            <h3>{title}</h3>
            <span>{date}</span>
          </header>
          <section>
            <p>{description}</p>
          </section>
        </article>
      ))}
    </div>
  );
}

export async function getStaticProps() {
  const files = fs.readdirSync(`${process.cwd()}/content/posts`);

  const posts = files.map((filename) => {
    const markdownWithMetadata = fs
      .readFileSync(`content/posts/${filename}`)
      .toString();

    const { data } = matter(markdownWithMetadata);

    // Convert post date to format: Month day, Year
    const options = { year: "numeric", month: "long", day: "numeric" };
    const formattedDate = data.date.toLocaleDateString("en-US", options);

    const frontmatter = {
      ...data,
      date: formattedDate,
    };

    return {
      slug: filename.replace(".md", ""),
      frontmatter,
    };
  });

  return {
    props: {
      posts,
    },
  };
}
 ```
#### Styling
##### Layout in *components/layout.js*:
######
```javascript
import Link from "next/link";
import { useRouter } from "next/router";

export default function Layout({ children }) {
  const { pathname } = useRouter();
  const isRoot = pathname === "/";

  const header = isRoot ? (
    <h1 className="mb-8">
      <Link href="/">
        <a className="text-6xl font-black text-black no-underline">
          Next.Js Starter Blog
        </a>
      </Link>
    </h1>
  ) : (
    <h1 className="mb-2">
      <Link href="/">
        <a className="text-2xl font-black text-black no-underline">
          Next.Js Starter Blog
        </a>
      </Link>
    </h1>
  );

  return (
    <div className="max-w-screen-sm px-4 py-8 mx-auto">
      <header>{header}</header>
      <main>{children}</main>
      <footer>
        © {new Date().getFullYear()}, Built with{" "}
        <a href="https://nextjs.org/">Next.js</a> &#128293;
      </footer>
    </div>
  );
}
```
##### add layout to *pages/index.js*
######
```javascript
...
import Layout from "../components/layout";

export default function Home({ posts }) {
  return (
    <Layout>
       {posts.map(({ frontmatter: { title, description, date } }) => (
        <article key={title}>
          ...
        </article>
      ))}
    </Layout>
  );
}
```
###### ![image.png](../assets/pages_make a markdown blog with next.js_1616677784261_0.png)
#### Create the post pages
##### Create the *pages/post/[slug].js* script:
######
```javascript
import React from "react";
import fs from "fs";
import path from "path";
import matter from "gray-matter";
import ReactMarkdown from "react-markdown/with-html";
import Layout from "@components/layout";

export default function Post({ content, frontmatter }) {
  return (
    <Layout>
      <ReactMarkdown escapeHtml={false} source={content} />
    </Layout>
  );
}

export async function getStaticPaths() {
  const files = fs.readdirSync("content/posts");

  const paths = files.map((filename) => ({
    params: {
      slug: filename.replace(".md", ""),
    },
  }));

  return {
    paths,
    fallback: false,
  };
}

export async function getStaticProps({ params: { slug } }) {
   const markdownWithMetadata = fs
    .readFileSync(path.join("content/posts", slug + ".md"))
    .toString();

  const { data, content } = matter(markdownWithMetadata);

  // Convert post date to format: Month day, Year
  const options = { year: "numeric", month: "long", day: "numeric" };
  const formattedDate = data.date.toLocaleDateString("en-US", options);

  const frontmatter = {
    ...data,
    date: formattedDate,
  };

  return {
    props: {
      content: `# ${data.title}\n${content}`,
      frontmatter,
    },
  };
}
```
##### Add the link to *page/index.js* script:
######
```javascript
//...
import Link from "next/link";

export default function Home({ posts }) {
  return (
    <Layout>
      {posts.map(({ frontmatter: { title, description, date }, slug }) => (
        <article key={slug}>
          <header>
            <h3 className="mb-2">
              <Link href={"/post/[slug]"} as={`/post/${slug}`}>
                <a className="text-3xl font-semibold text-orange-600 no-underline">
                  {title}
                </a>
              </Link>
            </h3>
            <span className="mb-4 text-xs">{date}</span>
          </header>
          <section>
            <p className="mb-8">{description}</p>
          </section>
        </article>
      ))}
    </Layout>
  );
}
//...
```

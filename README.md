# `mobile-sections` demo

A pageload demo using the `mobile-sections-*` endpoints of (English) Wikipedia pages.
The Wikipedia language, a page title and revision can be specified in the path of the URL.

_Note It doesn't run any client-side transformations.

## Hosted examples

Navigate to [https://mobile-sections-demo.netlify.com/](https://mobile-sections-demo.netlify.com/). You should see the English Wikipedia Main Page.

Navigate to [https://mobile-sections-demo.netlify.com/en/Cat](https://mobile-sections-demo.netlify.com/en/Cat). You should see the English Wikipedia page Cat.

Navigate to [https://mobile-sections-demo.netlify.com/en/Cat/941307127](https://mobile-sections-demo.netlify.com/en/Cat/941307127). You should see revision 941307127 of the English Wikipedia page Cat.

## Run locally

_Note that you will need to have [Node.js](https://nodejs.org) installed._
This demo app is written in [Svelte](https://svelte.dev/).

Install the dependencies...

```bash
cd mobile-sections-demo
npm install
```

...then start the dev server:

```bash
npm run dev
```

By default, the server will only respond to requests from localhost. To allow connections from other computers, edit the `sirv` commands in package.json to include the option `--host 0.0.0.0`.

## Examples

Navigate to [localhost:5000](http://localhost:5000). You should see the English Wikipedia Main Page.

Navigate to [localhost:5000/en/Cat](http://localhost:5000/en/Cat). You should see the English Wikipedia page Cat.

Navigate to [localhost:5000/en/Cat/941307127](http://localhost:5000/en/Cat/941307127). You should see revision 941307127 of the English Wikipedia page Cat.

## Building and running in production mode

To create an optimized version of the app:

```bash
npm run build
```

You can run the newly built app with `npm run start`. This uses [sirv](https://github.com/lukeed/sirv), which is included in your package.json's `dependencies` so that the app will work when you deploy to platforms like [Heroku](https://heroku.com).

## Deploying to the web

### With [now](https://zeit.co/now)

Install `now` if you haven't already:

```bash
npm install -g now
```

Then, from within your project folder:

```bash
cd public
now deploy --name my-project
```

As an alternative, use the [Now desktop client](https://zeit.co/download) and simply drag the unzipped project folder to the taskbar icon.

### With [surge](https://surge.sh/)

Install `surge` if you haven't already:

```bash
npm install -g surge
```

Then, from within your project folder:

```bash
npm run build
surge public my-project.surge.sh
```

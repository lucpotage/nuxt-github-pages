Here is how to deploy a Nuxt 3 project on GitHub Pages:

# How to

1. Install dev dependency `gh-pages`
2. Add the script `"deploy": "gh-pages -d dist"` in package.json file
3. Specifiy app `baseURL` in nuxt.config.ts
4. Specifiy `buildAssetsDir` in nuxt.config.ts that doesn't start with an underscore `_`. See the router config example below
5. Create an empty file `.nojekyll` at the root of the project
6. Generate with `npm run generate`
7. Deploy with `npm run deploy`

Router config:

```ts
export default defineNuxtConfig({
  app: {
    baseURL: '/nuxt-github-pages/', // baseURL: '/<repository>/'
    buildAssetsDir: 'assets', // don't use "_" at the begining of the folder name to avoids nojkill conflict
  }
}
```

# What it does

The dependency will copy your dist content to a specific `gh-pages` branch that will be served by GitHub Pages. If you go to your Settings/Pages, you’ll see the active branch for your site.

The site is accessible on `https://<username>.github.io/<repository>/`. For this repository, the site is https://lucpotage.github.io/nuxt-github-pages/.

You can rely on GitHub Actions too. More info here: https://medium.com/front-end-weekly/ci-cd-with-github-actions-to-deploy-on-github-pages-73e225f8f131

More information about buildAssetsDir config: https://github.blog/2009-12-29-bypassing-jekyll-on-github-pages/
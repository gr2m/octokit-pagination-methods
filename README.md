# octokit-pagination-methods

> Legacy Octokit pagination methods from v15

Several pagination methods such as `octokit.hasNextPage()` and `octokit.getNextPage()` have been removed from `@octokit/request` in v16.0.0 in favor of `octokit.paginate()`. This plugin brings back the methods to ease the upgrade to v16.

## Usage

```js
const Octokit = require('@octokit/rest')
  .plugin('octokit-pagination-methods')
const octokit = new Octokit()

octokit.issues.getForRepo()

  .then(async response => {
    // returns true/false
    octokit.hasNextPage(response)
    octokit.hasPreviousPage(response)
    octokit.hasFirstPage(response)
    octokit.hasLastPage(response)

    // fetch other pages
    const nextPage = await octokit.getNextPage(response)
    const previousPage = await octokit.getPreviousPage(response)
    const firstPage = await octokit.getFirstPage(response)
    const lastPage = await octokit.getLastPage(response)
  })
```

## Credit

These methods have originally been created for `node-github` by [@mikedeboer](https://github.com/mikedeboer)
while working at Cloud9 IDE, Inc. It was adopted and renamed by GitHub in 2017.

## LICENSE

[MIT](LICENSE)

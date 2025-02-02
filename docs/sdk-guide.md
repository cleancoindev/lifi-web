# Guide for @lifinance/sdk

## Installation

### Step 1
Configure '@lifinance/sdk' for developing

1. Clone [@lifinance/sdk](https://github.com/lifinance/sdk)
2. Open terminal into downloaded `@lifinance/sdk`
3. Run `yarn` for installing dependencies
4. Run `yarn link` (console should appear)
```
➜  lifi-sdk git:(main) yarn link
success Registered "@lifinance/sdk".
info You can now run `yarn link "@lifinance/sdk"` in the projects
where you want to use this package and it will be used instead.
```
### Step 2
Go to your project lifi-web and run command `yarn sdk:link`
<br>
We added script in package.json which run same command `yarn sdk:link`
```
➜  lifi-web git:(main) yarn sdk:link
success Using linked package for "@lifinance/sdk".
```

## Usage
You are able to run watch mode for `@lifinance/sdk`.
1. Open terminal into `@lifinance/sdk`
2. Run command `yarn watch`
```
➜  lifi-sdk git:(main) yarn watch
$ tsc -w -p ./tsconfig.json
Starting compilation in watch mode...

Found 0 errors. Watching for file changes.
```


## Revert @lifinance/sdk
If you would like to use the node_module again, run in lifi-web project `yarn sdk:unlink`
That script is removing link to `@lifinance/sdk` also re-install package
```
➜  lifi-web git:(main) yarn sdk:unlink
$ yarn unlink '@lifinance/sdk' && yarn sdk:update
success Removed linked package "@lifinance/sdk".
```


## Merge request guide when have changes in @lifinance/sdk

1. Develop sdk changes locally, as descibed above
1. Create branch in @lifinance/sdk (e.g. `LF-91-new-step-sdk`)
1. Link the PR in the `package.json` file of the fronend, so the CI can use the updated sdk:
    ```
    "@lifinance/sdk": "github:lifinance/sdk#LF-91-new-step-sdk"
    ```
1. Create merge requests for both sdk and frontend (wait for CI, review)
1. Merging
   1. Release a new version of the sdk package
   1. Set the new version in the `package.json` of the frontend
1. Unlink @lifinance/sdk `yarn sdk:unlink`
1. Test it locally + wait for CI
1. Merge the PR

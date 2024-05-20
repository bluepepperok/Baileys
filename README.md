# Baileys BluePepper's custom version

## Original repository

See [the original repo](https://github.com/WhiskeySockets/Baileys).

## Installation

The module is available on github packages.
[Whatsapp productivity](https://github.com/bluepepperok/whatsapp-productivity) has a dependency on this library. It's `package.json` includes: `"@bluepepperok/baileys": "^specificVersionToUse"`.

## New versions
- If you want to start off a different branch of the original repo, create a new branch with the content of that branch.
- Before making any changes, update the `version` field on [package.json](package.json) to `originalVersion-bp-N-dev` and commit the file to git. N starts with 1 and should be increased for every custom version based off the same original version.  
- See the changes already done by BluePepper on other branches of this project and check whether you need to cherry pick some commits.
- Make the changes you want.
- Use [Example/example.ts](Example/example.ts) to test your changes.
- Make "Whatsapp productivity" use your local version of this library and test the changes.
  - On "Whatsapp productivity" dir run `npx link pathToBaseDirWhereYouCloneGithubRepos/baileys`. 
    - This won't cange its `package.json`
    - It will replace the downloaded release version in `whatsapp-productivity/node_modules/@bluepepperok/baileys/` for a symlink to `pathToBaseDirWhereYouCloneGithubRepos/baileys`.
    - Baileys dependencies were downloaded into `whatsapp-productivity/node_modules` during `npm install`. TODO: if baileys local version changed its dependencies, find a way to test the updated dependencies.
  - Run "Whatsapp productivity" and make sure everything works fine.
  - Run `npm install` to revert `npx link pathToBaseDirWhereYouCloneGithubRepos/baileys`.
- To publish a package version you need your own `.npmrc` (See `.npmrc.example`)
- `yarn publish` and select a version name `originalVersion-bp-N` where N is previous version + 1.
- `git push`
- `git push --tags`
- Make sure the package was published on the packages section of this repo.
- Update "Whatsapp productivity"'s `package.json` to use the new version of this library, run `npm install` and test the changes.


## How to get the .npmrc authToken / YOUR_PERSONAL_ACCESS_TOKEN
- Login to github
- Go to https://github.com/settings/tokens
- Click "generate new token"
- Choose the "classic" token mode
- Set the title and expiration date you want
- On the scope section, check `read:packages`, `write:packages`, `delete:packages` and `repo` 
- Click "generate token".

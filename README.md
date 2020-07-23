# lerna-conventional-commits
Shows an error when using lerna conventional commits to denote breaking changes as part of an investigation into https://github.com/aws/aws-sdk-js-v3/issues/1395.

# Reproduce the error in lerna.
 
```
git checkout not-respecting-breaking-commits
yarn install
yarn conventional-commit
```

## Expectation:  
The generated changelog has two items listed under breaking changes, as shown in [lerna's conventional commit docs] (https://www.conventionalcommits.org/en/v1.0.0/#examples)
 
```
refactor!: drop support for Node 6. This is the second example from [conventional commits v1.0.0](https://www.conventionalcommits.org/en/v1.0.0/#examples) that should also show up as breaking. It does not show up as breaking.
```
 
```
    feat: this is the first example [breaking change](https://www.conventionalcommits.org/en/v1.0.0/#examples) allow provided config object to extend other configs
    
    BREAKING CHANGE: `extends` key in config file is now used for extending other config files
```

## Actual result: 
The generated changelog only has one item listed under breaking changes, #2 from above. I've pasted what the generated changelog looks like after running yarn.



## ----------------- Full generated changelog -----------------
```
# Change Log

All notable changes to this project will be documented in this file.
See [Conventional Commits](https://conventionalcommits.org) for commit guidelines.

# 0.2.0 (2020-07-23)


### Bug Fixes

* inital commit, should not show up as breaking ([6b50c8f](https://github.com/alexforsyth/lerna-conventional-commits/commit/6b50c8f973581031688b4610e22c6f7cb4a79dfe))


### Features

* this is the first example [breaking change](https://www.conventionalcommits.org/en/v1.0.0/#examples) allow provided config object to extend other configs ([2fbc098](https://github.com/alexforsyth/lerna-conventional-commits/commit/2fbc0987eb2d80a6f18f89fb72010499dc1125ac))
* this should show up as non breaking feat ([f428450](https://github.com/alexforsyth/lerna-conventional-commits/commit/f428450f5dd13603999f6ba86a9e098d783410ce))


### BREAKING CHANGES

* `extends` key in config file is now used for extending other config files





# 0.1.0 (2020-07-23)


### Bug Fixes

* inital commit, should not show up as breaking ([6b50c8f](https://github.com/alexforsyth/lerna-conventional-commits/commit/6b50c8f973581031688b4610e22c6f7cb4a79dfe))

```

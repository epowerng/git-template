# Epower Git Template

Git directory template with commit style validator that we are using at Epower.ng.

This style guide is adapted from Angular commit style in combination with our own additions.

## Usage

Git Template is a replacement for the default directory that gets copied each time you create or clone a git repository. That's right, every time you create or clone a git repository, the commit style validator file will get copied in your .git directory.

To use this, first run this command to clone this repo to your home directory:

```sh
 # We assumed you are using Linux or MacOS, if you are using Windows replace the "~" symbol with "%HOMEPATH%"

  git clone https://github.com/epowerng/.git-template ~/.git-template

  # Or if you prefer using SSH protocol

  git clone git@github.com:epowerng/.git-template.git ~/.git-template
```

Set the newly cloned repo as your git template directory. This will tell git to populate new repositories created with either `git clone` or `git init` with the content of this directory.

```sh
  git config --global init.templatedir '~/.git-template'
```

And you are done, read the style guide below to know the rules.

## Regular Expressions

All your commit message must match below Regular Expression to be considered valid.

```js
  /^(revert: )?((build|ci|docs|feat|fix|perf|refactor|style|test|chore|revert)(\(.+\))?: .{1,50}|Initial commit)/
```

Continue reading to get the full explanation.

## Full Message Format

A commit message consists of a **header**, **body** and **footer**.  The header has a **type**, **scope** and **subject**:

```
  <type>(<scope>): <subject>
  <BLANK LINE>
  <body>
  <BLANK LINE>
  <footer>
```

The **header** is mandatory and the **scope** of the header is optional.

## Commit Type

Must be one of the following:

- build: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
- ci: Changes to our CI configuration files and scripts (example scopes: Circle, BrowserStack, SauceLabs)
- docs: Documentation only changes
- feat: A new feature
- fix: A bug fix
- perf: A code change that improves performance
- refactor: A code change that neither fixes a bug nor adds a feature; refactoring production code
- style: Changes that do not affect the meaning of the code (white-space, formatting, removing extra semi-colons, etc)
- test: Adding missing tests or correcting existing tests
- revert: commit that reverts a previous commit
- chore: updating build tasks, package manager configs, etc; no production code change

## Reverting Commit

If the commit reverts a previous commit, it should begin with `revert: `, followed by the header of the reverted commit. In the body it should say: `This reverts commit <hash>.`, where the hash is the SHA of the commit being reverted.

## Commit Scope

The scope could be anything specifying place of the commit change e.g a file name, function name, class name, component name etc.

## Commit Subject

The subject contains succinct description of the change:

- use the imperative, present tense: "change" not "changed" nor "changes"
- don't capitalize first letter
- no dot (.) at the end

## Commit Body

Just as in the **subject**, use the imperative, present tense: "change" not "changed" nor "changes".
The body should include the motivation for the change and contrast this with previous behavior.

## Commit Footer

The footer should contain any information about **Breaking Changes** and is also the place to
reference GitHub issues that this commit **Closes**.

**Breaking Changes** should start with the word `BREAKING CHANGE:` with a space or two newlines. The rest of the commit message is then used for this.

## Commit Examples

Appears under "Features" header, `Post.js` files:

```
  feat(components/Post.js): add 'comments' option
```

Appears under "Bug Fixes" header, `App` subheader, with a link to issue #28:

```
 fix(components/App.js): handle events on blur

 close #28
```

Appears under "Performance Improvements" header, and under "Breaking Changes" with the breaking change explanation:

```
  perf(components/StarRating.js): improve performance by removing the 'finalValue' option

  BREAKING CHANGE: The 'finalValue' option has been removed.
```

The following commit and commit `667ecc1` do not appear in the changelog if they are under the same release. If not, the revert commit appears under the "Reverts" header.

```
  revert: feat(components/Post.js): add 'comments' option

   This reverts commit 667ecc1654a317a13331b17617d973392f415f02.
```

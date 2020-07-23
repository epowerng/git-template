# Epower Git Template

Git directory template which includes commit style validator, preventing commits and pushing directly to master without a pull request that we are using at Epower.ng.

## Usage

Git Template is a replacement for the default directory that gets copied each time you create or clone a git repository.

To use this, first run this command to clone this repo to your home directory:

```sh
  # Windows users should use Git Bash terminal for consistency.

  git clone https://github.com/epowerng/git-template ~/.git-template

  # Or if you prefer using SSH protocol:

  git clone git@github.com:epowerng/git-template.git ~/.git-template
```

Set the newly cloned repo as your git template directory. This will tell git to populate new repositories created with either `git clone` or `git init` with the content of this directory.

```sh
  git config --global init.templatedir '~/.git-template'
```

## Commit Message Format

A commit message consists of a **header**, **body** and **footer**.  The header has a **type**, **scope** and **subject**:

```
  <type>(<scope>): <subject>
  <BLANK LINE>
  <body>
  <BLANK LINE>
  <footer>
```

The **header** is mandatory but the **scope** of the header is optional which means **type** and **subject** are required.

### Commit Type

Must be one of the following:

- `build`: Changes that affect the build system or external dependencies or version changes (example scopes: gulp, broccoli, npm)
- `ci`: Changes to our CI configuration files and scripts (example scopes: Circle, BrowserStack, SauceLabs)
- `docs`: Documentation only changes
- `feat`: A new feature
- `fix`: A bug fix
- `perf`: A code change that improves performance
- `refactor`: A code change that neither fixes a bug nor adds a feature; refactoring production code
- `style`: Changes that do not affect the meaning of the code (white-space, formatting, removing extra semi-colons, etc)
- `test`: Adding missing tests or correcting existing tests
- `chore`: updating build tasks, package manager configs, etc; no production code change
- `revert`: commit that reverts a previous commit, read more [here](#reverting-commit)

### Commit Scope

The scope could be anything specifying place of the commit change e.g a file name, function name, class name, component name etc.

### Commit Subject

The subject contains succinct description of the change:

- use the imperative, present tense: "change" not "changed" nor "changes"
- don't capitalize first letter
- no dot (.) at the end

So the subject should be written as if you are completing the below sentence:

> If this commit were applied, it would...

e.g `add a name field to the checkout form` will now read as `If this commit were applied, it would add a name field to the checkout form`.

Nice and clear!

### Commit Body

Just as in the **subject**, use the imperative, present tense: "change" not "changed" nor "changes".
The body should include the motivation for the change and contrast this with previous behavior.

### Commit Footer

The footer should contain any information about **Breaking Changes** and is also the place to
reference GitHub issues that this commit **Closes**.

**Breaking Changes** should start with the word `BREAKING CHANGE:` with a space or two newlines. The rest of the commit message is then used for this.

### Reverting Commit

If the commit reverts a previous commit, it should begin with `revert: `, followed by the header of the reverted commit. In the body it should say: `This reverts commit <hash>.`, where the hash is the SHA of the commit being reverted.

### Commit Examples

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

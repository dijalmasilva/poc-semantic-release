# Poc Semantic Release

## Steps to reproduce in your project

- Install dev dependencies:

```sh
npm i -D @commitlint/cli @commitlint/config-conventional @semantic-release/changelog @semantic-release/git commitizen cz-conventional-changelog husky semantic-release
```

- Add scripts to commit in `package.json` in root project:

```json
{
  "scripts": {
    "commit": "git-cz",
    "semantic-release": "semantic-release"
  }
}
```

- Create block release or add plugins in your `package.json` or you can be create a new file `.releaserc` in root project directory.

```json
{
  "release": {
    "plugins": [
      "@semantic-release/commit-analyzer",
      "@semantic-release/release-notes-generator",
      "@semantic-release/github",
      "@semantic-release/changelog",
      "@semantic-release/npm",
      [
        "@semantic-release/git",
        {
          "assets": ["CHANGELOG.md", "package.json", "package-lock.json"]
        }
      ]
    ]
  }
}
```

- Configurate if your project is open or private in `package.json`.

```json
{
  "publishConfig": {
    "access": "public"
  }
}
```

- In your CI, you need configure to Environments:

```yml
env:
  GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
  NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
```

- If you are using Actions from Github, you don't need add GITHUB_TOKEN in secrets.

- To get NPM_TOKEN, go to https://www.npmjs.com/settings/yourusername/tokens/ and generete a token. After this, you go to settings in your Github project and add your environment NPM_TOKEN with this token.

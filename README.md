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

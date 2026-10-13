# npm-mirror

Unchanged copies of npm packages that Cocos publishes (`@cocos/*`, and `workflow-extra`), so builds that use them
neither depend on Cocos's npm account nor need a token to install them.

Each copy is one release:

- the tag, and the asset's name without `.tgz`, is `cocos-<name>-<version>` (for example `cocos-ccbuild-2.3.19`)
- the asset is the tarball registry.npmjs.org serves for that version, byte for byte; the release notes give its npm
  URL, npm's integrity, and the file's sha512
- assets are never replaced: a new version is a new release

To check a copy against npm:

```
npm view @cocos/ccbuild@2.3.19 dist.integrity
curl -sL https://github.com/triumphgamedev/npm-mirror/releases/download/cocos-ccbuild-2.3.19/cocos-ccbuild-2.3.19.tgz \
  | openssl dgst -sha512 -binary | base64
```

Each package keeps its own license (its `package.json` and any LICENSE file in the tarball).

# Configurando Commit Semântico

Install husky\
`yarn add husky -D`

## Gitmoji

Install commitlint\
`yarn add @commitlint/cli commitlint-config-gitmoji -D`

Config to use\

```powershell
echo
"module.exports = {
  extends: ['gitmoji'],
  parserPreset: {
    parserOpts: {
      headerPattern: /^(:\w*:)(?:\s)(?:\((.*?)\))?\s((?:.*(?=\())|.*)(?:\(#(\d*)\))?/,
      headerCorrespondence: ['type', 'scope', 'subject', 'ticket']
    }
  }
}"
> commitlint.config.js
```

Instalando Commitizen\
`yarn add commitizen -D`
`commitizen init cz-emoji --yarn --dev --exact`

## Conventional Changelog

Install commitlint\
`yarn add @commitlint/cli @commitlint/config-conventional -D`

Config to use\

```powershell
echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
```

Instalando Commitizen\
`yarn add commitizen -D`
`commitizen init cz-conventional-changelog --yarn --dev --exact`

## Husky config

Add to package.json

```javascript
"scripts":{
	"commit":"git-cz"
}
```

```javascript
"husky": {
	"hooks": {
		"commit-msg": "commitlint -E HUSKY_GIT_PARAMS",
		"prepare-commit-msg": "exec < /dev/tty && git cz --hook || true",
	}
}
```

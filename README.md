# vue-project-specs-template

Vue项目代码规范项目模板
This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) to make the TypeScript language service aware of `.vue` types.

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
pnpm install
```

### Compile and Hot-Reload for Development

```sh
pnpm dev
```

### Type-Check, Compile and Minify for Production

```sh
pnpm build
```

### Lint with [ESLint](https://eslint.org/)

```sh
pnpm lint
```




1. 集成 Eslint
2. 集成 Editorconfig 配置
3. 集成 Commitizen、commitlint 和 @commitlint/cz-commitlint
4. 集成 Eslint Stylistic插件
5. 集成 Husky

## 集成 ESLint
```
  pnpm create @eslint/config
  npm init @eslint/config
```
直接用 `pnpm create vue@latest` 生成
## 集成 Editorconfig 配置
EditorConfig有助于为不同IDE编辑器上处理同一项目的多个开发人员维护一致的编码风格。

```.editorconfig
# EditorConfig is awesome: https://EditorConfig.org

root = true

[*] # 表示所有文件适用
charset = utf-8 # 设置文件字符集为 utf-8
indent_size = 2 # 缩进大小
indent_style = space # 缩进风格(tab | space)
end_of_line = lf # 控制换行类型(lf | cr | crlf)
insert_final_newline = true # 始终在文件末尾插入一个新行
trim_trailing_whitespace = true # 去除行首的任意空白字符

[*.md] # 表示仅 md 文件适用以下规则
insert_final_newline = false # 始终在文件末尾插入一个新行
trim_trailing_whitespace = false # 去除行首的任意空白字符

```
## 集成 Commitizen、commitlint和@commitlint/cz-commitlint
[Commitizen文档](https://commitizen.github.io/cz-cli/)

```
# 添加依赖
npm install --save-dev commitizen
pnpm add commitizen -D

# 初始化commitizen配置
npx commitizen init cz-conventional-changelog --save-dev --save-exact
npx commitizen init cz-conventional-changelog --pnpm --save-dev --save-exact
```
在 `package.json` 中添加 script
```
  ...
  "scripts": {
    "commit": "cz"
  }
```
后期提交用命令 `npm run commit`

### commitlint和@commitlint/cz-commitlint
```
# 安装commitlint
pnpm add -D @commitlint/config-conventional @commitlint/cli

# 配置commitlint， commitlint.config.js
export default { extends: ['@commitlint/config-conventional'] }

# 安装@commitlint/cz-commitlint
pnpm add -D @commitlint/cz-commitlint inquirer@9

# 等后面配置 husky hook，
# 在 .husky/commit-msg 中添加
npx --no -- commitlint --edit
```

## 集成 ESLint Stylistic 插件
[ESLint Stylistic](https://eslint.style/guide/getting-started)

```
npm i -D @stylistic/eslint-plugin
pnpm add -D @stylistic/eslint-plugin
# 如果没有生效或者有报错，需要重启 VS Code
```
## 集成Husky
[Husky](https://typicode.github.io/husky/)
用来执行git钩子:
- pre-commit前执行lint
- commit-msg执行commitlint

```
# 在 .husky/pre-commit 中添加
pnpm run lint

# 在 .husky/commit-msg 中添加
npx --no -- commitlint --edit
``` 

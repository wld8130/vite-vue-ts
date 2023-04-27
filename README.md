# 框架搭建任务

- [x] 基础内容搭建
      > vite + vue3 + pnpm + ts
- [x] 语法校验
  - [x] eslint + prettier
  - [ ] css校验

## 框架搭建步骤

通过pnpm安装，需要安装pnpm，若使用其他包管理，请自行替换命令。

- 打开终端，运行`pnpm create vite`
  > 根据提示输入对应的文件名称，vue,ts
- 进入当前创建好的文件
- 配置eslint
  > 运行`pnpm create @eslint/config`
  > 根据提示选择对应的选项
- 配置prettier
  > 运行`pnpm i prettier eslint-config-prettier eslint-plugin-prettier`
  > 修改 `.eslint.js`文件配置
  > 替换对应的配置
  
      ```
      parser: '@typescript-eslint/parser',
      parserOptions: {
        ecmaVersion: 'latest',
        sourceType: 'module',
        ecmaFeatures: {
          jsx: true,
        },
      },
      ```
  > 添加`.prettierrc.json`文件，配置如下。
  > 当配置文件名为`.prettierrc.js`时，会与`package.json`的`type:module`冲突，需要更换配置文件名

## eslint配置

安装：`pnpm create @eslint/config -D`

```js
module.exports = {
  env: {
    browser: true,
    es2021: true,
    node: true,
  },
  extends: [
    'eslint:recommended',
    'plugin:vue/vue3-essential',
    'plugin:@typescript-eslint/recommended',
    'plugin:prettier/recommended',
  ],
  overrides: [],
  parser: 'vue-eslint-parser',
  parserOptions: {
    parser: '@typescript-eslint/parser',
    ecmaVersion: 'latest',
    sourceType: 'module',
  },
  plugins: ['vue', '@typescript-eslint'],
  rules: {},
};
```

## prettier配置

文件形式建议为`.prettierrc.json`。
配置选项：

```js
module.exports = {
  // 1.一行代码的最大字符数，默认是80(printWidth: <int>)
  printWidth: 120,
  // 2.tab宽度为2空格(tabWidth: <int>)
  tabWidth: 2,
  // 3.是否使用tab来缩进，我们使用空格(useTabs: <bool>)
  useTabs: false,
  // 4.结尾是否添加分号，false的情况下只会在一些导致ASI错误的其工况下在开头加分号，我选择无分号结尾的风格(semi: <bool>)
  semi: true,
  // 5.使用单引号(singleQuote: <bool>)
  singleQuote: true,
  // 6.object对象中key值是否加引号（quoteProps: "<as-needed|consistent|preserve>"）as-needed只有在需求要的情况下加引号，consistent是有一个需要引号就统一加，preserve是保留用户输入的引号
  quoteProps: 'as-needed',
  // 7.在jsx文件中的引号需要单独设置（jsxSingleQuote: <bool>）
  jsxSingleQuote: false,
  // 8.尾部逗号设置，es5是尾部逗号兼容es5，none就是没有尾部逗号，all是指所有可能的情况，需要node8和es2017以上的环境。（trailingComma: "<es5|none|all>"）
  trailingComma: 'es5',
  // 9.object对象里面的key和value值和括号间的空格(bracketSpacing: <bool>)
  bracketSpacing: true,
  // 10.jsx标签多行属性写法时，尖括号是否另起一行(jsxBracketSameLine: <bool>)
  jsxBracketSameLine: false,
  // 11.箭头函数单个参数的情况是否省略括号，默认always是总是带括号（arrowParens: "<always|avoid>"）
  arrowParens: 'avoid',
  // 12.range是format执行的范围，可以选执行一个文件的一部分，默认的设置是整个文件（rangeStart: <int>  rangeEnd: <int>）
  rangeStart: 0,
  rangeEnd: Infinity,
  // 18. vue script和style标签中是否缩进,开启可能会破坏编辑器的代码折叠
  vueIndentScriptAndStyle: false,
  // 19.    endOfLine: "<lf|crlf|cr|auto>" 行尾换行符,默认是lf,
  endOfLine: 'auto',
  // 20.embeddedLanguageFormatting: "off",默认是auto,控制被引号包裹的代码是否进行格式化
  embeddedLanguageFormatting: 'off',
};
```

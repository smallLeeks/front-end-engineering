## react 项目基建

### 当前环境

--os   windows10
--node 14.19.1
--npm  6.14.16

### 需安装以下依赖

- husky
    ```
    npx husky install
    package.json => scripts => `"prepare": "husky install"`
    ```
    - int-staged
    - @commitlint/cli
    ```
    快速创建git hooks的commit-msg钩子: npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
    ```
    - @commitlint/config-conventional

- eslint及相关插件
    - eslint
    - eslint-config-airbnb
    - eslint-plugin-import
    - eslint-plugin-jsx-a11y
    - eslint-plugin-react
    - eslint-plugin-react-hooks

- prettier及相插件
    - prettier
    - eslint-config-prettier
    - eslint-plugin-prettier

### 相关命令配置

    ```
    "lint": "eslint --cache --max-warnings 0 \"src/**/*.{ts,tsx,js,jsx}\" --fix",
    "lint:pretty": "prettier --write \"./**/*.{html,jsx,tsx,ts,js,json,md}\"",
    "lint:staged": "lint-staged -c ./.husky/lintstagedrc.js",
    "prepare": "husky install",
    ```

### 相关配置文件

- .eslintrc.js (eslint 配置)
```
module.exports = {
    env: {
        browser: true,
        es2021: true,
        node: true,
    },
    extends: ['plugin:react/recommended'],
    settings: {
        react: {
            version: 'detect',
        },
    },
    parser: '@babel/eslint-parser',
    parserOptions: {
        ecmaFeatures: {
            jsx: true,
        },
        ecmaVersion: 12,
        sourceType: 'module',
    },
    plugins: ['react'],
    // 这里时配置规则的,自己看情况配置
    rules: {
        semi: ['warn', 'never'], // 禁止尾部使用分号
        'no-console': 0, // 禁止出现console
        'no-debugger': 'warn', // 禁止出现debugger
        'no-duplicate-case': 'warn', // 禁止出现重复case
        'no-empty': 'warn', // 禁止出现空语句块
        'no-extra-parens': 'warn', // 禁止不必要的括号
        'no-func-assign': 'warn', // 禁止对Function声明重新赋值
        'no-unreachable': 'warn', // 禁止出现[return|throw]之后的代码块
        'no-else-return': 'warn', // 禁止if语句中return语句之后有else块
        'no-empty-function': 'warn', // 禁止出现空的函数块
        'no-lone-blocks': 'warn', // 禁用不必要的嵌套块
        'no-multi-spaces': 'warn', // 禁止使用多个空格
        'no-redeclare': 'warn', // 禁止多次声明同一变量
        'no-return-assign': 'warn', // 禁止在return语句中使用赋值语句
        'no-return-await': 'warn', // 禁用不必要的[return/await]
        'no-self-compare': 'warn', // 禁止自身比较表达式
        'no-useless-catch': 'warn', // 禁止不必要的catch子句
        'no-useless-return': 'warn', // 禁止不必要的return语句
        'no-mixed-spaces-and-tabs': 'warn', // 禁止空格和tab的混合缩进
        'no-multiple-empty-lines': 'warn', // 禁止出现多行空行
        'no-trailing-spaces': 'warn', // 禁止一行结束后面不要有空格
        'no-useless-call': 'warn', // 禁止不必要的.call()和.apply()
        'no-var': 'warn', // 禁止出现var用let和const代替
        'no-unused-vars': 0, // 禁止未使用过的变量
        'no-delete-var': 'off', // 允许出现delete变量的使用
        'no-shadow': 'off', // 允许变量声明与外层作用域的变量同名
        'dot-notation': 'warn', // 要求尽可能地使用点号
        'default-case': 'warn', // 要求switch语句中有default分支
        eqeqeq: 'warn', // 要求使用 === 和 !==
        curly: 'warn', // 要求所有控制语句使用一致的括号风格
        'space-before-blocks': 'warn', // 要求在块之前使用一致的空格
        'space-in-parens': 'warn', // 要求在圆括号内使用一致的空格
        'space-infix-ops': 'warn', // 要求操作符周围有空格
        'space-unary-ops': 'warn', // 要求在一元操作符前后使用一致的空格
        'switch-colon-spacing': 'warn', // 要求在switch的冒号左右有空格
        'arrow-spacing': 'warn', // 要求箭头函数的箭头前后使用一致的空格
        'array-bracket-spacing': 'warn', // 要求数组方括号中使用一致的空格
        'brace-style': 'warn', // 要求在代码块中使用一致的大括号风格
        camelcase: 'warn', // 要求使用骆驼拼写法命名约定
        indent: ['warn', 4], // 要求使用JS一致缩进4个空格
        'max-depth': ['warn', 4], // 要求可嵌套的块的最大深度4
        'max-statements': ['warn', 100], // 要求函数块最多允许的的语句数量20
        'max-nested-callbacks': ['warn', 3], // 要求回调函数最大嵌套深度3
        'max-statements-per-line': ['warn', { max: 1 }], // 要求每一行中所允许的最大语句数量
        quotes: ['warn', 'single', 'avoid-escape'], // 要求统一使用单引号符号
        'react/prop-types': 'off',
    },
}
```

- .prettierrc.js (prettier 配置)

```
module.exports = {
    // 箭头函数单个参数不加括号
    arrowParens: 'avoid',
    // 一行最多 100 字符
    printWidth: 100,
    // 使用 4 个空格缩进
    tabWidth: 4,
    // 行尾需要有分号
    semi: false,
    // 使用单引号
    singleQuote: true,
    // 对象的 key 仅在必要时用引号
    quoteProps: 'as-needed',
    // jsx 不使用单引号，而使用双引号
    jsxSingleQuote: false,
    // 末尾不需要逗号
    trailingComma: 'all',
    // 大括号内的首尾需要空格
    bracketSpacing: true,
    // jsx 标签的反尖括号需要换行
    jsxBracketSameLine: false,
    // 每个文件格式化的范围是文件的全部内容
    rangeStart: 0,
    rangeEnd: Infinity,
    // 不需要写文件开头的 @prettier
    requirePragma: false,
    // 不需要自动在文件开头插入 @prettier
    insertPragma: false,
    // 使用默认的折行标准
    proseWrap: 'preserve',
    // 根据显示样式决定 html 要不要折行
    htmlWhitespaceSensitivity: 'css',
    // 换行符使用 lf
    endOfLine: 'auto',
}
```

- .prettierignore
```
#-------------------------------------------------------------------------------------------------------------------
# 保持与 .gitignore 同步
#-------------------------------------------------------------------------------------------------------------------

# Logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Runtime data
*.pid
*.seed
*.pid.lock

# Directory for instrumented libs generated by jscoverage/JSCover
lib-cov

# Coverage directory used by tools like istanbul
coverage

# nyc test coverage
.nyc_output

# Grunt intermediate storage (http://gruntjs.com/creating-plugins#storing-task-files)
.grunt

# Bower dependency directory (https://bower.io/)
bower_components

# node-waf configuration
.lock-wscript

# Compiled binary addons (https://nodejs.org/api/addons.html)
build/Release

# Dependency directories
node_modules/
jspm_packages/

# Optional npm cache directory
.npm

# Optional eslint cache
.eslintcache

# Optional stylint cache
.stylelintcache

# Optional REPL history
.node_repl_history

# Output of 'npm pack'
*.tgz
dist/

# Yarn Integrity file
.yarn-integrity

# dotenv environment variables file
.env

# next.js build output
.next

# OS X temporary files
.DS_Store

# Rush temporary files
common/deploy/
common/temp/
common/autoinstallers/*/.npmrc
**/.rush/temp/

# Heft
.heft

# Common toolchain intermediate files
temp
lib-amd
lib-es6
lib-esnext
lib-commonjs
dist
*.scss.ts
*.sass.ts

# Auto generated files
auto-imports.d.ts*
*.typegen.ts
.cache

#-------------------------------------------------------------------------------------------------------------------
# Prettier 通用配置
#-------------------------------------------------------------------------------------------------------------------

# 包管理文件
pnpm-lock.yaml
yarn.lock
package-lock.json
shrinkwrap.json

# 构建产物
dist
lib
public

# 在 Markdown 中，Prettier 将会对代码块进行格式化，这会影响输出
*.md
```

- commitlint.config.js (commitlint 配置)

```
module.exports = {
    // 忽略部分
    ignores: [commit => commit.includes('init')],
    // 继承的规则
    extends: ['@commitlint/config-conventional'],
    // 定义规则类型
    rules: {
        'body-leading-blank': [2, 'always'],
        'footer-leading-blank': [1, 'always'],
        'header-max-length': [2, 'always', 108],
        'subject-empty': [2, 'never'],
        'type-empty': [2, 'never'],
        // type 类型定义，表示 git 提交的 type 必须在以下类型范围内
        'type-enum': [
            2,
            'always',
            [
                'feat', // 新增feature
                'fix', // 修复bug
                'perf', // 优化相关，比如性能、体验的提升
                'style', // 仅仅修改了空格、格式缩进、逗号等等，不改变代码逻辑;
                'docs', // 	仅仅修改了文档，比如README, CHANGELOG, CONTRIBUTING等等;
                'test', // 测试用例，包括单元测试、集成测试等
                'refactor', // 代码重构，没有加新功能或者修复bug
                'chore', // 改变构建流程、或者增加依赖库、工具等
                'revert', // 回滚到上一个版本
            ],
        ],
    },
}
```

- .husky (git 各个阶段配置)
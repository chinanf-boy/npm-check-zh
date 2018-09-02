# npm-check [![explain]][source] [![translate-svg]][translate-list] [![size-img]][size]

[explain]: http://llever.com/explain.svg
[source]: https://github.com/chinanf-boy/Source-Explain
[translate-svg]: http://llever.com/translate.svg
[translate-list]: https://github.com/chinanf-boy/chinese-translate-list
[size-img]: https://packagephobia.now.sh/badge?p=Name
[size]: https://packagephobia.now.sh/result?p=Name
    
「 查过期的ㄡ不正确的和未使用的依赖项.  」

[中文](./readme.md) | ~~[english](./readme.en.md)~~


---

## 校对 🀄️
<!-- doc-templite START generated -->
<!-- time = '2018 8.6' -->
<!-- repo = 'dylang/npm-check' -->
<!-- commit = '72054dd3b2e100f707405fec3dd0bfae0db504c4' -->
翻译的原文 | 与日期 | 最新更新 | 更多
---|---|---|---
[commit] | ⏰ 2018 8.6 | ![last] | [中文翻译][translate-list]

[last]: https://img.shields.io/github/last-commit/dylang/npm-check.svg
[commit]: https://github.com/dylang/npm-check/tree/72054dd3b2e100f707405fec3dd0bfae0db504c4

<!-- doc-templite END generated -->


### 贡献

欢迎 👏 勘误/校对/更新贡献 😊 [具体贡献请看](https://github.com/chinanf-boy/chinese-translate-list#贡献)

## 生活

[help me live , live need money 💰](https://github.com/chinanf-boy/live-need-money)

---

### 目录

<!-- START doctoc -->
<!-- END doctoc -->


# NPM检查

[![Build Status](https://travis-ci.org/dylang/npm-check.svg?branch=master)](https://travis-ci.org/dylang/npm-check)
[![NPM version](https://badge.fury.io/js/npm-check.svg)](http://badge.fury.io/js/npm-check)
[![Dependency Status](https://img.shields.io/david/dylang/npm-check.svg)](https://david-dm.org/dylang/npm-check)
[![npm](https://img.shields.io/npm/dm/npm-check.svg?maxAge=2592000)](<>)

> 检查过期的ㄡ不正确的和未使用的依赖项. 

<img width="796" alt="npm-check -u" src="https://cloud.githubusercontent.com/assets/51505/9569917/96947fea-4f48-11e5-9783-2d78077256f2.png">

### 特征

-   告诉你什么过时了. 
-   提供到包的文档的链接,这样您就可以决定是否需要更新. 
-   请告知您是否在代码中使用了依赖项. 
-   在您的全球安装包也通过`-g`.
-   **交互更新**少打字,少打字,通过`-u`.
-   支持公私[@范围/包](https://docs.npmjs.com/getting-started/scoped-packages).
-   支持ES6风格[`import from`](http://exploringjs.com/es6/ch_modules.html)语法. 
-   使用NPM的安装版本升级您的模块,包括新版本`npm@3`因此,依赖关系会在你期望的地方进行. 
-   与任何公共NPM注册表一起工作,[有注册中心](https://www.npmjs.com/enterprise)和备用注册表[窦房结](https://github.com/rlidwka/sinopia).
-   不为包查询注册表`private: true`在他们的包裹里. 
-   在命令行应用程序中,因为命令行应用程序也很有趣. 
-   作品与`npm@2`和`npm@3`以及新的替代安装程序`ied`和`pnpm`.

### 要求

-   节点>=0.11. 

### 在命令行上

这是最容易使用的方法. `npm-check`.

### 安装

```bash
$ npm install -g npm-check
```

### 使用

```bash
$ npm-check
```

<img width="882" alt="npm-check" src="https://cloud.githubusercontent.com/assets/51505/9569919/99c2412a-4f48-11e5-8c65-e9b6530ee991.png">

结果应该看起来像屏幕截图,或者当你的包都是最新的和正在使用的东西. 

当需要更新时,它将返回一个可以在CI工具中使用的非零响应代码. 

### 选项

```
Usage
  $ npm-check <path> <options>

Path
  Where to check. Defaults to current directory. Use -g for checking global modules.

Options
  -u, --update          Interactive update.
  -y, --update-all      Uninteractive update. Apply all updates without prompting.
  -g, --global          Look at global modules.
  -s, --skip-unused     Skip check for unused packages.
  -p, --production      Skip devDependencies.
  -d, --dev-only        Look at devDependencies only (skip dependencies).
  -i, --ignore          Ignore dependencies based on succeeding glob.
  -E, --save-exact      Save exact version (x.y.z) instead of caret (^x.y.z) in package.json.
  --specials            List of depcheck specials to include in check for unused dependencies.
  --no-color            Force or disable color output.
  --no-emoji            Remove emoji support. No emoji in default in CI environments.
  --debug               Show debug output. Throw in a gist when creating issues on github.

Examples
  $ npm-check           # See what can be updated, what isn't being used.
  $ npm-check ../foo    # Check another path.
  $ npm-check -gu       # Update globally installed modules by picking which ones to upgrade.
```

![npm-check-u](https://cloud.githubusercontent.com/assets/51505/9569912/8c600cd8-4f48-11e5-8757-9387a7a21316.gif)

#### `-u, --update`

显示交互式UI,用于选择要更新的模块. 

自动更新引用的版本`package.json`.

*根据建议`npm`团队,`npm-check`仅使用更新`npm install`不是`npm update`. 避免使用多个版本`npm`在一个目录中,`npm-check`将使用版本自动安装更新的模块`npm`全球安装. *

<img width="669" alt="npm-check -g -u" src="https://cloud.githubusercontent.com/assets/51505/9569921/9ca3aeb0-4f48-11e5-95ab-6fdb88124007.png">

##### 使用更新[ied](https://github.com/alexanderGugel/ied)或[pnpm](https://github.com/rstacruz/pnpm)

设置环境变量`NPM_CHECK_INSTALLER`您希望使用的安装程序的名称. 

```bash
NPM_CHECK_INSTALLER=pnpm npm-check -u
## pnpm install --save-dev foo@version --color=always
```

你也可以用这种方法进行干运转试验: 

```bash
NPM_CHECK_INSTALLER=echo npm-check -u
```

#### `-y, --update-all`

更新你的依赖关系`--update`只是没有任何提示. 如果您希望自动更新依赖项,则这一点尤其有用. `npm-check`.

#### `-g, --global`

检查您的全局安装包的版本. 

如果值`process.env.NODE_PATH`设置时,它将重写包返回的全局NoDEN1模块的默认路径. [`global-modules`](https://www.npmjs.com/package/global-modules).

*提示: 使用`npm-check -u -g`对全局模块进行安全的交互式更新,包括NPM本身. *

#### `-s, --skip-unused`

默认情况下`npm-check`会让你知道如果你的模块没有被用来查看`require`代码中的语句. 

此选项将跳过该检查. 

当使用时默认为启用. `global`或`update`.

#### `-p, --production`

默认情况下`npm-check`将查看列为`dependencies`和`devDependencies`.

此选项将使其忽略已列出的包的过时和未使用的检查. `devDependencies`.

#### `-d, --dev-only`

忽略`dependencies`并且只检查`devDependencies`.

此选项将使其忽略已列出的包的过时和未使用的检查. `dependencies`.

#### `-i, --ignore`

忽略与指定的GLUB匹配的依赖项. 

`$ npm-check -i babel-*`将忽略从"巴别塔"开始的所有依赖关系. 

#### `-E, --save-exact`

使用软件包安装`--save-exact`意思是确切的版本将保存在PACKAG.JSON中. 

适用于两者`dependencies`和`devDependencies`.

#### `--specials`

在查找未使用的依赖项时,检查特殊文件 (如配置文件) . 

`$ npm-check --specials=bin,webpack`将在`scripts`PACKAG.JSON和WebPACK配置部分. 

见[http://GITHUB.COM/DEPCHECK/DEPCHECK](https://github.com/depcheck/depcheck#special)欲了解更多信息. 

#### `--color, --no-color`

启用或禁用颜色支持. 

默认情况下`npm-check`使用颜色,如果他们是可用的. 

#### `--emoji, --no-emoji`

启用或禁用表情支持. 对于不支持它们的终端是有用的. 在CI服务器中自动禁用. 

#### `--spinner, --no-spinner`

启用或禁用旋转器. 对于不支持它们的终端是有用的. 在CI服务器中自动禁用. 

### 美国石油学会

API是在这里,如果你想用CI工具集包装这个. 

```js
const npmCheck = require('npm-check');

npmCheck(options)
  .then(currentState => console.log(currentState.get('packages')));
```

#### `update`

-   交互式更新. 
-   默认是`false`

#### `global`

-   检查全局模块. 
-   默认是`false`
-   `cwd`使用此选项自动设置. 

#### `skipUnused`

-   跳过检查未使用的包. 
-   默认是`false`

#### `ignoreDev`

-   忽略`devDependencies`.
-   这叫做`--production`在命令行上匹配`npm`.
-   默认是`false`

#### `devOnly`

-   忽略`dependencies`并且只检查`devDependencies`.
-   默认是`false`

#### `ignore`

-   忽略与指定的GLUB匹配的依赖项. 
-   默认是`[]`

#### `saveExact`

-   用精确版本更新包`x.y.z`代替Sever范围`^x.y.z`.
-   默认是`false`

#### `debug`

-   显示调试输出. 在GITHUB上创建问题时要抛砖引玉. 
-   默认是`false`

#### `cwd`

-   覆盖在哪里`npm-check`检查. 
-   默认是`process.cwd()`

#### `specials`

-   名单[`depcheck`](https://github.com/depcheck/depcheck)包括特殊解析器. 
-   默认是`''`

#### `currentState`

承诺的结果是`currentState`对象,查看[JS](lib/state/state.js)看看它是如何工作的. 

你可能想要`currentState.get('packages')`获取包数组和每个包的状态. 

数组中的每个条目看起来如下: 

```js
{
  moduleName: 'lodash',                 // name of the module.
  homepage: 'https://lodash.com/',      // url to the home page.
  regError: undefined,                  // error communicating with the registry
  pkgError: undefined,                  // error reading the package.json
  latest: '4.7.0',                      // latest according to the registry.
  installed: '4.6.1',                   // version installed
  isInstalled: true,                    // Is it installed?
  notInstalled: false,                  // Is it installed?
  packageWanted: '4.7.0',               // Requested version from the package.json.
  packageJson: '^4.6.1',                // Version or range requested in the parent package.json.
  devDependency: false,                 // Is this a devDependency?
  usedInScripts: undefined,             // Array of `scripts` in package.json that use this module.
  mismatch: false,                      // Does the version installed not match the range in package.json?
  semverValid: '4.6.1',                 // Is the installed version valid semver?
  easyUpgrade: true,                    // Will running just `npm install` upgrade the module?
  bump: 'minor',                        // What kind of bump is required to get the latest, such as patch, minor, major.
  unused: false                         // Is this module used in the code?
},
```

如果你使用,你也会看到这个. `--debug`在命令行上. 

### 灵感

-   [NPM过时](https://www.npmjs.com/doc/cli/npm-outdated.html)-笨拙的输出,需要深度=0是可拖动的. 
-   [戴维](https://github.com/alanshaw/david)-不与私人注册机构合作. 
-   [更新通知器](https://github.com/yeoman/update-notifier)-对于单个模块,不是包装中的一切. JSON. 
-   [除错](https://github.com/depcheck/depcheck)-只是谜题的一部分. NPM检查使用DeBECK. 

### 关于作者

你好!谢谢你检查这个项目!我的名字是**迪伦格林尼**. 当我没有被我的两个孩子压垮的时候,我喜欢为开源社区做贡献. 我也是一个技术领先者[欧波威耳](https://opower.com/).[![@dylang](https://img.shields.io/badge/github-dylang-green.svg)](https://github.com/dylang) [![@dylang](https://img.shields.io/badge/twitter-dylang-blue.svg)](https://twitter.com/dylang)

以下是我的其他节点项目: 

| 名字                                                             | 描述                                                                                  | npm 下载                                                                                                                                   |
| -------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| [`grunt‑notify`](https://github.com/dylang/grunt-notify)       | 自动桌面通知的咕噜错误和警告. 支持OS XㄡWindowsㄡLinux.                                               | [![grunt-notify](https://img.shields.io/npm/dm/grunt-notify.svg?style=flat-square)](https://www.npmjs.org/package/grunt-notify)          |
| [`shortid`](https://github.com/dylang/shortid)                 | 非常短的非顺序URL友好的唯一ID生成器.                                                               | [![shortid](https://img.shields.io/npm/dm/shortid.svg?style=flat-square)](https://www.npmjs.org/package/shortid)                         |
| [`space‑hogs`](https://github.com/dylang/space-hogs)           | 从命令行中发现惊人的大目录.                                                                      | [![space-hogs](https://img.shields.io/npm/dm/space-hogs.svg?style=flat-square)](https://www.npmjs.org/package/space-hogs)                |
| [`rss`](https://github.com/dylang/node-rss)                    | RSS馈源发生器. 向任何项目添加RSS提要. 支持外壳和GOSSSS.                                                | [![rss](https://img.shields.io/npm/dm/rss.svg?style=flat-square)](https://www.npmjs.org/package/rss)                                     |
| [`grunt‑prompt`](https://github.com/dylang/grunt-prompt)       | 使用控制台复选框ㄡ带有过滤的文本输入ㄡ密码字段来为您的Grutter配置提供交互式提示.                                        | [![grunt-prompt](https://img.shields.io/npm/dm/grunt-prompt.svg?style=flat-square)](https://www.npmjs.org/package/grunt-prompt)          |
| [`xml`](https://github.com/dylang/node-xml)                    | 快速简单的XML生成器. 支持属性ㄡCDATA等包括测试和示例.                                                    | [![xml](https://img.shields.io/npm/dm/xml.svg?style=flat-square)](https://www.npmjs.org/package/xml)                                     |
| [`changelog`](https://github.com/dylang/changelog)             | 命令行工具 (和Node模块) ,用于为npmjs.org注册表中的模块以及任何公共github.com repo中的模块生成颜色输出ㄡ标记或json中的更改日志.  | [![changelog](https://img.shields.io/npm/dm/changelog.svg?style=flat-square)](https://www.npmjs.org/package/changelog)                   |
| [`grunt‑attention`](https://github.com/dylang/grunt-attention) | 显示终端中的注意力捕获消息                                                                       | [![grunt-attention](https://img.shields.io/npm/dm/grunt-attention.svg?style=flat-square)](https://www.npmjs.org/package/grunt-attention) |
| [`observatory`](https://github.com/dylang/observatory)         | 漂亮的UI,用于显示命令行上运行的任务.                                                                | [![observatory](https://img.shields.io/npm/dm/observatory.svg?style=flat-square)](https://www.npmjs.org/package/observatory)             |
| [`anthology`](https://github.com/dylang/anthology)             | 任何@ NPMJS用户的模块信息和统计信息                                                               | [![anthology](https://img.shields.io/npm/dm/anthology.svg?style=flat-square)](https://www.npmjs.org/package/anthology)                   |
| [`grunt‑cat`](https://github.com/dylang/grunt-cat)             | 将文件回传给终端. 作品与文本,小品,ASCII艺术,全彩ANSI.                                                  | [![grunt-cat](https://img.shields.io/npm/dm/grunt-cat.svg?style=flat-square)](https://www.npmjs.org/package/grunt-cat)                   |

*使用此列表生成[选本](https://github.com/dylang/anthology).*

### 许可证

版权所有 (C) 2016 Dylan Greene,撰稿人. 

发布下[MIT许可](https://tldrlegal.com/license/mit-license).

截屏是[西比萨](https://creativecommons.org/licenses/by-sa/4.0/) (归属共享) . 

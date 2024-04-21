---
title: npm入门
date: 2024-04-21 15:09:27
tags: front end
cover: https://pic1.zhimg.com/v2-5f85caa925c4bea110c361588f452b8e_720w.jpg?source=172ae18b
top_img: https://pic1.zhimg.com/v2-5f85caa925c4bea110c361588f452b8e_720w.jpg?source=172ae18b
---
npm，全名 node package manger。

* npm 是 `Node`的开放式模块登记和管理系统，是 `Node.js`包的标准发布平台，用于 `Node.js`包的发布、传播、依赖控制，网址：[www.npmjs.com/](https://link.juejin.cn?target=https%3A%2F%2Fwww.npmjs.com%2F "https://www.npmjs.com/")
* npm 提供了命令行工具，可以方便地下载、安装、升级、删除包，也可以让你作为开发者发布并维护包

## npm 如何使用

* npm 在按照 Node.js 时会连带被安装。但有可能不是最新版本，需要 `npm install npm@latest -g` 升级到最新版本。

基本命令：

```shell
查看 npm 命令列表
npm help
查看各个命令的简单用法
npm -l
查看 npm 的版本
npm -v
查看 npm 的配置
npm config list -l
```

## npm 的使用

用来初始化生成 `package.json`文件。在这个过程中会向用户提问一系列问题，如果你觉得不用修改默认配置，一路回车就可以了。

如果使用了 `-f`（代表 `force`）、 `-y`（代表 `yes`），则跳过提问阶段，直接生成一个新的 `package.json`文件。

## npm set 设置环境变量

```csharp
  $ npm set init-author-name 'Your name'
  $ npm set init-author-email 'Your email'
  $ npm set init-author-url 'http://yourdomain.com'
  $ npm set init-license 'MIT'
```

上面命令等于为 `npm init`设置了默认值，以后执行 `npm init`的时候， `package.json`的作者姓名、邮件、主页、许可证字段就会自动写入预设的值。这些信息会存放在用户主目录的 `~/.npmrc`文件，使得用户不用每个项目都输入。如果某个项目有不同的设置，可以针对该项目运行 `npm config`。

```shell
npm set save-exact true
```

上面命令设置加入模块时， `package.json`将记录模块的确切版本，而不是一个可选的版本范围。

## npm config

```shell
npm config set prefix $dir
```

上面的命令将指定的 `$dir`目录，设为模块的全局安装目录。如果当前有这个目录的写权限，那么运行 `npm install`的时候，就不再需要 `sudo`命令授权了。

```arduino
$ npm config set save-prefix ~
```

上面的命令使得 `npm install --save`和 `npm install --save-dev`安装新模块时，允许的版本范围从克拉符号（^）改成波浪号（~），即从允许小版本升级，变成只允许补丁包的升级。

```shell
npm config set init.author.name $name
npm config set init.author.email $email
```

上面命令指定使用 `npm init`时，生成的 `package.json`文件的字段默认值。

## npm info

`npm info`命令可以查看每个模块的具体信息

```ruby
$ npm info underscore
$ npm info underscore description
$ npm info underscore homepage
$ npm info underscore version
```

## npm search

`npm search`命令用于搜索npm仓库，它后面可以跟字符串，也可以跟正则表达式

```ruby
  $ npm search
```

## npm list

`npm list`命令以树型结构列出当前项目安装的所有模块，以及它们依赖的模块。

```csharp
npm list
npm list -global
npm list vue
```

加上global参数，会列出全局安装的模块。

## npm install

`Node`模块采用 `npm install`命令安装。

每个模块可以"全局安装"，也可以"本地安装"。"全局安装"指的是将一个模块安装到系统目录中，各个项目都可以调用。一般来说，全局安装只适用于工具模块，比如 `eslint`和 `gulp`。"本地安装"指的是将一个模块下载到当前项目的 `node_modules`子目录，然后只有在项目目录之中，才能调用这个模块

```shell
本地安装
npm install
全局安装
sudo npm install -global
sudo npm install -g
也支持直接输入Github代码库地址
npm install git://github.com/package/path.git
npm install git://github.com/package/path.git
强制重新安装
npm install  --force
如果你希望，所有模块都要强制重新安装，那就删除node_modules目录，重新执行npm install
rm -rf node_modules
npm install
```

## 安装不同版本

install 命令总是安装模块的最新版本，如果要安装模块的特定版本，可以在模块名后面加上@和版本号。

```ruby
$ npm install sax@latest
$ npm install sax@0.1.1
$ npm install sax@">=0.1.0

$ npm install readable-stream --save --save-exact

$ npm install sax --save
$ npm install node-tap --save-dev

$ npm install sax -S
$ npm install node-tap -D

$ npm install <module-name>@beta (latest beta)

$ npm install <module-name>@1.3.1-beta.3

$ npm install --production

$ NODE_ENV=production npm install
```

## 避免系统权限

默认情况下， `Npm`全局模块都安装在系统目录（比如 `/usr/local/lib/`），普通用户没有写入权限，需要用到 `sudo`命令。这不是很方便，我们可以在没有 `root`权限的情况下，安装全局模块。

首先，在主目录下新建配置文件 `.npmrc`，然后在该文件中将 `prefix`变量定义到主目录下面。

```bash
  prefix = /home/yourUsername/npm
```

然后在主目录下新建 `npm`子目录

```shell
mkdir ~/npm
```

此后，全局安装的模块都会安装在这个子目录中， `npm`也会到 `~/npm/bin`目录去寻找命令。

最后，将这个路径在 `.bash_profile`文件（或 `.bashrc`文件）中加入 `PATH`变量。

```bash
export PATH=~/npm/bin:$PATH
```

## npm update

npm update命令可以更新本地安装的模块

```ini

$ npm update [package name]

$ npm update -global [package name]
```

它会先到远程仓库查询最新版本，然后查询本地版本。如果本地版本不存在，或者远程版本较新，就会安装。

使用 `-S`或 `--save`参数，可以在安装的时候更新 `package.json`里面模块的版本号。

注意，从 `npm v2.6.1`开始，npm update只更新顶层模块，而不更新依赖的依赖，以前版本是递归更新的。如果想取到老版本的效果，要使用下面的命令。

```css
$ npm --depth 9999 update
```

## npm uninstall

npm uninstall命令，卸载已安装的模块

```ini
$ npm uninstall [package name]

$ npm uninstall [package name] -global
```

## npm run

npm 不仅可以用于模块管理，还可以用于执行脚本。package.json 文件有一个 scripts 字段，可以用于指定脚本命令，供npm直接调用。

npm run 命令会自动在环境变量 $PATH 添加 node_modules/.bin 目录，所以 scripts 字段里面调用命令时不用加上路径，这就避免了全局安装 NPM 模块。

npm run 如果不加任何参数，直接运行，会列出 package.json 里面所有可以执行的脚本命令。

npm内置了两个命令简写，npm test 等同于执行 npm run test，npm start 等同于执行 npm run start。

```css
$ npm i eslint --save-dev
```

## pre- 和 post- 脚本

npm run 为每条命令提供了 pre- 和 post- 两个钩子（hook）。以 npm run lint 为例，执行这条命令之前，npm会先查看有没有定义 prelint 和 postlint 两个钩子，如果有的话，就会先执行 npm run prelint，然后执行 npm run lint，最后执行npm run postlint。

## 全局模块(在命令行的任何地方可以使用) 局部模块

* 为什么全局模块可以直接在任何地方使用

## 全局的模块

* 必须使用package.json 中配置bin参数
* #! /usr/bin/env node

## npm link

就是将当前的目录临时的放到全局下。

开发 NPM 模块的时候，有时我们会希望，边开发边试用，比如本地调试的时候，require('myModule') 会自动加载本机开发中的模块。Node规定，使用一个模块时，需要将其安装到全局的或项目的 node_modules 目录之中。对于开发中的模块，解决方法就是在全局的 node_modules 目录之中，生成一个符号链接，指向模块的本地目录。

npm link 就能起到这个作用，会自动建立这个符号链接。

请设想这样一个场景，你开发了一个模块 myModule，目录为 src/myModule，你自己的项目 myProject 要用到这个模块，项目目录为 src/myProject。首先，在模块目录（src/myModule）下运行 npm link 命令。

```bash
src/myModule$ npm link
```

上面的命令会在NPM的全局模块目录内，生成一个符号链接文件，该文件的名字就是 package.json 文件中指定的模块名。

```bash
/path/to/global/node_modules/myModule -> src/myModule
```

这个时候，已经可以全局调用 myModule 模块了。但是，如果我们要让这个模块安装在项目内，还要进行下面的步骤。

切换到项目目录，再次运行 npm link 命令，并指定模块名。

```bash
src/myProject$ npm link myModule
```

上面命令等同于生成了本地模块的符号链接。

```bash
src/myProject/node_modules/myModule -> /path/to/global/node_modules/myModule
```

然后，就可以在你的项目中，加载该模块了。

```ini
var myModule = require('myModule')
```

这样一来，myModule 的任何变化，都可以直接反映在 myProject 项目之中。但是，这样也出现了风险，任何在myProject目录中对myModule的修改，都会反映到模块的源码中。

如果你的项目不再需要该模块，可以在项目目录内使用 npm unlink 命令，删除符号链接。

```bash
src/myProject$ npm unlink myModule
```

## npm bin

```python

$ npm bin
./node_modules/.bin
```

## npm adduser

```makefile
$ npm adduser
Username: YOUR_USER_NAME
Password: YOUR_PASSWORD
Email: YOUR_EMAIL@domain.com
```

## npm publish

npm publish用于将当前模块发布到npmjs.com。执行之前，需要向npmjs.com申请用户名。

```ruby

$ npm adduser

$ npm login

$ npm publish

$ npm publish --tag beta

$ npm init --scope=

$ npm install --save-dev babel-cli@6 babel-preset-es2015@6
```

然后，在package.json里面写入build脚本。

```json
"scripts": {
  "build": "babel source --presets babel-preset-es2015 --out-dir distribution",
  "prepublish": "npm run build"
}
```

运行上面的脚本，会将 source 目录里面的ES6源码文件，转为 distribution 目录里面的 ES5 源码文件。然后，在项目根目录下面创建两个文件 .npmignore 和 .gitignore，分别写入以下内容。

```arduino

source

node_modules
distribution
```

## npm deprecate

如果想废弃某个版本的模块，可以使用 npm deprecate 命令。

```kotlin
$ npm deprecate my-thing@"< 0.2.3" "critical bug fixed in v0.2.3"
```

## github / npm

## npm版本号管理的问题

* semver规范 规定了版本号 由3位组成 MAJOR MINOR PATCH
  - MAJOR 可能不在兼容老版本
  - MINOR 新增了一些兼容旧版本的api vue.observable
  - PATCH 修复bug

> 都是git的tag 对应着npm的版本

```bash
npm version major minor patch
```

> 会自动和git进行关联

## 版本号含义

* 2.2.0 必须是2.2.0
* ^2.2.0 限定大版本，后面更新只要不超过2尽可以
* ~2.2.0 限定前两个版本，后面的版本只要比0大就可以
*
> =2.0 大于这个版本

预发版本

* alpha 预览版 内部测试版
* beta 测试版 公开测试版
* rc 最终测试版本

## scripts

* 可以配置脚本的命令 快捷键(可以把很长的命令放到scripts中)
* 执行命令 会将当前的node_modules目录下的.bin文件夹放到全局中(所以可以直接使用)
* npm run start 可以简写成 npm start

## npx

* npx和script一致可以帮我们直接运行 .bin目录下的内容
* 如果.bin目录下存在 会执行对应脚本，如果不存在会下载运行

> npx 只是一个临时的使用方案。 npm5.2 之后产生的

## 源的切换 (npm nrm nvm)

* npm install nrm -g
* nrm ls / nrm use

## 包的发布

* 如何发布一个包 先注册npm账号
* 一定要在官方源上发
* npm addUser 添加用户
* npm publish 发布包

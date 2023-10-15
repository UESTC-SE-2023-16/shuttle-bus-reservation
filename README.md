<div align="center">

~假装有图片~

# Shuttle-Bus-Reservation

又一个班车预约系统课设

</div>

## 开发环境搭建步骤

使用了以下工具进行管理：

- poetry：管理Python虚拟环境
- pre-commit：管理代码格式规范和commit信息规范
- nonemoji：为commit提供有概括性的emoji

### 配置开发环境

#### 什么是Poetry？

[Poetry](https://python-poetry.org/) 是一个 Python 虚拟环境和依赖管理工具。

#### 安装Poetry

如果你是 Linux / MacOS / WSL用户, 执行以下命令:

```sh
curl -sSL https://install.python-poetry.org | python3 -
```

如果你是 Windows 用户，请使用 **Powershell** 执行以下命令

```powershell
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
```

> [!NOTE]
> 如果报错无法找到`py`命令，请尝试将`py`替换为`python`
> 参见 [Poetry-Installation](https://python-poetry.org/docs/#installation)

安装结束后，命令行中输入(Powershell请打开一个新的窗口)命令: `poetry --version`，如果出现类似以下内容，则为安装成功：

```powershell
$ poetry --version

Poetry (version 1.3.2)
```

#### 配置Poetry

打开系统的命令行界面(Powershell / sh / bash或者其他)，输入命令：

```sh
poetry config virtualenvs.in-project true
```

该命令会让poetry在本项目所在目录下创建虚拟环境，而非其他奇怪的地方  
输入命令 `poetry config --list` 进行验证，应观察到存在输出:

```toml
...
virtualenvs.in-project = true
...
```

证明配置成功

### pre-commit 配置

> [!IMPORTANT]
> 如无特殊说明，本节内容均应在poetry的虚拟环境中进行，并且鉴于一些原因，安装过程可能需要一些魔法。

#### 什么是pre-commit?

[pre-commit](https://pre-commit.com/#introduction)是Git自带有的hook，它可以在我们commit之前先对提交的内容进行遍历、检测亦或是其他操作。它可以确保提交到仓库内的代码风格一致。

#### 安装pre-commit

正常情况下，pre-commit会在之前的`poetry install`命令中被安装，如果执行命令`pre-commit --version`显示未找到该命令，可以使用`pip install pre-commit`命令进行安装。

#### 配置pre-commit

安装pre-commit无误后，执行命令`pre-commit install`，将会安装一系列预先设置好的git hook，用以规范仓库代码和提交信息风格。  
接下来，只要你进行`git commit`相关的命令，pre-commit都将会自动运行，对你修改过的代码进行规范。

### VS Code 配置

如果你使用VsCode进行项目的开发，建议安装以下插件：

- EditorConfig for VS Code
- Pylance
- Python

并启用 Pylance 的类型检查为 `basic`

(设置 > 扩展 > Pylance > "python.analysis.typeCheckingMode": "basic")

## commit注意事项

项目使用了 [nonemoji](https://github.com/nonebot/nonemoji) 对commit信息进行规范

### nonemoji 介绍以及使用

nonemoji 可以认为是 [gitmoji](https://gitmoji.dev/) 的简化版。

gitmoji是一个标准化和解释在GitHub提交消息上使用emoji的倡议。 gitmoji 是一个开源项目，专门规定了在 github 提交代码时应当遵循的 emoji 规范

在git commit上使用emoji提供了一种简单的方法，仅通过查看所使用的表情符号来确定提交的目的或意图。

对于commit，在git commit时，应该所写的commit msg前附带一个emoji(前后使用`:`包裹起来的emoji名称，例如`:fire: ->`:fire:)，用来概括本次提交的意图，例如:

```commit
git commit -m ":bug: 修复了xxx错误"

// 这样commit之后的信息就会显示

🐛 修复了xxx错误

```

从而使得commit msg更容易理解

也可以直接在命令行里输入`nonemoji`命令，选择一个合适的nonemoji后填写commit msg并提交

所有可用的nonemoji参见下面的链接，或者使用`nonemoji list`命令查看

### 为什么要使用 nonemoji？

在执行 git commit 指令时使用 emoji 图标为本次提交添加一个特别的图标， 这个本次提交的记录很容易突出重点，或者说光看图标就知道本次提交的目的。这样就方便在日后查看历史提交日子记录中快速的查找到对于的提交版本。

## 怎么使用 nonemoji？

> [!IMPORTANT]
> 使用一下命令时请确保已经处于本项目的虚拟环境之中

### 快速提交

使用命令`nonemoji commit`可以快速选择一个emoji并填写commit msg进行commit

> 参考教程：[Git Commit emoji Guide 提交表情使用指北](https://hooj0.github.io/git-emoji-guide/)

## nonemoji 表情库

| emoji 表情                               | emoji 代码                    | commit 说明               |
| :--------------------------------------- | :---------------------------- | :------------------------ |
| :sparkles: (火花)                        | `:sparkles:`                  | 引入新功能                |
| :bug: (bug)                              | `:bug:`                       | 修复 bug                  |
| :memo: (备忘录)                          | `:memo:`                      | 添加或者更新文档          |
| :page_facing_up: (文档)                  | `:page_facing_up:`            | 添加或更新许可证。        |
| :art: (调色板)                           | `:art:`                       | 改进代码结构/代码格式     |
| :recycle: (循环箭头)                     | `:recycle:`                   | 重构代码                  |
| :white_check_mark: (白色复选框)          | `:white_check_mark:`          | 增加或者更新测试          |
| :rocket: (火箭)                          | `:rocket:`                    | 部署功能                  |
| :lipstick: (口红)                        | `:lipstick:`                  | 更新 UI 和样式文件        |
| :bookmark: (书签)                        | `:bookmark:`                  | 发行/版本标签             |
| :label: (标签)                           | `:label:`                     | 增加或者更新类型          |
| :rotating_light: (警车灯)                | `:rotating_light:`            | 移除 compiler/linter 警告 |
| :heavy_plus_sign: (加号)                 | `:heavy_plus_sign:`           | 添加一个依赖              |
| :heavy_minus_sign: (减号)                | `:heavy_minus_sign:`          | 移除一个依赖              |
| :arrow_down: (下降箭头)                  | `:arrow_down:`                | 降级依赖                  |
| :arrow_up: (上升箭头)                    | `:arrow_up:`                  | 升级依赖                  |
| :pushpin: (图钉)                         | `:pushpin:`                   | 将依赖关系固定到特定版本  |
| :green_heart: (绿心)                     | `:green_heart:`               | 修复 CI 构建问题          |
| :construction_worker: (工人)             | `:construction_worker:`       | 添加 CI 构建系统          |
| :chart_with_upwards_trend: (上升趋势图)  | `:chart_with_upwards_trend:`  | 添加分析或跟踪代码        |
| :wrench: (扳手)                          | `:wrench:`                    | 修改配置文件              |
| :hammer: (锤子)                          | `:hammer:`                    | 添加或者更新开发脚本      |
| :globe_with_meridians: (地球)            | `:globe_with_meridians:`      | 国际化与本地化            |
| :pencil2: (铅笔)                         | `:pencil2:`                   | 修复 typo                 |
| :tada: (庆祝)                            | `:tada:`                      | 开始项目                  |
| :construction: (施工)                    | `:construction:`              | 工作进行中                |
| :rewind: (双左箭头)                      | `:rewind:`                    | 恢复更改                  |
| :twisted_rightwards_arrows: (双合并箭头) | `:twisted_rightwards_arrows:` | 合并分支                  |
| :package: (箱子)                         | `:package:`                   | 更新编译的文件或包        |
| :alien: (面具)                           | `:alien:`                     | 由于外部API更改而更新代码 |
| :truck: (面包车)                         | `:truck:`                     | 移动或重命名文件          |
| :boom: (爆炸)                            | `:boom:`                      | 介绍突破性变化            |
| :wheelchair: (轮椅)                      | `:wheelchair:`                | 提高可访问性              |
| :bulb: (灯泡)                            | `:bulb:`                      | 更新源代码注释            |
| :beers: (干杯)                           | `:beers:`                     | 醉生梦死的写代码          |
| :loud_sound: (有声喇叭)                  | `:loud_sound:`                | 添加日志                  |
| :mute: (静音喇叭)                        | `:mute:`                      | 删除日志                  |
| :children_crossing: (小盆友)             | `:children_crossing:`         | 改善用户体验/可用性       |
| :building_construction: (建筑施工)       | `:building_construction:`     | 进行架构改变              |
| :see_no_evil: (蒙眼猴子)                 | `:see_no_evil:`               | 添加或更新.gitignore文件  |
| :triangular_flag_on_post: (旗子)         | `:triangular_flag_on_post:`   | 更改特性flags             |
| :goal_net: (球门)                        | `:goal_net:`                  | 捕获异常                  |
| :wastebasket: (垃圾桶)                   | `:wastebasket:`               | 清理需要弃用的代码        |
| :coffin: (棺材)                          | `:coffin:`                    | 清理从未使用的死代码      |
| :technologist: (码农)                    | `:technologist:`              | 提高开发者体验            |
| :zap: (闪电)                             | `:zap:`                       | 提升性能                  |
| :fire: (火焰)                            | `:fire:`                      | 移除代码或文件            |
| :bento: (便当)                           | `:bento:`                     | 更改asset                 |

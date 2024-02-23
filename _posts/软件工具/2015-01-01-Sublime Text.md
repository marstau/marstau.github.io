---
layout: post
title: Sublime Text
category: 软件工具
tags: software
keywords: Sublime
description: 
---

#### 快捷键[More](http://www.ithome.com/html/soft/31560.htm)

搜索函数 : ⌘ + R

批量缩进和反缩进:(shift +) tab

跳转到某一行=> ctrl + G

搜索打开项目中的文件: ctrl + P

粘贴并格式化: ctrl + shift + V

打开文件所在目录: ctrl + O

同文件内设置标签 : cmd + F2

前一视图: ctrl + tab

一直按住选中光标框选当前变量名: ctrl + d

批量选中变量到变量尾部： shift + end

选中文字全小/大写： ctrl + K + L/U

前/下一个文件: ctrl + PageUp/PageDown

#### 正则

替换数字

```
\d
```

任意非数字

```
(.[^0-9]*)
```

#### 删除逗号后面所有字符

```
155973091,chycmaxefgk
```

```
,([a-zA-Z0-9]*)
,(.*)
```
#### 匹配中文

```
[\x{4e00}-\x{9fa5}]
```

#### |字符前的所有字符

```
{云代理}YmEHBgUANzY0Kj8y|.59.102:80
{云代理}MzllbmdoVV1TQlVb|7.243.56:8082
{云代理}ZTcRQhNEIXEhbiJz|.10.8:80
{云代理}NGI9BD8CDjcNKA01|8.60.24:80

([^\n^|]*)[|]
```

#### 隐藏某些文件[More](https://zhidao.baidu.com/question/2057317553393860987.html)

`preference-->setting-->user`
```
"file_exclude_patterns": ["*.meta"]
```

#### 定位文件到左边工程所在位置[More](http://julianhigman.com/blog/2013/07/23/sublime-text-3-keyboard-shortcut-to-reveal-file-in-sidebar/)

首选项->按键绑定 - 用户，下添加如下:

```
[
    { "keys": ["alt+f1"], "command": "reveal_in_side_bar"}
]
```


#### 自动对齐/自动缩进

preference->key bindings->user中编辑

```
[
	{ "keys": ["ctrl+q"], "command": "reindent" }
]
```

然后在当前文件中输入设置的快捷键即可跟踪工程文件位置。

## 插件

```
Ctrl + Shift + P, 调用命令面板
输入“Package Control: Install Package”(安装扩展包)，
```

#### `Unity Shader`

#### `ConvertToUTF8`: 修复查看中文乱码[More](https://www.cnblogs.com/QQ931697811/p/5488340.html)

#### `HexViewer`: 文件十六进制查看器

#### `JsFormat`: 格式化javascript sublime text 2 对js进行重新排版[More](http://www.iplaysoft.com/sublimetext.html)

JsFormat 的功能就是可以将一些凌乱的 JavaScript 代码重新排版，
以方便更好地阅读与编辑。
安装成功后，随便打开一个js文件（最好是换行、对齐特别凌乱的那种），按下 Ctrl+Shift+P 调用命令面板，你会发现已经多了一项命令叫做
“Format: Javascript”，快捷键是“CTRL+ALT+F”

若无法格式化,则是因为语法检查不通过可以复制一段简单代码尝试

#### `Ethereum`： Ethereum插件

#### `MarkdownPreview` + `LiveReload`： markdown预览工具

会自动打开网页


#### `SublimeTmpl` :  自动保存utf8文件 新建文本自动填充模板内容


#### `babel`: javascript高亮

安装`MarkdownPreview`后，设置按键

```
{ "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"}  }

"parser": "markdown"也可设置为"parser":"github"，改为使用Github在线API解析markdown。
```

安装LiveReload后，配置
```
Preferences -> Package Settings -> Markdown Preview -> Settings

{
    "enable_autoreload": true
}


再次Ctrl+shift+p, 输入LiveReload: Enable/disable plug-ins, 回车, 选择 Simple Reload with delay (400ms)或者Simple Reload，两者的区别仅仅在于后者没有延迟。
```

#### `tabnine`: Programmer AI

#### 文件夹显示过滤[More](https://developer.aliyun.com/article/356415)

Preferences->Setting-User添加如下命令：
```
"file_exclude_patterns": ["*.meta", "*.bytes","*.class"]
```

#### [MarkdownEditing](https://github.com/SublimeText-Markdown/MarkdownEditin): markdown格式工具

black theme[More](http://www.javatronic.fr/articles/2014/01/10/tuning_sublime_for_markdown_editing.html)
`Preferences > Package Settings > MarkdownEditing > Markdown GFM Settings - User`
```
{
  "extensions":
  [
    "md",
    "mdown",
    "txt",
    "markdown"
  ],

  "color_scheme": "Packages/MarkdownEditing/MarkdownEditor-Dark.tmTheme",

  // Layout
  "draw_centered": false,
  "word_wrap": false,
  "wrap_width": 120
}
```

#### 搜索去除部分目录

全局搜索的Where中输入诸如:`-web/node_modules,-web/dist`语句


#### 右键添加sublime[More](https://blog.csdn.net/geofferysun/article/details/52264069)

复制到SublimeText3的安装目录，然后重命名为：sublime_addright.inf，然后右击安装就可以了
```
[Version]
Signature="$Windows NT$"

[DefaultInstall]
AddReg=SublimeText3

[SublimeText3]
hkcr,"*\\shell\\SublimeText3",,,"Open with SublimeText3"
hkcr,"*\\shell\\SublimeText3\\command",,,"""%1%\sublime_text.exe"" ""%%1"" %%*"
hkcr,"Directory\shell\SublimeText3",,,"Open with SublimeText3"
hkcr,"*\\shell\\SublimeText3","Icon",0x20000,"%1%\sublime_text.exe, 0"
hkcr,"Directory\shell\SublimeText3\command",,,"""%1%\sublime_text.exe"" ""%%1"""
```

## 设置

```
[
    { "keys": ["ctrl+shift+w"], "command": "reveal_in_side_bar"},
    { "keys": ["ctrl+shift+r"], "command": "reveal_in_side_bar"},
    { "keys": ["alt+f1"], "command": "reveal_in_side_bar"},
    { "keys": ["alt+f2"], "command": "toggle_bookmark" },
    { "keys": ["ctrl+alt+p"], "command": "prompt_select_workspace" },
    { "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"}  },
    { "keys": ["f1"], "command": "goto_definition" },
    { "keys": ["ctrl+u"], "command": "open_dir",  "args": { "dir": "$file_path", "file": "$file_name" } },
    { "keys": ["alt+f3"], "command": "find_all_under" },
    { "keys": ["alt+d"], "command": "find_under_expand" }
]
```

```
{
    "font_size": 15,
    "file_exclude_patterns": ["*.meta", ".DS_Store"],
    "ignored_packages":
    [
        "Vintage",
    ],
    "highlight_modified_tabs": true,
    "translate_tabs_to_spaces": true,
    "word_wrap": "true",
    "expand_tabs_on_save" : true,
}
```


#### 每次鼠标经过变量时,都会弹出definitions提示 关闭定义提示

```
"show_definitions": false,
```

#### 不同格式设置tab的缩进

安装插件editorconfig

#### 格式化js[More](https://www.cnblogs.com/luzhenqian/p/9049354.html)

安装插件HTML-CSS-JS Prettify, 默认快捷键ctrl + shift + H

#### 修改主题颜色

工具栏->工具->命令面板,Package Resource Viewer:Open Resource,回车后选择Color Scheme:Monokai

#### 配置lua编译环境

windows安装minGW,配置环境变量,安装ming32-lua版本,重启sublime,新建test.lua,编译使用`ctrl + B`

#### 配置c编译环境

保证安装了c编译器,新建c文件,选择`C_Run`或`C_RuninCommand`：

按`ctrl + shift + b`


#### auto_find_in_selection会导致回车无法替换

## Reference

* [正则使用](http://blog.sina.com.cn/s/blog_df71a16c0101k0q0.html)
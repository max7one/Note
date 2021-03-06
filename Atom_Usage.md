## 快捷键

`ctrl-p` 项目内文件搜索
`ctrl-shift-p` 应用搜索
`ctrl-shift-f` 在当前项目内搜索
`ctrl-m` markdown预览
`F2` 修改文件名
`ctrl-\` 关闭打开侧边栏
`ctrl-,` 打开设置页面
`ctrl-n` 新建文件
`ctrl-o` 打开文件
`ctrl-backspace` 删除到前个单词首
`ctrl-shift-o` 打开文件夹
`ctrl-g` 到达指定行
`ctrl-shift-l` 设定当前文件的语法检测
`ctrl-l` 选定当前行
`ctrl-enter` 下一行输入
`ctrl-j` 合并行
`ctrl-[`/ `]`缩进当前行
`ctrl-shift-k` 删除行
`ctrl-/` 注释
`ctrl-d` 同个多选
`alt-F3` 全选
`ctrl-alt-o` 添加项目
`ctrl-alt-m` 选中括号内的内容
`ctrl-alt-[` 折叠
`ctrl-alt-]` 展开
`ctrl-alt-shift-[` 折叠全部
`ctrl-alt-shift-]` 展开全部
`ctrl-.` 查看按键绑定
`ctrl-r` 查看当前文件的标题(对于查看markdown很有用)
`ctrl-alt-.` 补全标签或括号
`ctrl-alt-j` 跳转到匹配标签或括号

## 其他技巧

- 当焦点位于目录树上时，你可以用快捷键 a,`shift-a`,m 以及 delete 来创建、移动或删除文件和目录
- 当你按下 ctrl-T 或 ctrl-P 的时候，模糊查找框（Fuzzy Finder）就会弹出。它允许你通过输入文件名或路径的一部分，在整个项目中模糊查找相应的文件。

## 配置

keymap.cson 快捷键设置
```
'.editor':
    'ctrl-shift-h': 'atom-beautify:beautify-editor'
    'ctrl-alt-,': 'application:show-settings'

'atom-text-editor':
    'ctrl-e': 'emmet:expand-abbreviation'
    'ctrl-h': 'editor:move-to-first-character-of-line'
    'ctrl-i': 'editor:move-to-end-of-screen-line'
    'ctrl-shift-i': 'editor:split-selections-into-lines'
    'ctrl-0': 'open-in-browser:open'
    'ctrl-shift-/': 'editor:toggle-block-comments'
    'ctrl-m': 'markdown-preview:toggle'
```

snippets.cson 配置
```
'.source.js':
    'dot':
        'prefix': 'd'
        'body': '<%= ${1:"replaced"} %>$2'
```

## 常用插件

- `emmet`  (script:src => <script src=""></script>)
- `language-markdown`
- `atom-beautify`
- `Highlight Selected`
- `open-in-browser`
- `pigments`
- `autocomplete-paths`
- `sublime-block-comment`
- `merge-conflicts`
- `atom-ternjs`
- `file-icons`
- `webbox-color`
- `Goto Definition`
- `split-diff`

**注意点**
`tree-view` 的 `Hide Ignored Names`选上
`autosave` 的 `Enable` 选上
`whitespace` 的 `Remove Tralling whitespace` 去掉

## 正则查找

开启正则  `ctrl-alt-/`
全部替换  `ctrl-enter`

空行  `^\r\n`

## 代码提示补全

`c` -> `enter` ==> code
```
```

## 其他

插件安装不上的问题 (`windows`的解决方式)
1. `windows`在`.atom/package`下`git clone Url`
2. `cd 插件目录`之后 `npm install`
3. 重启`atom`

# sublime

## 1. 通用

- 安装**Package Control**

>组合键 Ctrl+Shift+P 调出命令面板<br>
>输入 ipc （模糊关键字搜索），选择Install Package Control<br>
>左下角有安装提示

- 使用**Package Control**

>组合键 Ctrl+Shift+P 调出命令面板<br>
>输入pc找到Package Control：Install Package 选项
>在搜索框中输入要安装的包名(需要逐个安装，重复以上步骤)

- 配置自动保存

>配置自动保存提高效率<br>
>组合键 Ctrl+Shift+P 调出命令面板<br>
>输入preference，选择preference：setting<br>
>
>```
>	/*
>		Auto save
>	*/
>   "save_on_focus_lost": true,
> ```

## 2. markdown

- 所需插件

| 所需插件        | 主要功能                 |
|-----------------|--------------------------|
| MarkdownEditing | 用于语法高亮             |
| MarkdownPreview | 用于生成HTML文档进行预览 |
| LiveReload      | 用于实时预览             |

 | 作者 | 朝代 | 评分 |
 | :--: | :--: | :--: |
 | 李白 |  唐  | 100  |

- 配置MarkdownEditing

>组合键 Ctrl+Shift+P 调出命令面板<br>
>输入并选择keybinds<br>
>
>```
>[
>     {"keys": ["alt+m"], "command": "markdown_preview", "args": { "target": "browser"}}
> ]
> ```
> 
> 之后即可使用快捷键**alt+m**打开浏览器预览

- 配置LiveReload

>自动启动配置：Preference > Package Settings > LiveReload > Settings - User
>
>```
>{
>  "enabled_plugins": [
>      "SimpleReloadPlugin",
>      "SimpleRefresh"
>  ]
>}
>```



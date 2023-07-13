# windowsTerminal

## 1. 安装

如果电脑没有自带，[官方推荐](https://github.com/microsoft/terminal) 微软应用商店安装

## 2. 基础设置

- 支持图形化界面下配置，与`setting.json`配置文件是相互对应的，文件结构及字段含义参考[官方文档](https://docs.microsoft.com/en-us/windows/terminal/customize-settings/profile-general)：<br>
- 新增窗口建议修改配置文件，其他设置建议直接通过界面操作<br>
- `profiles`配置支持哪些窗口类型，以下是默认自带的；还可以扩展wsl,git bash等
- `defaults`配置全局，`list`各窗口的同名配置项会覆盖全局配置

```json
   "profiles": 
    {
        "defaults": {},
        "list": 
        [
            {
                "commandline": "%SystemRoot%\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
                "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
                "hidden": false,
                "name": "Windows PowerShell"
            },
            {
                "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
                "hidden": false,
                "name": "\u547d\u4ee4\u63d0\u793a\u7b26",
                "commandline": "%SystemRoot%\\System32\\cmd.exe"
            },
            {
                "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
                "hidden": false,
                "name": "Azure Cloud Shell",
                "source": "Windows.Terminal.Azure"
            }
        ]
    }
```

- 扩展Git Bash: `list`种添加以下内容(根据Git安装位置自行修改)

```json
    {
        "commandline": "C:\\Program Files\\Git\\bin\\bash.exe -li",
        "guid": "{ff254222-0d70-4f98-8021-835c5f4349de}",
        "hidden": false,
        "icon": "C:\\Program Files\\Git\\mingw64\\share\\git\\git-for-windows.ico",
        "name": "Git Bash"
    }
```

## 3. 美化

- 自行配置字体、颜色等字段；我的设置及效果图(以cmd为例)

 ```json
        {
         "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
         "background": "#282C34",
            "backgroundImage": "D:\\workbench\\wiki\\source\\_static\\img\\miku.png",
            "backgroundImageAlignment": "bottomRight",
            "backgroundImageOpacity": 0.20000000000000001,
            "backgroundImageStretchMode": "uniform",
            "closeOnExit": "graceful",
            "colorScheme": "One Half Dark",
            "commandline": "%SystemRoot%\\System32\\cmd.exe",
            "cursorColor": "#FFFFFF",
            "cursorShape": "bar",
            "elevate": false,
            "font": 
            {
                "face": "Consolas",
                "size": 10
            },
            "foreground": "#DCDFE4",
            
            "hidden": false,
            "historySize": 9001,
         "name": "\u547d\u4ee4\u63d0\u793a\u7b26",
            "opacity": 85,
            "padding": "0, 0, 0, 0",
            "snapOnInput": true,
            "useAcrylic": true
        }

 ```

- 主题插件美化窗口(以新版powershell为例)
  - 更新powershell
    - `$PSVersionTable`命令查看当前版本，通常情况下自带的是5.x版本，[office官网](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.2)下载msi文件安装即可
  - 安装oh-my-posh
    - [清除旧版](https://ohmyposh.dev/docs/migrating):
      - `Remove-Item $env:POSH_PATH -Force -Recurse` 安装过建议先清楚缓存
      - `Uninstall-Module oh-my-posh -AllVersions` 然后卸载旧版本
    - [重新安装](https://ohmyposh.dev/docs/installation/windows):
      - `winget install JanDeDobbeleer.OhMyPosh -s winget` 使用winget安装，可能会很慢
      - `(Get-Command oh-my-posh).Source` 查看安装路径,需要重新打开终端
      - `winget upgrade JanDeDobbeleer.OhMyPosh -s winget` 需要更新也是通过winget进行
  - oh-my-posh 挑选并配置主题
    - `$env:POSH_THEMES_PATH` 查看 oh-my-posh 主题存放位置 [官方主题预览页](https://ohmyposh.dev/docs/themes)
    - [配置方式](https://ohmyposh.dev/docs/migrating)
      - `echo $PROFILE` 查看当前窗口配置文件路径
      - `if (!(Test-Path -Path $PROFILE )) { New-Item -Type File -Path $PROFILE -Force }` 当前窗口不存在配置文件则先创建
      - `notepad $PROFILE` 编辑配置文件
      - `oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\M365Princess.omp.json" | Invoke-Expression` 配置文件中写入选好的主题(也即主题json文件存放位置)
  - 挑选字体
    - 根据[oh-my-posh官方字体说明](https://ohmyposh.dev/docs/installation/fonts) 主题必须使用Nerd字体族，且具体的字体还需与主题匹配，否则会乱码。
    - oh-my-posh官方推荐使用的字体为`Meslo LGM NF`
    - [Nerd 字体预览及下载](https://www.nerdfonts.com/) 下载后解压直接右键安装即可
    - 本人使用的是`Meslo LGM NF`字体，`M365Princess`主题，效果如图，可以自行尝试不会有乱码的组合(因为官方没给)。

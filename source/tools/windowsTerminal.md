# windowsTerminal

## 安装

如果电脑没有自带，[官方推荐](https://github.com/microsoft/terminal) 微软应用商店安装

## 基础设置

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

### 美化

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

- 


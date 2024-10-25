---
tags:
  - 常见问题
---

# MOD常见问题：入门

### 我要怎么开始做以撒的MOD？（新手入门） {: .subHeader}

如果你能够访问Youtube并且可以听懂英文，推荐观看[Youtube上的Lytebringr的教程视频系列](https://www.youtube.com/playlist?list=PLMZJyHSWa_My5DDoTQcKCgs475xIpQHSF)。这些视频是在胎衣+DLC发布之后制作的，但与忏悔DLC之间没有太大变化，所以它们仍然是你学习诀窍的最佳选择。

如果你不具备查看外网视频的条件，可以去视频网站上搜索一些以撒的MOD制作教程。

胎衣+和忏悔的一个主要区别是，[MOD目录的位置](#where-is-the-directoryfolder-for-mods-located)发生了改变。

其他资源：

- [项目实例教程](../tutorials/ExampleProject.md)
- [一些有用的工具](../tutorials/Tools.md)
- [AgentCucco的视频教程（Youtube）](https://www.youtube.com/playlist?list=PLUYzSIp7NO8cEer2FmtxSXlXoMFirvYDN) （播放列表）
- [:material-language-typescript:IsaacScript的“绿蜡烛”教程](https://isaacscript.github.io/main/example-mod)
- [catinsurance的忏悔MOD制作教程](https://youtube.com/playlist?list=PLkIbky8_pFUpqAF9l7dh_YsEV-zpJ4q50)

## 怎么以以撒的风格制作贴图？ {: .subHeader}

看看LeatherIceCream的这个[视频](https://www.youtube.com/watch?v=cJ68vYqzSm0)，它解释了处理方法。

## 怎么开启调试控制台？ {: .subHeader}

在胎衣+中，控制台在你启用至少一个MOD时会自动启用。

在忏悔中，控制台的启用基于options.ini文件中的"EnableDebugConsole"设置。默认情况下，它被设置为"0"，所以如果你想使用控制台，你必须把它从"0"改成"1"。（默认情况下，options.ini文件位于`文档\My Games\Binding of Isaac Repentance\options.ini`.）

要打开控制台，在一局游戏内按下**波浪号(~)**键。如果你不是英文键盘，详见[wiki的控制台页面](https://isaac.huijiwiki.com/wiki/%E6%8E%A7%E5%88%B6%E5%8F%B0)。

该wiki同时拥有一个[控制台命令的列表](https://isaac.huijiwiki.com/wiki/%E6%8E%A7%E5%88%B6%E5%8F%B0).

## <span id="where-is-the-directoryfolder-for-mods-located">MOD的目录/文件夹在哪里？</span> {: .subHeader}

所有MOD都在这个位置内：

=== ":fontawesome-brands-windows: **Windows**"

    ```
    忏悔:
    [以撒游戏目录]\mods\

    胎衣+:
    文档\My Games\Binding of Isaac Afterbirth+ Mods\
    ```

=== ":fontawesome-brands-apple: **Mac OS**"

    ```
    胎衣+:
    /Users/[username]/Library/Application Support/Binding of Isaac Afterbirth+ Mods
    ```

=== ":fontawesome-brands-linux: **Linux**"

    ```
    胎衣+:
    /Steam/steamapps/compatdata/250900/pfx/drive_c/users/steamuser/Documents/My Games/Binding of Isaac Afterbirth+ Mods
    ```

### 我要怎么解包文件？我要怎么用资源提取器？ {: .subHeader}

默认情况下，游戏资源在：

```
[以撒游戏目录]\resources
```

但是，除非您运行所提供的资源提取器，否则此目录将大部分为空。资源提取器位于此处：

```
[以撒游戏目录]\tools\ResourceExtractor\ResourceExtractor.exe
```

运行提取器后，resources目录将被游戏使用的所有XML文件、ANM2文件、图像和其他各种文件充满。

请注意，每次出现原版补丁时，您还必须重新运行资源提取器。

### anm2文件在哪儿？ {: .subHeader}

- 在以撒中，贴图动画由位于`resources/gfx`文件夹中的anm2文件表示。
- 游戏中的每个实体都有一个相关的anm2文件。
- 此外，UI元素使用各种anm2文件进行渲染（位于`resources/gfx/ui`文件夹中）。
- anm2文件只是一种有不同文件扩展名的XML文件。
- 要编辑原版动画或添加新动画，您可以：
  - 直接使用文本编辑器编辑文件。（以撒前制作人员Kilburn就是这么做的。）
  - 使用提供的以撒动画编辑器编辑文件，该编辑器位于：`[以撒游戏目录]\tools\IsaacAnimationEditor\IsaacAnimationEditor.exe`

### 我修改了一个XML文件，但当我打开游戏或开始新的一局时会崩溃。 {: .subHeader}

崩溃意味着XML文件无效，这意味着您在编辑文件时写错了某个地方。从头开始，一次做一个小编辑，直到你找到导致游戏崩溃的确切部分。

另一个有用的故障排除工具是类似[xmlvalidation.com](https://www.xmlvalidation.com/)的XML验证器。

### 如何得知某个实体的实体类型、变种或子类型？ {: .subHeader}

您可以：

1. 在游戏控制台中输入“spawn x”。例如，“spawn Confessional”将显示忏悔室的ID为6.17。这意味着它的实体类型是6，变种是17。
2. 或者，您可以在“resources-dlc3/entities2.xml”文件中使用ctrl+f搜索您想要的实体。


### 我要怎么编辑房间？ {: .subHeader}

2014年，Chronometrics制作了一个名为[Basement Renovator](https://github.com/Basement-Renovator/Basement-Renovator)的第三方房间编辑器，以改进官方编辑房间的流程。它是开源的，位于GitHub上。由于Basement Renovator比官方房间编辑好用得多，即使是官方开发商现在也使用Basement Renovator。（这就是为什么忏悔房间不能用官方编辑器编辑。）

官方房间编辑器也依然存在，伴随着游戏本体一起提供，位于：

```
[以撒游戏目录]\tools\RoomEditor\RoomEditor.exe
```

Basement Renovator是用Python编写的，因此您可以从源代码运行它，也可以从[发布页面](https://github.com/basement-renovator/basement-renovator/releases)下载exe文件。

### 我要怎么覆盖原版音乐？ {: .subHeader}

- 对于正常的音乐替换，您可以直接在MOD文件夹里替换相应的原版资源文件。
- 对于动态的音乐替换，选择一项：
    - 使用[REPENTOGON](https://repentogon.com/)的[这个回调](https://repentogon.com/enums/ModCallbacks.html?h=music#mc_pre_music_play).
    - 使用Taz的[音乐MOD回调MOD](https://steamcommunity.com/sharedfiles/filedetails/?id=2491006386).
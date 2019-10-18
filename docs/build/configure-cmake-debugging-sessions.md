---
title: 在 Visual Studio 中配置 CMake 调试会话
ms.date: 03/21/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 41f53c0c3ea46a8a1aa11215968aaee6c13c2dea
ms.sourcegitcommit: e33126222c418daf977533ea9e2819d99e0d7b8d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2019
ms.locfileid: "72534107"
---
# <a name="configure-cmake-debugging-sessions"></a>配置 CMake 调试会话

所有可执行的 CMake 目标都显示在“常规”工具栏的“启动项”下拉列表中。 要启动调试会话，只需选择一个调试会话并启动调试程序。

![CMake 启动项下拉列表](media/cmake-startup-item-dropdown.png "CMake 启动项下拉列表")

还可以从解决方案资源管理器启动调试会话。 首先，切换到 "**解决方案资源管理器**" 窗口中的 " **CMake 目标" 视图**。

![CMake 目标视图按钮](media/cmake-targets-view.png  "CMake 目标视图菜单项")

然后，右键单击任何可执行文件，然后选择 "**调试**" 或 "**调试和启动设置**"。 **调试**基于活动配置自动开始调试所选目标。 "**调试" 和 "启动设置**" 将打开 "*启动*" 文件，并为所选目标添加新的 "调试" 配置。

## <a name="customize-debugger-settings"></a>自定义调试器设置

要自定义项目中任何可执行 CMake 目标的调试程序设置，请右键单击特定 CMakeLists.txt 文件，并选择“调试和启动设置”。 （或在**解决方案资源管理器**中的 "**目标" 视图**中选择目标。）当你在子菜单中选择 CMake 目标时 **，将创建一个名为**的文件。 此文件预填充了所选 CMake 目标的相关信息，且允许指定程序参数或调试程序类型等其他参数。 若要引用**CMakeSettings**文件中的任何密钥，**请在该**文件的开头加上 `cmake.`。 下面的示例显示一个简单的**启动**文件，该文件将在**CMakeSettings**文件中提取当前所选配置的 `remoteCopySources` 项的值：

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

一旦您保存了**启动. vs json**文件，就会在 "**启动项**" 下拉列表中创建一个具有新名称的条目。 通过编辑 CMake**文件，** 可为任意数量的目标创建任意数量的调试配置。

## <a name="support-for-cmakesettings-variables"></a>对 CMakeSettings 变量的支持

 **启动. 与 json**支持在**CMakeSettings**中声明的变量（请参阅下文）和适用于当前所选配置的变量。 它还具有一个名为 `currentDir` 的密钥，该密钥为本地项目设置正在启动的应用程序的当前目录：

```json
{
  "type": "default",
  "project": "CMakeLists.txt",
  "projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

运行应用时，`currentDir` 的值类似于以下形式

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```

键 "cwd" 为远程项目设置启动应用程序的当前目录。 默认值为 "$ {debugInfo. System.defaultworkingdirectory}"，其计算结果为 

```cmd
/var/tmp/src/bfc6f7f4-4f0f-8b35-80d7-9198fa973fb9/Linux-Debug
```

## <a name="see-also"></a>请参阅

[Visual Studio 中的 CMake 项目](cmake-projects-in-visual-studio.md)<br/>
[配置 Linux CMake 项目](../linux/cmake-linux-project.md)<br/>
[连接到远程 Linux 计算机](../linux/connect-to-your-remote-linux-computer.md)<br/>
[自定义 CMake 生成设置](customize-cmake-settings.md)<br/>
[配置 CMake 调试会话](configure-cmake-debugging-sessions.md)<br/>
[部署、运行和调试 Linux 项目](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 预定义配置引用](cmake-predefined-configuration-reference.md)<br/>

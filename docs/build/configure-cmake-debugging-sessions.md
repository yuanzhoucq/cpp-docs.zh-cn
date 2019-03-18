---
title: 配置调试会话在 Visual Studio 中的 CMake
ms.date: 03/05/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 9a4dd009544a4590c336697ba2162eec45718869
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825149"
---
# <a name="configure-cmake-debugging-sessions"></a>配置 CMake 调试会话

所有可执行的 CMake 目标都显示在“常规”工具栏的“启动项”下拉列表中。 要启动调试会话，只需选择一个调试会话并启动调试程序。

![CMake“启动项”下拉列表](media/cmake-startup-item-dropdown.png "CMake“启动项”下拉列表")

也可以从 CMake 菜单启动调试会话。

## <a name="customize-debugger-settings"></a>自定义调试器设置

要自定义项目中任何可执行 CMake 目标的调试程序设置，请右键单击特定 CMakeLists.txt 文件，并选择“调试和启动设置”。 当在子菜单中选择 CMake 目标时，名为`launch.vs.json`创建。 此文件预填充了所选 CMake 目标的相关信息，且允许指定程序参数或调试程序类型等其他参数。 若要引用中的任意键`CMakeSettings.json`文件中，前面加上其与`cmake.`中`launch.vs.json`。 下面的示例演示一个简单`launch.vs.json`的值中提取的文件`remoteCopySources`中的键`CMakeSettings.json`当前所选配置文件：

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

一旦您保存`launch.vs.json`文件中，在创建一个条目**启动项**下拉列表中使用新名称。 通过编辑`launch.vs.json`文件中，您可以创建任意数量的 CMake 目标的任意数量的调试配置。

## <a name="support-for-cmakesettings-variables"></a>对出现 CMakeSettings 变量的支持

 `Launch.vs.json` 支持中声明的变量`CMakeSettings.json`（见下文） 和适用于当前所选的配置。 它还具有一个名为密钥`currentDir`，用于设置启动应用程序的当前目录：

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
## <a name="see-also"></a>请参阅

[在 Visual Studio 中的 CMake 项目](cmake-projects-in-visual-studio.md)<br/>
[配置 Linux CMake 项目](../linux/cmake-linux-project.md)<br/>
[连接到远程 Linux 计算机](../linux/connect-to-your-remote-linux-computer.md)<br/>
[自定义 CMake 生成设置](customize-cmake-settings.md)<br/>
[配置 CMake 调试会话](configure-cmake-debugging-sessions.md)<br/>
[部署、运行和调试 Linux 项目](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 预定义的配置参考](cmake-predefined-configuration-reference.md)<br/>
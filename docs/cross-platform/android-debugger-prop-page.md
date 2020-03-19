---
title: Android 调试器属性（C++）
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 3ac896b384181e4e2b436368f39a343d35fe321a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79470273"
---
# <a name="android-debugger-properties"></a>Android 调试器属性

| properties | 说明 | 选项 |
|--|--|--|
| 调试器类型 | 指定要调试的代码类型。 | **仅限本机**<br /><br />仅限 Java |
| 调试目标 | 指定要用于调试的仿真器或设备。 如果没有正在运行的仿真程序，则使用 "Android 虚拟设备（AVD）管理器" 启动设备。 |
| 要启动的包 | 指定要调试的 .apk 的位置。 调试应用程序时，此选项将启动包（APK）。 |
| 启动活动 | 用于启动应用程序的 Android 活动必须与清单中所使用的活动相匹配。 按“应用”从 AndroidManifest.xml 检索列表并动态填充该列表。 |
| 其他符号搜索路径 | 调试符号的其他搜索路径。 |
| 其他 Java 源搜索路径 | Java 源文件的其他搜索路径。 （仅在调试器类型为仅限 Java 时适用。） |

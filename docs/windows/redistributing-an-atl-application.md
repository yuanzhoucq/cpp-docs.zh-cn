---
title: 重新分发 ATL 应用程序
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, redistributing
- redistributing ATL
- redistributing OLE DB templates
- OLE DB templates, redistributing
ms.assetid: 9a696b22-2345-43ec-826b-be7cb8cfd676
ms.openlocfilehash: a1da92a00d6bf88f41801f8eb99433d0c64812b1
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786156"
---
# <a name="redistributing-an-atl-application"></a>重新分发 ATL 应用程序

从 Visual Studio 2012 开始，活动模板库 (ATL) 是仅包含标头的库。 ATL 项目没有指向 ATL 选项的动态链接。 不需要任何可再发行 ATL 库。

如果再次发行 ATL 可执行应用程序，必须通过发出以下命令来注册 .exe 文件（以及它所包含的任何控件）：

```
filename /regserver
```

其中，`filename` 是可执行文件的名称。

在 Visual Studio 2010 中，可以为 MinDependency 或 MinSize 配置生成 ATL 项目。 若将“常规”属性页上的“ATL 的使用”属性设置为“静态链接到 ATL”，并将“代码生成”属性页上的“运行时库”属性设置为“多线程(/MT)”（C/C++ 文件夹），则将获得 MinDependency 配置。

若将“常规”属性页上的“ATL 的使用”属性设置为“动态链接到 ATL”，或将“代码生成”属性页上的“运行时库”属性设置为“多线程 DLL (/MD)”（C/C++ 文件夹），则将获得 MinSize 配置。

MinSize 使输出文件尽可能小，但要求在目标计算机上安装 ATL100.dll 和 Msvcr100.dll（如果选择了“多线程 DLL (/MD)”选项）。 应在目标计算机上注册 ATL100.dll，以确保具有所有 ATL 功能。 ATL100.dll 包含 ANSI 和 Unicode 导出。

针对 MinDependency 目标生成 ATL 或 OLE DB 模板项目时，不需要在目标计算机上安装和注册 ATL100.dll，尽管可能获得更大的程序映像。

如果再次发行 ATL 可执行应用程序，必须通过发出以下命令来注册 .exe 文件（以及它所包含的任何控件）：

```
filename /regserver
```

其中，`filename` 是可执行文件的名称。

## <a name="see-also"></a>请参阅

[重新分发 Visual C++ 文件](redistributing-visual-cpp-files.md)

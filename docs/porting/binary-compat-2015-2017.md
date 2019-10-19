---
title: Visual Studio 2015 和 Visual Studio 2019 之间的 C++ 二进制兼容性
ms.date: 10/17/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 6365ded349ad08a167b76ca9f6ab43e6e7752987
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587901"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>Visual Studio 2015 和 Visual Studio 2019 之间的 C++ 二进制兼容性

在 Visual Studio 2013 及更低版本中，不能保证使用不同编译器工具集和运行时库版本生成的对象文件 (OBJ)、静态库 (LIB)、动态库 (DLL) 和可执行文件 (EXE) 之间的二进制兼容性。 

在 Visual Studio 2015 及更高版本中，C++ 工具集的主版本号是 14（Visual Studio 2015 是 v140，Visual Studio 2017 是 v141，Visual Studio 2019 是 v142）。 这反映了这样的事实：使用这两个版本之一的编译器编译的运行时库和应用程序是二进制兼容的。 这意味着，如果拥有使用 Visual Studio 2015 生成的第三方库，则无需对其进行重新编译即可通过使用 Visual Studio 2017 或 Visual Studio 2019 生成的应用程序使用该库。

此规则的唯一例外是，使用 `/GL` 编译器开关编译的静态库或对象文件不是二进制兼容的。 

混合使用通过 MSVC 工具集的不同受支持版本生成的二进制文件时，应用程序在其上运行的 Visual C++ 可再发行组件的版本不能低于用于生成应用或其使用的任何库的任何工具集版本。 

## <a name="upgrade-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>从 Visual Studio C++ 2015 或2017升级到 visual studio 2019 的 Microsoft Visual 可再发行组件

由于我们已保留二进制兼容性，并且保持与 visual Studio 2015、2017和2019的C++视觉可再发行组件相同的主版本（14），因此，任何时候C++都只能从这些位置安装一个 visual 可再发行组件版本。 较新版本将覆盖已安装的旧版本。 如果你有 visual Studio C++ 2015 或2017中的可再发行组件，然后再安装2019，则2019版本将覆盖较旧的版本。 由于我们确保最新版本将具有所有最新的功能和 bug 修补程序（包括安全修补程序），因此我们始终建议升级到最新的可用版本。

同样，我们不允许在已存在较新版本的C++计算机上安装旧版 Visual 可再发行版本。 在已有C++ 2019 的计算机上安装 visual Studio 2015 或2017中的可再发行组件会导致安装失败。 错误如下所示：

```
*0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.*.
```

此错误是由设计决定的。 建议保留最新的安装。

## <a name="see-also"></a>请参阅

* [Visual C++ 更改历史记录](../porting/visual-cpp-change-history-2003-2015.md)
* [最新支持的C++ Visual 可再发行组件下载](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 

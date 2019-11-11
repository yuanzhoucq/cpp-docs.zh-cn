---
title: C++Visual Studio 2015 和 Visual Studio 2019 之间的二进制兼容性
description: 介绍 Visual Studio 2015、2017和C++ 2019 中编译文件之间的二进制兼容性。 一个 Microsoft Visual C++可再发行组件包适用于所有三个版本。
ms.date: 11/07/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: e41c34abe25deefe100f525044faeac0b0c3054a
ms.sourcegitcommit: eb254b4462a58d219376ff501bf768bd1adc07ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2019
ms.locfileid: "73912877"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>C++Visual Studio 2015 和 Visual Studio 2019 之间的二进制兼容性

在 Microsoft Visual Studio 2013 及更早版本中，在使用不同版本的编译器工具集生成的对象文件（Obj）、静态库（库）、动态链接库（Dll）和可执行文件（Exe）之间不保证二进制兼容性和运行时库。

在 Visual Studio 2015 及更高版本中，C++ 工具集的主版本号是 14（Visual Studio 2015 是 v140，Visual Studio 2017 是 v141，Visual Studio 2019 是 v142）。 这种编号反映了这样一种事实：运行时库和用编译器的任何版本编译的应用程序都是二进制兼容的。 因此，如果你有使用 Visual Studio 2015 生成的第三方库，则无需对其进行重新编译即可从使用 Visual Studio 2017 或 Visual Studio 2019 构建的应用程序中使用它。

此规则的唯一例外是，用 `/GL` 编译器开关编译的静态库或对象文件*不*是二进制兼容的。

当混合使用 Microsoft C++ （MSVC）工具集的不同受支持版本生成的二进制文件时C++ ，应用程序在其上运行的可视可再发行组件包不能早于用于生成应用程序的任何工具集版本或它所使用的任何库。

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>将 Microsoft Visual C++ studio 2015 或2017中的可再发行组件升级到 visual studio 2019

由于我们保留了二进制文件兼容性，并且在 Microsoft Visual Studio 2015、2017和2019的C++ Microsoft Visual 可再发行组件中保持主版本（14）相同，因此， C++在任何时候都只能从这些版本的 visual 可再发行组件安装一个版本。 较新版本将覆盖已安装的旧版本。 如果你有 visual Studio C++ 2015 或2017中的可视可再发行组件，然后再安装 visual studio 2019，则2019版本将覆盖旧版本。 由于我们确保最新版本具有所有最新的功能和 bug 修复（包括安全修补程序），因此我们始终建议升级到最新的可用版本。

同样，我们不允许在已安装较新版本的计算机C++上安装较早版本的 Visual 可再发行组件。 在已具有C++ 2019 版本的计算机上安装 visual Studio 2015 或2017中的可再发行组件会触发安装失败。 此错误如下所示：

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

此错误是由设计决定的。 建议保留最新版本。

## <a name="see-also"></a>请参阅

* [Visual C++ 更改历史记录](../porting/visual-cpp-change-history-2003-2015.md)
* [最新支持的C++ Visual 可再发行组件下载](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 

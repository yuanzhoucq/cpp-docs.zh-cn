---
title: C++Visual Studio 2015、2017和2019之间的二进制兼容性
description: 介绍 Visual Studio 2015、2017和C++ 2019 中编译文件之间的二进制兼容性。 一个 Microsoft Visual C++可再发行组件包适用于所有三个版本。
ms.date: 11/11/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 118ad0a32d5dc8c344967f9a67f2d5b05aa806c0
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965554"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-2017-and-2019"></a>C++Visual Studio 2015、2017和2019之间的二进制兼容性

Visual Studio 2013 和C++更早版本中的 Microsoft （MSVC）编译器工具集不保证各版本之间的二进制兼容性。 不能链接对象文件、静态库、动态库和由不同版本生成的可执行文件。 Abi、对象格式和运行库是不兼容的。

我们已在 Visual Studio 2015、2017和2019中更改了此行为。 任何这些版本的编译器编译的运行时库和应用都是二进制兼容的。 它反映在C++工具集主编号中，这对于所有三个版本均为14。 （工具集版本是 v140 for Visual Studio 2015、v141 for 2017 和 v142 for 2019）。 假设你有 Visual Studio 2015 生成的第三方库。 你仍可以在 Visual Studio 2017 或2019生成的应用程序中使用它们。 无需使用匹配的工具集进行重新编译。 最新版本的 Microsoft Visual C++可再发行组件包（可再发行组件）适用于所有版本。

此规则有一个例外：使用 `/GL` 编译器开关编译的静态库或对象文件在不同版本之间*不*兼容二进制。

应用使用的可再发行组件具有重要的二进制兼容性限制。 当混合使用不同的受支持版本的工具集生成的二进制文件时，它适用。 可再发行版本必须至少与任何应用组件所用的最新工具集相同。

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>将 Microsoft Visual C++ studio 2015 或2017中的可再发行组件升级到 visual studio 2019

我们为 Visual Studio 2015、 C++ 2017 和2019保留了相同的 Microsoft visual 可再发行组件主版本号。 这意味着一次只能安装一个可再发行的实例。 较新的版本将覆盖已安装的任何较旧版本。 例如，一个应用可以安装 Visual Studio 2015 中的可再发行组件。 然后，另一个应用从 Visual Studio 2019 安装可再发行组件。 2019版本覆盖了较旧的版本，但由于它们是二进制兼容的，所以前面的应用程序仍能正常工作。 我们确保最新版本的可再发行组件包含所有最新功能、安全更新和 bug 修复。 这就是我们始终建议升级到最新可用版本的原因。

同样，如果已安装较新版本，则无法安装较旧的可再发行组件。 如果尝试，安装程序将报告错误。 如果在已有2019版本的计算机上安装2015或2017可再发行组件，会看到类似于下面的错误：

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

此错误是由设计决定的。 建议保留最新版本。 请确保安装程序可在不提示的情况下从此错误恢复。

## <a name="see-also"></a>请参阅

[视觉C++更改历史记录](../porting/visual-cpp-change-history-2003-2015.md)\
[最新支持的C++ Visual 可再发行组件下载](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)

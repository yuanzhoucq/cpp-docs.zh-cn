---
title: Microsoft C++移植和升级指南
description: 将 Microsoft C++代码升级到最新版本的 Visual Studio。
ms.date: 11/05/2019
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: overview
ms.openlocfilehash: 04c3950d637c01031e78d0d95e13232143ceb232
ms.sourcegitcommit: 4dde7914608508e47c21cae03ac58fe953a0c29b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74119485"
---
# <a name="microsoft-c-porting-and-upgrading-guide"></a>Microsoft C++移植和升级指南

本主题提供将 Microsoft C++代码升级到最新版本的 Visual Studio 的指南。 如果要从在 Visual Studio 2008 或更早版本中创建的项目进行升级，则必须首先使用 Visual Studio 2010 将该项目转换为 MSBuild 格式，然后在 Visual Studio 2019 中打开该项目。 对于在 Visual Studio 2010 到2015中创建的项目，只需在 Visual Studio 2019 中打开该项目。 有关完整说明，请[参阅C++从早期版本的 Visual Studio 升级项目](upgrading-projects-from-earlier-versions-of-visual-cpp.md)。

Visual Studio 2015、Visual Studio 2017 和 Visual Studio 2019 中的工具集与二进制兼容，使你能够升级到更高版本的编译器，而无需升级库依赖项。 有关详细信息，请参阅[ C++ 2015 和2019之间的二进制兼容性](binary-compat-2015-2017.md)。

升级使用开源库的项目或要在多个平台上运行的项目时，我们建议迁移到基于 CMake 的项目。 有关详细信息，请参阅[Visual Studio 中的 CMake 项目](../build/cmake-projects-in-visual-studio.md)

## <a name="reasons-to-upgrade-c-code"></a>升级C++代码的原因

如果旧版应用程序运行在安全环境中，而不是处于活动状态，则可能不会对其进行升级。 但是，如果应用程序需要持续维护或新的功能开发（包括性能或安全性），则可以考虑出于以下任何原因来升级代码：

- 由于改进了编译器优化，相同的代码可以更快地运行。

- 新式C++功能和编程做法消除了许多常见的 bug 原因，并生成了比旧的 C 样式惯例更容易维护的代码。

- 由于编译器和链接器中的性能改进，生成时间明显更快。

- 更好的标准一致性。 使用[/permissive-](../build/reference/permissive-standards-conformance.md)编译器选项，可以确定 Microsoft C++编译器以前允许但不符合当前C++标准的代码。

- 更好的运行时安全性，包括更安全的[C 运行时库]()功能和编译器功能，如[防护检查](../build/reference/guard-enable-guard-checks.md)和地址 sanitizers （Visual Studio 2019 版本16.4）。

## <a name="multitargeting-vs-upgrading"></a>多定向与升级

如果将基本代码升级到新工具集不是一个选项，你仍可以使用最新版本的 Visual Studio 来生成和编辑使用较旧工具集和库编译的项目。 在 Visual Studio 2019 中，可以利用如下功能：

- 新式静态分析工具，包括C++核心准则检查程序和 Clang，有助于识别源代码中的潜在问题。

- 根据您选择的新式样式自动设置格式可帮助使旧代码更具可读性。

有关详细信息，请参阅 [使用 Visual Studio 中的本机多重目标生成旧项目](use-native-multi-targeting.md)。

## <a name="in-this-section"></a>本节内容

|Title|描述|
|-----------|-----------------|
|[从C++ Visual Studio 的早期版本升级项目](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|如何将基本代码升级到 Visual Studio 2019 和编译器的 v142。|
|[用于升级C++代码的 IDE 工具](ide-tools-for-upgrading-code.md)|有助于升级过程的有用 IDE 功能。|
|[C++2015和2019之间的二进制兼容性](binary-compat-2015-2017.md)|从 v142 项目按原样使用 v140 库。|
|[使用 Visual Studio 中的本机多目标来生成旧项目](use-native-multi-targeting.md)|将 Visual Studio 2019 与较旧的编译器和库配合使用。|
|[Visual C++ 更改历史记录（2003 - 2015）](visual-cpp-change-history-2003-2015.md)|Visual Studio 2003 到2015中的 Microsoft C++库和生成工具的所有更改列表，这些更改可能需要更改代码。|
|[Visual C++ 新增功能（2003 - 2015）](visual-cpp-what-s-new-2003-through-2015.md)|Visual Studio 2003 到 Visual Studio 2015 的所有 " C++新增功能" 信息。|
|[移植和升级：示例和案例研究](porting-and-upgrading-examples-and-case-studies.md)|本部分中，我们移植和升级了多个示例和应用程序并讨论了体验和结果。 你可能会发现阅读这些内容会使你了解移植和升级过程中所涉及的内容。 在整个过程中，我们讨论了升级所用的提示和技巧，并演示如何修复特定错误。|
|[移植到通用 Windows 平台](porting-to-the-universal-windows-platform-cpp.md)|包含有关移植代码到 Windows 10 的信息|
|[Visual C++ 简介（针对 UNIX 用户）](introduction-to-visual-cpp-for-unix-users.md)|为不熟悉 Visual C++ 并想要有效率的使用它的 UNIX 用户提供信息。|
|[在 Windows 上运行 Linux 程序](porting-from-unix-to-win32.md)|讨论用于将 UNIX 应用程序迁移到 Windows 的选项。|

## <a name="see-also"></a>请参阅

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[Visual Studio 中的 C++ 编译器新变化](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Visual Studio 中的 C++ 符合性改进](../overview/cpp-conformance-improvements.md)<br/>

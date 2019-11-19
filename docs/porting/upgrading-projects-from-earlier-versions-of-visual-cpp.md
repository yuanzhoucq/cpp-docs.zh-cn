---
title: 从C++ Visual Studio 的早期版本升级项目
description: 如何从旧版本的 Visual Studio 升级 Microsoft C++ 项目。
ms.date: 10/29/2019
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: b317271a9cd0873e60a6dd9acd1b73a766aaea19
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627170"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>从C++ Visual Studio 的早期版本升级项目

若要升级在 Visual Studio 2008 或更早版本中创建的项目，必须首先使用 Visual Studio 2010 将项目从 VCBuild 格式（. vcproj）转换为 MSBuild 格式（. .vcxproj）。 有关详细信息，请参阅[Visual Studio 2008 说明](use-native-multi-targeting.md#instructions-for-visual-studio-2008)。

若要升级在 Visual Studio 2010 或更高版本中创建的项目，只需在最新版本的 Visual Studio 中打开该项目。 Visual Studio 提供将项目升级到当前架构。 如果你选择 "**否**"，并且你的计算机上已安装了较旧版本的 visual studio，则可以在较新版本的 visual studio 中使用该项目，然后继续以较旧的工具集为目标。 例如，如果项目必须在 Windows XP 上继续运行，则可以将其升级到 Visual Studio 2019，但必须将工具集指定为 v141 或更早版本。 有关详细信息，请参阅 [使用 Visual Studio 中的本机多重目标生成旧项目](use-native-multi-targeting.md)。 如果选择 **"是"** ，则项目将被转换，并且无法转换回早期版本。 因此，在升级方案中，最好是复制现有项目和解决方案文件。

## <a name="upgrade-reports"></a>升级报表

升级项目时，你将获取一个升级报告，该报告也将在你的项目文件夹中保存为 UpgradeLog.htm。 升级报告将显示遇到的问题的摘要，并显示有关所做更改的一些信息，其中包括：

1. 项目属性

2. 包含文件

3. 由于编译器一致性改进或标准中的更改而无法完全编译的代码

4. 依赖于不再可用的 Visual Studio 或 Windows 功能或未包含在 Visual Studio 默认安装中或已从产品中移除的标头文件的代码

5. 由于 API 中的更改（如 API 重命名、函数签名更改或函数弃用）而不再编译的代码

6. 由于诊断中的更改（如警告变为错误）而不再编译的代码

7. 由于库更改导致的链接器错误（尤其是使用 /NODEFAULTLIB 时）。

8. 行为更改所导致的运行时错误或意外结果

9. 工具中引入的错误。 如果遇到问题，请通过正常支持渠道或通过使用 [Visual Studio C++ 开发人员社区](https://developercommunity.visualstudio.com/spaces/62/index.html)页面将其报告给 Visual C++ 团队。

某些升级的项目和解决方案无需修改即可成功生成。 但是，大多数项目可能需要更改项目设置和源代码。 没有一种正确的方法来解决这些错误，但建议使用某种分阶段方法。 在开始之前，请查看[潜在升级问题概述](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)，了解有关多种常见错误的详细信息。

 1. 将平台工具集、 C++语言标准和 Windows SDK 版本（如果适用）设置为所需的版本。 （**Project** > **属性** > **配置属性** > **常规**）
 1. 如果有很多错误，请关闭 "[预许可](../build/reference/permissive-standards-conformance.md)" 选项（**Project** > **属性** > **配置属性** > **C/C++**  > **语言**）和[代码分析](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)（**Project** >  ** > ** **配置属性** > **代码分析**）选项暂时减少错误计数。
 1. 确保所有依赖项都存在并且包含路径或库位置正确。 （**Project** >  > **VC + + 目录** > **配置属性**的**属性**
 1. 标识并修复由于对不再存在的 Api 的引用而导致的错误。
 1. 修复任何阻止编译的剩余错误。 有关常见错误的修补程序，请参阅[潜在的升级问题概述](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)。
 1. 启用**恢复**并修复由于先前在 MSVC 中编译的不符合代码而显示的任何新错误。
 1. 启用代码分析来识别潜在问题或过时的编码模式，这些模式将不再被视为可接受。 如果代码分析标记多个错误，则可以关闭某些警告，使其首先重点关注最重要的部分。 IDE 可以帮助快速修复某些类型的问题。
 1. 请考虑其他现代化代码的机会，例如，通过将C++自定义数据结构和算法替换为标准库中的自定义数据结构和算法或提升的开源库。 通过使用标准功能，你可以更轻松地维护代码，还可以更自信地相信，许多专家在标准委员会和更广泛C++的社区中对代码进行了良好的测试和评审。

若要修复错误，请尝试在 Stack Overflow 或[ C++开发人员社区](https://developercommunity.visualstudio.com/spaces/62/index.html)上搜索或发布问题。

## <a name="in-this-section"></a>本节内容

[潜在的升级问题概述](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[将代码升级到通用 CRT](upgrade-your-code-to-the-universal-crt.md)<br/>
[更新 WINVER 和 _WIN32_WINNT](modifying-winver-and-win32-winnt.md)<br/>
[修复库内部的依赖项](fix-your-dependencies-on-library-internals.md)<br/>
[浮点迁移问题](floating-point-migration-issues.md)<br/>
[C++Visual Studio 2019 中弃用的功能](features-deprecated-in-visual-studio.md)<br/>
[VCBuild 与 MSBuild](build-system-changes.md)<br/>
[第三方库端口](porting-third-party-libraries.md)<br/>

## <a name="see-also"></a>请参阅

[Visual Studio 中 Visual C++ 的新增功能](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Visual C++ 更改历史记录（2003 - 2015）](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[非标准行为](../cpp/nonstandard-behavior.md)<br/>
[端口数据应用程序](../data/data-access-programming-mfc-atl.md)<br/>

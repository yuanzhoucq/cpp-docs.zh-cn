---
title: 从C++ Visual Studio 的早期版本升级项目
description: 如何从旧版本的 Visual Studio 升级 Microsoft C++ 项目。
ms.date: 01/21/2020
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: a18d2dbabdeec0f283fb4eca7ed52e616f9d224a
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725716"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>从C++ Visual Studio 的早期版本升级项目

若要升级在 Visual Studio 早期版本中创建的项目，只需在最新版本的 Visual Studio 中打开该项目。 Visual Studio 提供将项目升级到当前架构。

如果选择 "**否**"，则不会升级项目。 对于在 Visual Studio 2010 及更高版本中创建的项目，仍可在较新版本的 Visual Studio 中使用该项目。 只需将项目属性设置为继续以较旧的工具集为目标。 如果在您的计算机上保留旧版 Visual Studio，则其工具集在更高版本中可用。 例如，如果您的项目必须继续在 Windows XP 上运行，则可以升级到 Visual Studio 2019。 然后，在项目属性中将工具集指定为 v141_xp 或更早版本。 有关详细信息，请参阅 [使用 Visual Studio 中的本机多重目标生成旧项目](use-native-multi-targeting.md)。

如果选择 **"是"** ，则会就地升级项目。 不能将其转换回早期版本。 在升级方案中，这就是创建现有项目和解决方案文件的备份副本的最佳做法。

## <a name="upgrade-reports"></a>升级报表

升级项目时，你将获得升级报告。 该报表还会作为 UpgradeLog 保存在项目文件夹中。 升级报表显示在转换过程中发现的问题的摘要。 其中列出了有关所做更改的一些信息，其中包括：

- 项目属性。

- 包含文件。

- 由于编译器一致性改进或标准中的更改，不再完全编译的代码。

- 依赖于不再可用的 Visual Studio 或 Windows 功能的代码。 或者是不包含在 Visual Studio 默认安装中或已从产品中删除的头文件。

- 由于 Api 中的更改（如重命名的 Api、更改的函数签名或弃用的函数）而不再编译的代码。

- 由于诊断中的更改（如警告变为错误）而不再编译的代码

- 由于库已更改，尤其是在使用/NODEFAULTLIB 时，链接器错误。

- 运行时错误或意外结果，因为行为发生了更改。

- 工具中引入的错误。 如果发现问题，请通过正常支持渠道或通过C++使用[visual Studio C++开发人员社区](https://developercommunity.visualstudio.com/spaces/62/index.html)页面将其报告给视觉对象团队。

某些升级的项目和解决方案无需修改即可成功生成。 但是，大多数项目可能需要对项目设置和源代码进行更改。 不能通过一种正确的方法来解决这些问题，但建议使用分阶段方法。 在开始之前，请查看[潜在升级问题概述](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)，了解有关多种常见错误的详细信息。

1. 将平台工具集、 C++语言标准和 Windows SDK 版本（如果适用）设置为首选版本。 （**Project** > **属性** > **配置属性** > **常规**）

1. 如果有大量错误，可以在修复这些错误时暂时关闭某些选项。 若要关闭[/permissive-](../build/reference/permissive-standards-conformance.md)选项，请使用**Project** > **属性** > **配置属性** > **C/C++**  > **语言**。 若要关闭[代码分析](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)选项，请使用**Project** > **属性** > **配置属性** > **代码分析**。

1. 确保所有依赖项都存在并且包含路径或库位置正确。 （**Project** >  > **VC + + 目录** > **配置属性**的**属性**

1. 标识并修复对不再存在的 Api 的引用导致的错误。

1. 修复任何阻止编译的剩余错误。 有关常见错误的修补程序，请参阅[潜在的升级问题概述](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)。

1. 重新打开 **/permissive-** ，并修复以前在 MSVC 中编译的不符合代码导致的任何新错误。

1. 启用代码分析来识别潜在问题或过时的编码模式，这些模式将不再被视为可接受。 如果代码分析标记多个错误，则可以关闭某些警告，使其首先重点关注最重要的部分。 IDE 可以帮助快速修复某些类型的问题。

1. 请考虑其他现代化代码的机会。 例如，将C++自定义数据结构和算法替换为标准库中的自定义数据结构和算法，或将其替换为增强的开源库。 通过使用标准功能，你可以更轻松地维护代码。 你可以确信，此代码已由许多专家在标准委员会和更广泛C++的社区中进行了良好的测试和审核。

若要修复错误，请尝试在 Stack Overflow 或[ C++开发人员社区](https://developercommunity.visualstudio.com/spaces/62/index.html)上搜索或发布问题。

## <a name="in-this-section"></a>本节内容

[潜在的升级问题概述](overview-of-potential-upgrade-issues-visual-cpp.md)\
将[代码升级到通用 CRT](upgrade-your-code-to-the-universal-crt.md)\
[更新 WINVER 和 _WIN32_WINNT](modifying-winver-and-win32-winnt.md)\
[修复库内部\ 的依赖项](fix-your-dependencies-on-library-internals.md)
[浮点迁移问题](floating-point-migration-issues.md)\
[Visual Studio 2019 中弃用的功能\ C++ ](features-deprecated-in-visual-studio.md)
[VCBuild 与 MSBuild](build-system-changes.md)\
[第三方库端口](porting-third-party-libraries.md)

## <a name="see-also"></a>另请参阅

[Visual Studio 中 Visual C++ 的新增功能](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)\
[视觉C++更改历史记录 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)\
[非标准行为](../cpp/nonstandard-behavior.md)\
[端口数据应用程序](../data/data-access-programming-mfc-atl.md)

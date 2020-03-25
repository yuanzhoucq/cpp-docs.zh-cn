---
title: Visual Studio 中C++项目的 MSBuild 引用
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: ec1285a760d438a94863181a1b099e6db153c268
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168897"
---
# <a name="msbuild-reference-for-c-projects"></a>C++ 项目的 MSBuild 参考

MSBuild 是 Visual Studio 中所有项目的本机生成系统，包括C++项目。 当你在 Visual Studio 集成开发环境（IDE）中生成项目时，它将调用 msbuild.exe 工具，而该工具又使用 .vcxproj 项目文件和各种 .targets 和属性文件。 通常，我们强烈建议使用 Visual Studio IDE 来设置项目属性和调用 MSBuild。 如果未正确完成，手动编辑项目文件可能导致严重问题。

如果由于某种原因要直接从命令行使用 MSBuild，请参阅[从命令行使用 msbuild](../msbuild-visual-cpp.md)。 有关 MSBuild 的常规详细信息，请参阅 Visual Studio 文档中的[msbuild](/visualstudio/msbuild/msbuild) 。

## <a name="in-this-section"></a>在本节中

[C++ 项目的 MSBuild 内部项](msbuild-visual-cpp-overview.md)<br/>
有关如何存储和使用属性和目标的信息。

[用于生成命令和属性的常用宏](common-macros-for-build-commands-and-properties.md)<br/>
介绍可用于定义路径和产品版本等属性的宏（编译时常量）。

[为项目创建的C++文件类型](file-types-created-for-visual-cpp-projects.md)<br/>
描述 Visual Studio 为不同项目类型创建的各种文件。

[Visual Studio C++项目模板](visual-cpp-project-types.md)<br>
描述可用于C++的基于 MSBuild 的项目类型。

[C++ 新项模板](using-visual-cpp-add-new-item-templates.md)<br>
介绍可以添加到 Visual Studio 项目中的源文件和其他项。

[预编译标头文件](../creating-precompiled-header-files.md)如何使用预编译头文件以及如何创建您自己的自定义预编译代码以加速生成时间。

[Visual Studio 项目属性参考](property-pages-visual-cpp.md)<br/>
在 Visual Studio IDE 中设置的项目属性的参考文档。

## <a name="see-also"></a>另请参阅

[C/C++ 生成参考](c-cpp-building-reference.md)

---
title: MS 为视觉工作室中的C++项目构建参考
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: 96987a252d12f718025dd55deecad5c6bac26872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336215"
---
# <a name="msbuild-reference-for-c-projects"></a>C++ 项目的 MSBuild 参考

MSBuild 是 Visual Studio 中所有项目的本机构建系统，包括C++项目。 在 Visual Studio 集成开发环境 （IDE） 中生成项目时，它会调用 msbuild.exe 工具，该工具又会消耗 .vcxproj 项目文件以及各种 .target 和 .props 文件。 通常，我们强烈建议使用 Visual Studio IDE 设置项目属性并调用 MSBuild。 如果操作不正确，手动编辑项目文件可能会导致严重问题。

如果由于某种原因希望直接从命令行使用 MSBuild，请参阅[从命令行使用 MSBuild。](../msbuild-visual-cpp.md) 有关 MSBuild 的详细信息，请参阅可视化工作室文档中的[MSBuild。](/visualstudio/msbuild/msbuild)

## <a name="in-this-section"></a>在本节中

[C++ 项目的 MSBuild 内部项](msbuild-visual-cpp-overview.md)<br/>
有关如何存储和使用属性和目标的信息。

[生成命令和属性的常见宏](common-macros-for-build-commands-and-properties.md)<br/>
描述可用于定义属性（如路径和产品版本）的宏（编译时间常量）。

[为C++项目创建的文件类型](file-types-created-for-visual-cpp-projects.md)<br/>
描述 Visual Studio 为不同的项目类型创建的各种文件。

[可视化工作室C++项目模板](visual-cpp-project-types.md)<br>
描述可用于C++的基于 MSBuild 的项目类型。

[C++ 新项模板](using-visual-cpp-add-new-item-templates.md)<br>
描述源文件以及可以添加到 Visual Studio 项目的其他项目。

[预编译的标头文件](../creating-precompiled-header-files.md)如何使用预编译的标头文件以及如何创建自己的自定义预编译代码以加快生成时间。

[可视化工作室项目属性参考](property-pages-visual-cpp.md)<br/>
在可视化工作室 IDE 中设置的项目属性的参考文档。

## <a name="see-also"></a>另请参阅

[C/C++ 生成参考](c-cpp-building-reference.md)

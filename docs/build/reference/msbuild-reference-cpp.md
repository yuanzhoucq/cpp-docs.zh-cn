---
title: 在 Visual Studio 中的 c + + 项目的 MSBuild 参考
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: b6ec6b5d276cb7104cf61c229476596d2a2a7684
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024694"
---
# <a name="msbuild-reference-for-c-projects"></a>C + + 项目的 MSBuild 参考

MSBuild 是 Visual Studio 中，包括 c + + 项目中的所有项目的本机生成系统。 Visual Studio 集成的开发环境 (IDE) 中的项目生成时，它调用了 msbuild.exe 工具，它又使用.vcxproj 项目文件中和各种.targets 和.props 文件。 一般情况下，我们强烈建议使用 Visual Studio IDE 设置项目属性以及调用 MSBuild。 手动编辑项目文件可能导致严重问题，如果操作不正确。

如果出于某种原因，你想要直接从命令行使用 MSBuild，请参阅[从命令行使用 MSBuild](../msbuild-visual-cpp.md)。 有关 MSBuild 的详细信息一般情况下，请参阅[MSBuild](/visualstudio/msbuild/msbuild) Visual Studio 文档中。

## <a name="in-this-section"></a>本节内容

[MSBuild 的 c + + 项目的内部组件](msbuild-visual-cpp-overview.md)<br/>
有关如何存储和使用属性和目标的信息。

[用于生成命令和属性的常用宏](common-macros-for-build-commands-and-properties.md)<br/>
介绍可用于定义属性，例如路径和产品版本的宏 （编译时常量）。

[C + + 项目创建的文件类型](file-types-created-for-visual-cpp-projects.md)<br/>
描述各种类型的 Visual Studio 会创建不同的项目类型的文件。

[Visual Studio c + + 项目模板](visual-cpp-project-types.md)<br>
介绍可用于 c + + 的基于 MSBuild 的项目类型。

[C + + 新项模板](using-visual-cpp-add-new-item-templates.md)<br>
介绍源文件和其他项可以添加到 Visual Studio 项目。

[预编译标头文件](../creating-precompiled-header-files.md)如何使用预编译标头文件以及如何创建自己的自定义预编译代码，以加快构建时间。

[Visual Studio 项目属性引用](property-pages-visual-cpp.md)<br/>
在 Visual Studio IDE 中设置的项目属性的参考文档。

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](c-cpp-building-reference.md)
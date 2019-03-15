---
title: 如何：而无需更改项目文件中修改 c + + 项目属性和目标
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], modifying outside project file
ms.openlocfilehash: ad527d8ee69a1786be7d325571f9c9ac4f9a8574
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825154"
---
# <a name="how-to-modify-c-project-properties-and-targets-without-changing-the-project-file"></a>如何：而无需更改项目文件中修改 c + + 项目属性和目标

可以从 MSBuild 命令提示符处重写项目属性和目标而无需更改项目文件。 当你想要暂时或偶尔应用某些属性时，这非常有用。 它假定你对 MSBuild 有一定了解。 有关详细信息，请参阅 [MSBUild](https://docs.microsoft.com/visualstudio/msbuild/msbuild)。

> [!IMPORTANT]
> 可以使用 Visual Studio 中的 XML 编辑器或任何文本编辑器来创建 .props 或 .targets 文件。 不要在此情况下使用“属性管理器”，因为它会将属性添加到项目文件中。

重写项目属性：

1. 创键指定要重写的属性的 .props 文件。

1. 从命令提示符处设置 ForceImportBeforeCppTargets="C:\sources\my_props.props"

重写项目目标：

1. 创建具有其实现或特定目标的 .targets 文件

2. 从命令提示符处设置 ForceImportAfterCppTargets ="C:\sources\my_target.targets"

还可以使用/p: 选项在 msbuild 命令行上设置任一选项：

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

以这种方法重写属性和目标等同于将以下导入添加到该解决方案的所有 .vcxproj 文件：

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```

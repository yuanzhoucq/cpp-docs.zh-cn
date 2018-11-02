---
title: /I （附加包含目录）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
ms.openlocfilehash: 0dc1769924880d8cb1b5dc173dd614e87584cac9
ms.sourcegitcommit: 45835842604602a011813d0cd70abc5df91b89ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750387"
---
# <a name="i-additional-include-directories"></a>/I （附加包含目录）

将目录添加到搜索包含文件的目录的列表。

## <a name="syntax"></a>语法

> **/I**[]*目录*

### <a name="arguments"></a>自变量

*目录*<br/>
要添加到的目录列表的目录搜索包含文件。

## <a name="remarks"></a>备注

若要添加多个目录，请多次使用此选项。 仅在找到指定的包含文件之前，将搜索目录。

可以使用此选项与 ([/X （忽略标准包含路径）](../../build/reference/x-ignore-standard-include-paths.md)) 选项。

编译器将按以下顺序搜索目录：

1. 如果指定使用[#include 指令](../../preprocessor/hash-include-directive-c-cpp.md)以双引号形式，它将先搜索本地目录。 在包含文件所在的同一目录中开始执行搜索 **#include**语句。 如果这样做没能找到该文件，它将搜索中的当前打开的目录包含文件，打开它们的相反顺序。 搜索从父包含文件的目录中开始进行，然后继续向上到任何祖父包含文件的目录。

1. 如果指定使用 **#include**角度中的指令进行分类窗体中，或如果本地目录搜索失败，它将搜索通过使用指定的目录 **/I**选项，CL 遇到它们的顺序在命令行中。

1. 指定的目录**INCLUDE**环境变量。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **常规**属性页。

1. 修改**附加包含目录**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>。

## <a name="example"></a>示例

以下命令将查找请求的 MAIN.c 按以下顺序包含文件： 首先，如果使用双引号指定，本地文件进行搜索。 接下来，搜索将继续在的 \INCLUDE 目录中，然后在 \MY\INCLUDE 目录中，并最后的目录中分配给 INCLUDE 环境变量。

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
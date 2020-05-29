---
title: /Fo（对象文件名）
description: Visual Studio 中 Microsoft C++ /Fo（对象文件名）编译器选项的参考指南。
ms.date: 04/20/2020
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: cd22ba745128fe1df67853d98c1495491b9ca840
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748971"
---
# <a name="fo-object-file-name"></a>/Fo（对象文件名）

指定要使用的对象*`.obj`*（ ） 文件名或目录，而不是默认值。

## <a name="syntax"></a>语法

> **`/Fo`**_路径_

## <a name="remarks"></a>备注

可以使用**`/Fo`** 编译器选项为 CL 编译器命令生成的所有对象文件设置输出目录。 或者，您可以使用它重命名单个对象文件。

默认情况下，编译器生成的对象文件将放置在当前目录中。 它们被赋予源文件的基本名称和*`.obj`* 扩展名。

要使用**`/Fo`** 选项重命名对象文件，请指定输出文件名作为*路径名*参数。 重命名对象文件时，可以使用所需的任何名称和扩展名，但建议的约定是使用*`.obj`*。 如果指定要编译多个源文件时的文件名，**`/Fo`** 编译器将生成命令行错误 D8036。

要使用**`/Fo`** 选项为 CL 命令创建的所有对象文件设置输出目录，请指定该目录为*路径名称*参数。 目录由*路径名称*参数中的尾随斜杠指示。 指定的目录必须存在;它不是自动创建的。

## <a name="example"></a>示例

以下命令行在驱动器 D 上的现有目录*\\中间*的中间值中创建名为*sample.obj*的对象文件。

```cmd
CL /Fo"D:\intermediate\" /EHsc /c sample.cpp
```

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>在可视化工作室中设置选项，或以编程方式设置选项

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/C++** > **输出文件**属性页。

1. 修改**对象文件名**属性以设置输出目录。 在 IDE 中，对象文件必须具有 的*`.obj`* 扩展名。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>。

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](output-file-f-options.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[指定路径名](specifying-the-pathname.md)

---
title: -I (附加包含目录) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
dev_langs:
- C++
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a580488650a1272ec1dffcd1f0ba27c736df92da
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705336"
---
# <a name="i-additional-include-directories"></a>/I（附加包含目录）

将目录添加到搜索包含文件的目录的列表。

## <a name="syntax"></a>语法

```
/I[ ]directory
```

## <a name="arguments"></a>自变量

*目录*<br/>
要添加到的目录列表的目录搜索包含文件。

## <a name="remarks"></a>备注

若要添加多个目录，请多次使用此选项。 仅在找到指定的包含文件之前，将搜索目录。

可以将此选项用于忽略标准包含路径 ([/X （忽略标准包含路径）](../../build/reference/x-ignore-standard-include-paths.md)) 选项。

编译器搜索目录按以下顺序：

1. 包含的源文件的目录。

1. 用指定的目录 **/I**选项，CL 遇到它们的顺序。

1. 指定的目录**INCLUDE**环境变量。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**常规**属性页。

1. 修改**附加包含目录**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>。

## <a name="example"></a>示例

以下命令将查找请求的 MAIN.c 按以下顺序包含文件： 包含 MAIN.c，然后在的 \INCLUDE 目录中，然后在 \MY\INCLUDE 目录中，并将最后的目录中分配给包含的目录中的第一行环境变量。

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
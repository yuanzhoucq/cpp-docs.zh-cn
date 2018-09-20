---
title: -Fp （名称。Pch 文件） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- /fp
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
dev_langs:
- C++
helpviewer_keywords:
- Fp compiler option [C++]
- -Fp compiler option [C++]
- naming precompiler header files
- PCH files, naming
- names [C++], PCH
- .pch files, naming
- precompiled header files, naming
- /Fp compiler option [C++]
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a851f93ae845d56b9c986e822e94970ad5cccd5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427129"
---
# <a name="fp-name-pch-file"></a>/Fp（命名 .Pch 文件）

提供的预编译标头而不是使用默认路径名称的路径名称。

## <a name="syntax"></a>语法

> **/Fp**<em>路径名</em>

## <a name="remarks"></a>备注

使用此选项与[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)或[/Yu （使用预编译标头文件）](../../build/reference/yu-use-precompiled-header-file.md)提供而不是使用默认路径名称的预编译标头的路径名称。 此外可以使用 **/Fp**与 **/Yc**若要指定不同于预编译的头文件使用 **/Yc**<em>文件名</em>参数和从源代码文件的基名称。

如果未指定扩展的路径名称的一部分，则假定.pch 的扩展名。 如果指定的目录不包含文件名称，默认文件名称是 VC*x*0.pch，其中*x*是 Visual c + + 中使用的主要版本。

此外可以使用 **/Fp**选项与 **/Yu**。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**预编译标头**属性页。

1. 修改**预编译头文件**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>。

## <a name="example"></a>示例

如果你想要创建您的程序的调试版本的预编译标头文件和标头文件和源代码进行编译，可以如指定的命令：

```
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

## <a name="example"></a>示例

以下命令指定使用名为 MYPCH.pch 的预编译标头文件。 编译器将假定已预 PROG.cpp 中的源代码编译通过 MYAPP.h 和预编译的代码位于 MYPCH.pch。 它使用 MYPCH.pch 的内容，并将编译 PROG.cpp 创建的.obj 文件的其余部分。 此示例的输出是名为 PROG.exe 的文件。

```
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](../../build/reference/output-file-f-options.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[指定路径名](../../build/reference/specifying-the-pathname.md)
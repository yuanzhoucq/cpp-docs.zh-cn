---
title: /Fp (名称&period;pch 文件)
description: /Fp 编译器选项用于指定预编译标头文件的名称。
ms.date: 05/31/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- /fp
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
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
ms.openlocfilehash: 6e7faa934d14acb5d129173c5e0c7ee67d6caf2b
ms.sourcegitcommit: 540fa2f5015de1adfa7b6bf823f6eb4ed5a6a4bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2019
ms.locfileid: "66460875"
---
# <a name="fp-name-periodpch-file"></a>/Fp (名称&period;pch 文件)

提供的预编译标头而不是使用默认路径名称的路径名称。

## <a name="syntax"></a>语法

> **/Fp**<em>pathname</em>

## <a name="remarks"></a>备注

使用 **/Fp**选项与[/Yc （创建预编译标头文件）](yc-create-precompiled-header-file.md)或[/Yu （使用预编译标头文件）](yu-use-precompiled-header-file.md)指定预编译标头 (PCH) 的路径和文件名称文件。 默认情况下 **/Yc**选项通过使用源文件的基名称来创建 PCH 文件名称和一个*pch*扩展。

如果未指定扩展的一部分*pathname*的扩展*pch*假定。 当通过使用正斜杠指定目录名称 ( **/** ) 的末尾*pathname*，默认文件名为 vc*版本*0.pch，其中*版本*是 Visual Studio 工具集的主要版本。 此目录必须存在，或者会生成 C1083 错误。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 打开**配置属性** > **C /C++**  > **预编译标头**属性页。

1. 修改**预编译头输出文件**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="examples"></a>示例

若要创建单独的命名版本程序的调试版本的预编译标头文件，可以如指定的命令：

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

以下命令指定使用名为 MYPCH.pch 的预编译标头文件。 编译器预编译到 MYAPP.h，PROG.cpp 中的源代码，并将预编译的代码放入 MYPCH.pch。 然后使用 MYPCH.pch 的内容，并将编译 PROG.cpp 创建的.obj 文件的其余部分。 此示例的输出是名为 PROG.exe 的文件。

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](output-file-f-options.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[指定路径名](specifying-the-pathname.md)

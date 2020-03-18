---
title: /Fp （命名 &period;pch 文件）
description: 使用/Fp 编译器选项指定预编译头文件名称。
ms.date: 05/31/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
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
ms.openlocfilehash: d62c5bd9fc7920c0a2a5530879680fad2a01d39a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439783"
---
# <a name="fp-name-periodpch-file"></a>/Fp （命名 &period;pch 文件）

提供预编译标头的路径名称，而不是使用默认路径名称。

## <a name="syntax"></a>语法

> **/Fp**<em>路径名</em>

## <a name="remarks"></a>备注

将 **/fp**选项与[/Yc （创建预编译标头文件）](yc-create-precompiled-header-file.md)或[/Yu （使用预编译头文件）](yu-use-precompiled-header-file.md)一起使用，以指定预编译头（PCH）文件的路径和文件名。 默认情况下， **/yc**选项使用源文件的基名称和*PCH*扩展创建 pch 文件名。

如果未将扩展指定为*路径名称*的一部分，则假定为*pch*的扩展。 当你通过在*pathname*末尾使用斜杠（ **/** ）来指定目录名称时，默认文件名为 vc*版本*0 .Pch，其中*版本*是 Visual Studio 工具集的主版本。 此目录必须存在或生成错误 C1083。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1.  > **预编译标头**属性页打开 " **C++**  **配置属性**" > 。

1. 修改 "**预编译标头输出文件**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="examples"></a>示例

若要为程序的调试版本创建单独的预编译头文件的命名版本，可以指定如下所示的命令：

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

以下命令指定使用名为 MYPCH 的预编译头文件。 编译器通过 MYAPP 结束预编译进程中的源代码，并将预编译代码放在 MYPCH 中。 然后，它使用 MYPCH 的内容并编译程序的其余部分以创建 .obj 文件。 此示例的输出是一个名为 "al.exe" 的文件。

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>另请参阅

[输出文件 (/F) 选项](output-file-f-options.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[指定路径名](specifying-the-pathname.md)

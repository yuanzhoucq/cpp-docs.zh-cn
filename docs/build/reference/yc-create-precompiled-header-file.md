---
title: /Yc（创建预编译标头文件）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
ms.openlocfilehash: 71a05df3adc74edfd814bb6dc15121e4a343dc4d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825751"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc（创建预编译标头文件）

指示编译器创建一个预编译标头（.pch）文件，该文件表示某个时间点的编译状态。

## <a name="syntax"></a>语法

> __/Yc__\
> __/Yc__*filename*

## <a name="arguments"></a>参数

*名字*<br/>
指定标头（.h）文件。 使用此参数时，编译器将编译所有代码，直到包含 .h 文件。

## <a name="remarks"></a>备注

如果在不使用参数的情况下指定 **/yc** ，则编译器会将所有代码编译到基源文件的末尾，或者编译到基文件中出现[hdrstop](../../preprocessor/hdrstop.md)指令的点。 生成的 .pch 文件具有与基源文件相同的基名称，除非你使用**hdrstop**杂注或 **/fp**选项指定其他文件名。

预编译代码保存在一个文件中，该文件的名称是通过使用 **/yc**选项指定的文件的基名称和一个 .pch 扩展名创建的。 还可以使用[/fp （Name）。Pch 文件）](fp-name-dot-pch-file.md)选项指定预编译头文件的名称。

如果使用 __/yc__*filename*，则编译器会将所有代码编译为并包含指定的文件，以便以后用于[/Yu （使用预编译标头文件）](yu-use-precompiled-header-file.md)选项。

如果选项 __/yc__*filename*和 __/yu__*filename*出现在相同的命令行上，同时引用相同的文件名，则将优先使用 __/yc__*filename* 。 此功能简化了生成生成的编写。

有关预编译标头的详细信息，请参阅：

- [/Y（预编译标头）](y-precompiled-headers.md)

- [预编译标头文件](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 选择 .cpp 文件。 .Cpp 文件必须 #include 包含预编译标头信息的 .h 文件。 项目的 **/yc**设置可以在文件级别重写。

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 打开**配置属性**" **c/c + +**" "**预编译头**" 属性页。

1. 修改**预编译标头**属性。

1. 若要设置文件名，请修改**预编译标头文件**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>。

## <a name="example"></a>示例

考虑下列代码：

```cpp
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
// ...
```

使用命令`CL /YcMYAPP.H PROG.CPP`编译此代码时，编译器会在名为 "MYAPP" 的预编译头文件中保存 AFXWIN.H、RESOURCE .H 和 MYAPP 的所有预处理。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[预编译标头文件](../creating-precompiled-header-files.md)

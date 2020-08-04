---
title: /Yu（使用预编译标头文件）
ms.date: 07/31/2020
f1_keywords:
- /Yu
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
ms.openlocfilehash: 8cccce39949f23e4ceb72807ecaef3597ab733c4
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520457"
---
# <a name="yu-use-precompiled-header-file"></a>`/Yu`（使用预编译头文件）

指示编译器在当前编译中使用现有预编译头（ *`.pch`* ）文件。

## <a name="syntax"></a>语法

> **`/Yu`**\[*文件名*]

## <a name="arguments"></a>参数

*filename*<br/>
标头文件的名称，该文件包含在使用 `#include` 预处理器指令的源文件中。

## <a name="remarks"></a>备注

对于 **`/Yc`** 创建预编译标头的选项，和用于 **`/Yu`** 指示使用预编译标头的任何更高版本选项，包含文件的名称必须相同。

对于 **`/Yc`** ， *filename*指定预编译停止的点; 编译器将按*文件名*预编译所有代码，并使用包含文件的基名称和的扩展名命名生成的预编译标头 *`.pch`* 。

此 *`.pch`* 文件必须使用创建 **`/Yc`** 。

编译器将 .h 文件之前出现的所有代码视为预编译。 它跳转到 `#include` 与该文件关联的指令以外 *`.h`* ，使用文件中包含的代码 *`.pch`* ，然后在*filename*后面编译所有代码。

在命令行上，和文件名之间不允许有空格 **`/Yu`** 。 *filename*

如果在 **`/Yu`** 不使用文件名的情况下指定选项，则源程序必须包含 [`#pragma hdrstop`](../../preprocessor/hdrstop.md) 指定预编译头文件的文件名的杂注 *`.pch`* 。 在这种情况下，编译器将使用名为的预编译标头（ *`.pch`* 文件） [`/Fp (Name .pch file)`](fp-name-dot-pch-file.md) 。 编译器将跳到该杂注的位置，并从指定的预编译头文件还原已编译状态。 然后，它只编译紧跟杂注的代码。 如果 `#pragma hdrstop` 未指定文件名，则编译器将查找名称派生自源文件的基名称（扩展名为）的文件 *`.pch`* 。 你还可以使用 **`/Fp`** 选项指定其他 *`.pch`* 文件。

如果指定 **`/Yu`** 不带文件名的选项，并且无法指定 `hdrstop` 杂注，则会生成错误消息，并且编译将失败。

如果 **`/Yc`** _filename_和 **`/Yu`** _filename_选项出现在相同的命令行上，并且两者都引用相同的文件名，则 **`/Yc`** _文件名_优先，预编译所有的代码，直到包含命名文件。 此功能简化了生成生成的编写。

由于 *`.pch`* 文件包含有关有关程序的计算机环境和内存地址信息的信息，因此只应在 *`.pch`* 创建该程序的计算机上使用该文件。

有关预编译标头的详细信息，请参阅：

- [`/Y`（预编译头）](y-precompiled-headers.md)

- [预编译标头文件](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 在项目中的 .cpp 文件上指定[ `/Yc` （创建预编译标头文件）](yc-create-precompiled-header-file.md) 。

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **预编译头**" 属性页。

1. 修改**预编译标头**属性，**创建/使用 PCH 到 File**属性，或**创建/使用预编译标头**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>。

## <a name="example"></a>示例

如果以下代码：

```cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
...
```

使用命令行进行编译时 `CL /YuMYAPP.H PROG.CPP` ，编译器不会处理这三个 include 语句。 相反，它使用来自的预编译代码 *`MYAPP.pch`* ，这节省了预处理所有三个文件（以及它们可能包含的任何文件）所涉及的时间。

[`/Fp (Name .pch file)`](fp-name-dot-pch-file.md) **`/Yu`** *`.pch`* 如果名称不同于*filename*参数或源文件的基名称，则可以将选项与选项一起使用，以指定文件的名称 **`/Yc`** ，如以下示例中所示：

```cmd
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP
```

此命令指定名为的预编译头文件 *`MYPCH.pch`* 。 编译器使用其内容来还原所有标头文件（包括在内）的预编译状态 *`MYAPP.h`* 。 然后，编译器编译在 * 指令之后发生的代码 `#include "MYAPP.h"` 。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)

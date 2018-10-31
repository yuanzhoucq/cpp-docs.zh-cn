---
title: /Yd（将调试信息放在对象文件中）
ms.date: 11/04/2016
f1_keywords:
- /yd
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
ms.openlocfilehash: eda3dd38449f89d9b8d767b460970d659f6c9dc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430012"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd（将调试信息放在对象文件中）

从与一起使用时的预编译标头 (.pch) 文件创建完整的调试信息对象的所有文件中的所有步骤[/Yc](../../build/reference/yc-create-precompiled-header-file.md)并[/z7](../../build/reference/z7-zi-zi-debug-information-format.md)选项。 已否决。

## <a name="syntax"></a>语法

```
/Yd
```

## <a name="remarks"></a>备注

**/Yd**已弃用;Visual c + + 现在支持多个对象写入单一的.pdb 文件，请使用 **/Zi**相反。 有关不推荐使用的编译器选项的列表，请参阅**已弃用并删除的编译器选项**中[按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)。

除非需要将库包含调试信息，否则使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)选项而非 **/z7**并 **/Yd**。

将完整的调试信息存储在每个.obj 文件是只需将包含调试信息的库分发。 它会降低编译，并且需要大量的磁盘空间。 当 **/Yc**并 **/z7**而无需使用 **/Yd**，编译器创建.pch 文件中的第一个.obj 文件中存储常见的调试信息。 编译器不将此信息插入到.pch 文件中; 随后创建的.obj 文件它将插入交叉引用的信息。 无论多少个.obj 文件使用.pch 文件，只有一个.obj 文件包含常见的调试信息。

虽然此默认行为会导致更快地生成时间并降低磁盘空间要求，但是它并不可取如果很小的更改需要重新生成包含常见的调试信息的.obj 文件。 在这种情况下，编译器必须重新生成包含对原始的.obj 文件的交叉引用的所有.obj 文件。 此外，如果常见的.pch 文件由不同的项目中，依赖于对单个.obj 文件的交叉引用是非常困难。

预编译标头的详细信息，请参阅：

- [/Y（预编译标头）](../../build/reference/y-precompiled-headers.md)

- [创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="examples"></a>示例

假设您有两个基本文件，F.cpp 和 G.cpp，每个包含下列 **#include**语句：

```
#include "windows.h"
#include "etc.h"
```

以下命令创建预编译标头文件 ETC.pch 和对象文件 F.obj:

```
CL /YcETC.H /Z7 F.CPP
```

对象文件 F.obj 包括类型和 WINDOWS.h 和 ETC.h 的符号信息 （和它们包含的任何其他标头文件）。 现在，可以使用预编译标头 ETC.pch 编译源文件 G.cpp:

```
CL /YuETC.H /Z7 G.CPP
```

对象文件 G.obj 不包括预编译标头的调试信息，但只引用 F.obj 文件中的信息。 请注意，必须使用 F.obj 文件链接。

如果使用未编译预编译标头 **/z7**，您仍可以在使用更高版本编译中使用它 **/z7**。 但是，调试信息放在当前的对象文件中，并且本地函数和预编译标头中定义的类型提供了符号不到调试器。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
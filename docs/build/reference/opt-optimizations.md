---
title: /OPT （优化） |Microsoft 文档
ms.custom: ''
ms.date: 05/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc9f7f66b9bd0ee2c0da65d17eac33e1cbc8c316
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2018
---
# <a name="opt-optimizations"></a>/OPT（优化）

控制 LINK 在生成期间执行的优化。

## <a name="syntax"></a>语法

> **/OPT:**{**REF** | **NOREF**}<br/>
> **/OPT:**{**ICF**[**=**_迭代_] |**NOICF**}<br/>
> **/OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>自变量

**REF** &AMP;#124; **NOREF**

**/Opt: ref**消除函数和从未引用; 的数据 **/OPT:NOREF**保留函数和从未引用的数据。

启用 /opt: ref 时，LINK 会移除未引用的已打包的函数和数据，称为*Comdat*。 此优化称为可传递的 COMDAT 消除。 **/Opt: ref**选项还禁用增量链接。

内联的函数和类声明中定义的成员函数始终是 Comdat。 所有的对象文件中的函数构成 Comdat，如果它通过编译[/Gy](../../build/reference/gy-enable-function-level-linking.md)选项。 要放置**const** Comdat 中的数据，你必须将其声明使用`__declspec(selectany)`。 有关如何指定移除或折叠的数据的信息，请参阅[selectany](../../cpp/selectany.md)。

默认情况下， **/opt: ref**通过链接器，除非 **/OPT:NOREF**或[/调试](../../build/reference/debug-generate-debug-info.md)指定。 若要覆盖此默认设置，并在程序中保留未引用的 Comdat，请指定 **/OPT:NOREF**。 你可以使用[/包括](../../build/reference/include-force-symbol-references.md)选项重写特定符号的删除。

如果[/调试](../../build/reference/debug-generate-debug-info.md)指定，则默认为 **/选择**是**NOREF**，和所有函数都保留在映像中。 若要覆盖此默认设置，并优化调试生成，指定 **/opt: ref**。 这可以减小可执行文件，并且可以优化的有用，甚至在调试生成。 我们建议你还指定 **/OPT:NOICF**若要保留相同函数在调试生成。 这样更容易读取堆栈跟踪以及在本应折叠在一起的函数中设置断点。

**ICF**\[**=**_迭代_] &#124; **NOICF**

使用**ICF**\[**=**_迭代_] 若要执行相同的 COMDAT 折叠。 可以从链接器输出中删除冗余 COMDAT。 可选*迭代*参数指定的次数来遍历重复项的符号。 默认迭代次数为 1。 附加的迭代可以找到更多前一次迭代中未通过折叠发现的重复项。

默认情况下， **/opt: icf**通过链接器，除非 **/OPT:NOICF**或[/调试](../../build/reference/debug-generate-debug-info.md)指定。 若要覆盖此默认设置，并防止 Comdat 正在折叠在程序中，指定 **/OPT:NOICF**。

在调试版本中，你必须显式指定 **/opt: icf**以启用 COMDAT 折叠。 但是，因为 **/opt: icf**可以合并相同的数据或函数，它可以更改显示在堆栈跟踪中的函数名。 它还可以使其无法在某些函数中设置断点或检查在调试器中，某些数据，并可能会跳转到意外的函数时你单步执行代码。 代码的行为完全相同，但调试器演示文稿可以是非常容易引起混淆。 因此，不建议你使用 **/opt: icf**在调试生成中除非较小的代码的好处能弥补这些不足。

> [!NOTE]
> 因为 **/opt: icf**可以使同一地址分配给不同的函数或只读数据成员 (即， **const**变量时使用编译的 **/Gy**)，它能中断依赖于函数或只读数据成员的唯一地址的程序。 有关详细信息，请参阅 [/Gy （启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md)。

**LBR** &AMP;#124; **NOLBR**

**/Opt: lbr**和 **/OPT:NOLBR**选项仅适用于 ARM 二进制文件。 由于某些 ARM 处理器分支指令的范围有限，因此如果链接器检测到跳转的地址超出范围，它就会将分支指令的目标地址替换成包含指向实际目标的分支指令的代码“岛”的地址。 你可以使用 **/opt: lbr**来优化对长分支指令的检测和中间代码岛，若要最大程度减少总体代码大小的布局。 **/OPT:NOLBR**指示链接器生成的长分支指令的代码岛，为遇到，但不进行优化。

默认情况下， **/opt: lbr**增量链接未启用时，设置选项。 如果需要非增量链接而不是长分支优化，请指定 **/OPT:NOLBR**。 **/Opt: lbr**选项禁用增量链接。

## <a name="remarks"></a>备注

如果使用在命令行，链接器将默认为 **/opt: ref，ICF，LBR**。 如果 **/调试**指定，默认值是 **/OPT:NOREF，NOICR，NOLBR**。

**/选择**优化通常减小映像大小并加快程序速度。 这些改进可以在是很明显较大的程序，这就是为什么零售版本的默认启用它们。

链接器优化提前，都会占用额外的时间，但在优化的代码还保存的时间，链接器具有较少的重定位，若要修复，并创建较小的最终图像，从而节省了当它具有较少的调试信息来处理和写入 PDB 的更多时间。 如果启用了优化，它可以会更快的链接时在总体上而言，根据在分析中的小额外成本可能会超过由链接器中的节省经过较小的二进制文件的时间偏移量。

**/选择**自变量可指定在一起，并用逗号隔开。 而不是，如 **/opt: ref /OPT:NOICF**，你可以指定 **/opt: ref、 NOICF**。

你可以使用[/详细](../../build/reference/verbose-print-progress-messages.md)链接器选项，以查看通过删除的函数 **/opt: ref**和通过折叠函数 **/opt: icf**。

**/选择**通常将其自变量设置为使用创建的项目**新项目**对话框在 Visual Studio IDE 中，并通常具有不同的值，用于调试和发布配置。 如果你的项目中这些链接器选项不设置任何值，则可能获得项目默认值，它可以是不同于在命令行链接器使用的默认值。

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 OPT:ICF 或 OPT:REF 链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **优化**属性页。

1. 修改以下属性之一：

   - **启用 COMDAT 折叠**

   - **参考资料**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 OPT:LBR 链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入中的选项**其他选项**:

   `/opt:lbr` 或 `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> 属性。

## <a name="see-also"></a>请参阅

- [设置链接器选项](../../build/reference/setting-linker-options.md)
- [链接器选项](../../build/reference/linker-options.md)

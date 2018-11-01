---
title: /OPT（优化）
ms.date: 05/18/2018
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
ms.openlocfilehash: ad89dfa29df6e4ef500e01e53f203fa3c401602b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638225"
---
# <a name="opt-optimizations"></a>/OPT（优化）

控制 LINK 在生成期间执行的优化。

## <a name="syntax"></a>语法

> **/ 选择：**{**REF** | **NOREF**}<br/>
> **/ 选择：**{**ICF**[**=**_迭代_] |**NOICF**}<br/>
> **/ 选择：**{**LBR** | **NOLBR**}

## <a name="arguments"></a>自变量

**REF** &AMP;#124; **NOREF**

**/Opt: ref**消除了函数和数据永远不会引用;**/Opt: noref**保留从未引用过的函数和数据。

当启用 /opt: ref 时，LINK 移除未引用的已打包的函数和数据，称为*Comdat*。 此优化称为可传递的 COMDAT 消除。 **/Opt: ref**选项也会禁用增量链接。

内联的函数和类声明中定义的成员函数始终为 Comdat。 所有的对象文件中的函数将组成排列的 Comdat，如果使用编译[/Gy](../../build/reference/gy-enable-function-level-linking.md)选项。 若要放置**const** Comdat 中的数据，您必须将其声明使用`__declspec(selectany)`。 有关如何指定用于删除或折叠的数据的信息，请参阅[selectany](../../cpp/selectany.md)。

默认情况下 **/opt: ref**除非由链接器启用 **/opt: noref**或[/debug](../../build/reference/debug-generate-debug-info.md)指定。 若要替代此默认设置，并在程序中保留未引用的 Comdat，指定 **/opt: noref**。 可以使用[/include](../../build/reference/include-force-symbol-references.md)选项重写特定符号的删除。

如果[/debug](../../build/reference/debug-generate-debug-info.md)指定的默认值为 **/opt**是**NOREF**，而且所有函数都保留在映像中。 若要覆盖此默认值和优化的调试版本，请指定 **/opt: ref**。 这可以减少到可执行文件的大小，并可以是一项实用优化甚至在调试生成。 我们建议，还可以指定 **/OPT:NOICF**若要保留相同函数在调试生成。 这样更容易读取堆栈跟踪以及在本应折叠在一起的函数中设置断点。

**ICF**\[**=**_迭代_] &#124; **NOICF**

使用**ICF**\[**=**_迭代_] 若要执行相同的 COMDAT 折叠。 可以从链接器输出中删除冗余 COMDAT。 可选*迭代*参数指定的次数来遍历重复项的符号。 默认迭代次数为 1。 附加的迭代可以找到更多前一次迭代中未通过折叠发现的重复项。

默认情况下 **/opt: icf**除非由链接器启用 **/OPT:NOICF**或[/debug](../../build/reference/debug-generate-debug-info.md)指定。 若要替代此默认设置，并防止排列的 Comdat 折叠在程序中，指定 **/OPT:NOICF**。

在调试版本中，您必须显式指定 **/opt: icf**以启用 COMDAT 折叠。 但是，由于 **/opt: icf**可以合并相同的数据或函数，它可以更改堆栈跟踪中出现的函数名称。 它还可以使其不可能在某些函数中设置断点，或检查在调试器中，某些数据，并可以帮助您进入意外的函数时您单步执行代码。 代码的行为完全相同，但调试器演示文稿可以是非常容易引起混淆。 因此，不建议你使用 **/opt: icf**调试生成中除非较小的代码的好处能弥补这些不足。

> [!NOTE]
> 因为 **/opt: icf**可能会导致相同的地址分配给不同的函数或只读数据成员 (即**const**变量使用编译时 **/Gy**)，它可能会中断依赖于函数或只读数据成员的唯一地址的程序。 有关详细信息，请参阅 [/Gy （启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md)。

**LBR** &AMP;#124; **NOLBR**

**/OPT:LBR**并 **/OPT:NOLBR**选项仅适用于 ARM 二进制文件。 由于某些 ARM 处理器分支指令的范围有限，因此如果链接器检测到跳转的地址超出范围，它就会将分支指令的目标地址替换成包含指向实际目标的分支指令的代码“岛”的地址。 可以使用 **/OPT:LBR**来优化对长分支指令的检测和中间代码岛，若要最大程度减少总体代码大小的布局。 **/OPT:NOLBR**指示链接器生成代码岛的长分支指令，因为其出现，而不进行优化。

默认情况下 **/OPT:LBR**时未启用增量链接，设置选项。 如果希望非增量链接而不是长分支优化，指定 **/OPT:NOLBR**。 **/OPT:LBR**选项禁用增量链接。

## <a name="remarks"></a>备注

如果使用在命令行，链接器将默认为**ICF，/opt: ref LBR**。 如果 **/debug**指定，默认值为**NOICR，/opt: noref NOLBR**。

**/Opt**优化通常减少映像大小并加快程序速度。 这些改进可以在是很明显较大的程序，这就是为什么它们对于零售版本的默认情况下启用。

链接器优化需要额外的时间，但优化的代码也节省了时间时链接器具有更少的重定位，若要修复，并创建较小的最终图像，并且它将保存时，它具有较少的调试信息来处理和写入 PDB 的更多时间。 启用优化时，它可以生成更快的链接时总体而言，因为在分析中的小额外成本可能会超过由链接器中的节省经过较小的二进制文件的时间偏移量。

**/Opt**变量可以指定在一起，以逗号隔开。 而不是，如 **/opt: ref /OPT:NOICF**，可以指定 **/opt: ref、 NOICF**。

可以使用[/verbose](../../build/reference/verbose-print-progress-messages.md)链接器选项以查看通过删除的函数的 **/opt: ref**和通过折叠函数 **/opt: icf**。

**/Opt**通常将其自变量设置为使用创建的项目**新项目**对话框在 Visual Studio IDE 中，并通常具有不同的值，用于调试和发布配置。 如果未不设置任何值，为你的项目中的这些链接器选项，您可能会收到项目默认设置，可以不同于在命令行链接器将使用的默认值。

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

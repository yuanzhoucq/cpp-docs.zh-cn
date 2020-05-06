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
ms.openlocfilehash: 5c0ab3579fcb9633c435305a8b02b0c3f73d7a6f
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825699"
---
# <a name="opt-optimizations"></a>/OPT（优化）

控制 LINK 在生成期间执行的优化。

## <a name="syntax"></a>语法

> **/OPT：**{**REF** | **NOREF**} \
> **/Opt：**{**ICF**[**=**_迭代_] |**NOICF**}\
> **/OPT：**{**LBR** | **NOLBR**}

## <a name="arguments"></a>参数

**引用**&#124; **NOREF**

**/Opt： REF**消除了从未引用的函数和数据;**/Opt： NOREF**保留从未引用的函数和数据。

启用/OPT： REF 后，LINK 将删除未引用的打包函数和数据（称为*comdat*）。 此优化称为可传递的 COMDAT 消除。 **/Opt： REF**选项还禁用增量链接。

在类声明中定义的内联函数和成员函数始终是 Comdat 的。 如果使用[/gy](gy-enable-function-level-linking.md)选项编译对象文件中的所有函数，则会将其转换为 comdat。 若要将**const**数据放置在 comdat 中，必须使用`__declspec(selectany)`来声明它。 有关如何指定删除或折叠数据的信息，请参阅[selectany](../../cpp/selectany.md)。

默认情况下，如果指定了 **/opt： NOREF**或[/debug](debug-generate-debug-info.md) ，则链接器将启用 **/opt： REF** 。 若要替代此默认设置并保留程序中的未引用 Comdat，请指定 **/opt： NOREF**。 可以使用[/INCLUDE](include-force-symbol-references.md)选项重写特定符号的移除。

如果指定了[/debug](debug-generate-debug-info.md) ，则 **/opt**的默认值为**NOREF**，所有函数都保留在映像中。 若要重写此默认值并优化调试生成，请指定 **/opt： REF**。 这可以减少可执行文件的大小，也可以在调试版本中进行有用的优化。 建议你还在调试版本中指定 **/opt： NOICF**以保留相同的函数。 这样更容易读取堆栈跟踪以及在本应折叠在一起的函数中设置断点。

**ICF**\[ICF**=**_迭代_] &#124; **NOICF**

使用**ICF**\[**=**_迭代_] 执行相同的 COMDAT 折叠。 可以从链接器输出中删除冗余 COMDAT。 可选的*迭代*参数指定遍历符号以查找重复项的次数。 默认迭代次数为1。 附加的迭代可以找到更多前一次迭代中未通过折叠发现的重复项。

默认情况下，如果指定了 **/opt： NOICF**或[/debug](debug-generate-debug-info.md) ，则链接器将启用 **/opt： ICF** 。 若要重写此默认值，并在程序中阻止 Comdat 折叠，请指定 **/opt： NOICF**。

在调试版本中，必须显式指定 **/opt： ICF**才能启用 COMDAT 折叠。 但是，由于 **/opt： ICF**可以合并相同的数据或函数，因此它可以更改堆栈跟踪中出现的函数名称。 它还可能导致在某些函数中设置断点或在调试器中检查某些数据，并在单步执行代码时将您带到意外函数。 代码的行为是相同的，但调试器演示可能会很容易混淆。 因此，建议不要在调试版本中使用 **/opt： ICF** ，除非小型代码的优点超过了这些缺点。

> [!NOTE]
> 由于 **/opt： ICF**可能导致相同的地址分配给不同的函数或只读数据成员（即，使用 **/gy**编译时的**常量**变量），因此它可能会破坏依赖于函数或只读数据成员的唯一地址的程序。 有关详细信息，请参阅 [/Gy （启用函数级链接）](gy-enable-function-level-linking.md)。

**LBR** &#124; **NOLBR**

**/Opt： LBR**和 **/opt： NOLBR**选项仅适用于 ARM 二进制文件。 由于某些 ARM 处理器分支指令的范围有限，因此如果链接器检测到超出范围的地址，则会将分支指令的目标地址替换为代码 "岛" 的地址，该代码包含一个包含实际目标的分支指令。 可以使用 **/opt： LBR**来优化长分支指令的检测和中间代码岛的位置，以最大程度地减少总体代码大小。 **/Opt： NOLBR**指示链接器为遇到的长分支指令生成代码岛，但不进行优化。

默认情况下，当未启用增量链接时，将设置 **/opt： LBR**选项。 如果需要非增量链接而不是长分支优化，请指定 **/opt： NOLBR**。 **/Opt： LBR**选项禁用增量链接。

## <a name="remarks"></a>备注

当在命令行中使用链接器时，链接器默认为 **/opt： REF、ICF、LBR**。 如果指定了 **/debug** ，则默认值为 **/opt： NOREF、NOICF、NOLBR**。

**/Opt**优化通常会减小映像大小并提高程序速度。 这些改进在大型程序中可能非常重要，这就是在默认情况下为零售版本启用它们的原因。

链接器优化之前需要额外的时间，但优化后的代码还可以节省时间，因为链接器的重定位更少，无法修复并创建更小的最终映像，并且在处理和写入 PDB 的调试信息较少的情况下，它可节省更多的时间。 启用优化时，它可能会导致更快的链接时间，因为分析中的较小额外成本可能比通过链接器传递较小的二进制文件时节省的时间更多。

可以将 **/opt**参数一起指定，并用逗号分隔。 例如，可以指定 **/opt： ref、NOICF**，而不是 **/OPT： REF/opt： NOICF**。

您可以使用[/verbose](verbose-print-progress-messages.md)链接器选项查看 **/opt： REF**和由 **/opt： ICF**折叠的函数所删除的函数。

通常为使用 Visual Studio IDE 中的 "**新建项目**" 对话框创建的项目设置 **/opt**参数，对于 "调试" 和 "发布" 配置，通常具有不同的值。 如果你的项目中未设置这些链接器选项的值，则可能会获得项目默认值，该默认值可能与命令行中的链接器使用的默认值不同。

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 OPT:ICF 或 OPT:REF 链接器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性** > **链接器** > **优化**" 属性页。

1. 修改以下属性之一：

   - **启用 COMDAT 折叠**

   - **参考**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 OPT:LBR 链接器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性** > **链接器** > **命令行**" 属性页。

1. 在 "**其他选项**" 中输入选项：

   `/opt:lbr` 或 `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> 属性。

## <a name="see-also"></a>另请参阅

- [MSVC 链接器参考](linking.md)
- [MSVC 链接器选项](linker-options.md)

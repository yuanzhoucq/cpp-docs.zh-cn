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
ms.openlocfilehash: b25db4d6c260c3c6751de293aa2a82df8aa05e7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336226"
---
# <a name="opt-optimizations"></a>/OPT（优化）

控制 LINK 在生成期间执行的优化。

## <a name="syntax"></a>语法

> **/选择：**[**参考** | **NOREF**]<br/>
> **/OPT：**[**ICF**]**=**_迭代_|**NOICF**|<br/>
> **/OPT：**[**LBR** | **NOLBR**]

## <a name="arguments"></a>参数

**参考&#124;****诺夫雷**

**/OPT：REF**消除了从未引用的函数和数据;**/OPT：NOREF**保留从未引用的函数和数据。

启用 /OPT：REF 后，LINK 将删除未引用的打包函数和数据，称为*COMDAT。* 此优化称为可传递的 COMDAT 消除。 **/OPT：REF**选项还禁用增量链接。

在类声明中定义的内联函数和成员函数始终是 COMDAT。 如果使用[/Gy](gy-enable-function-level-linking.md)选项编译对象文件中的所有函数，则将其制作为 COMDAT。 要将**const**数据放在 COMDAT 中，必须使用`__declspec(selectany)`声明数据。 有关如何指定数据进行删除或折叠的信息，请参阅[selectany](../../cpp/selectany.md)。

默认情况下 **，/OPT：REF**由链接器启用，除非指定 **/OPT：NOREF**或[/DEBUG。](debug-generate-debug-info.md) 要覆盖此默认值并在程序中保留未引用的 COMDAT，请指定 **/OPT：NOREF**。 您可以使用[/INCLUDE](include-force-symbol-references.md)选项来覆盖特定符号的删除。

如果指定[/DEBUG，](debug-generate-debug-info.md)**则 /OPT**的默认值为**NOREF**，并且所有函数都保留在映像中。 要覆盖此默认值并优化调试生成，请指定 **/OPT：REF**。 这可以减小可执行文件的大小，即使在调试生成中也可以进行有用的优化。 我们建议您也指定 **/OPT：NOICF**以在调试生成中保留相同的函数。 这样更容易读取堆栈跟踪以及在本应折叠在一起的函数中设置断点。

**ICF**\[**=**_迭代_= &#124; **NOICF**

使用**ICF**\[**=**_迭代_= 执行相同的 COMDAT 折叠。 可以从链接器输出中删除冗余 COMDAT。 可选*迭代*参数指定遍历重复符号的次数。 默认迭代次数为 1。 附加的迭代可以找到更多前一次迭代中未通过折叠发现的重复项。

默认情况下 **，/OPT：ICF**由链接器启用，除非指定 **/OPT：NOICF**或[/DEBUG。](debug-generate-debug-info.md) 要覆盖此默认值并防止在程序中折叠 COMDAT，请指定 **/OPT：NOICF**。

在调试生成中，必须显式指定 **/OPT：ICF**才能启用 COMDAT 折叠。 但是，由于 **/OPT：ICF**可以合并相同的数据或函数，因此它可以更改堆栈跟踪中显示的函数名称。 它还会使无法在某些函数中设置断点或检查调试器中的某些数据，并且在单步执行代码时，可能会将您带入意外的函数。 代码的行为是相同的，但调试器表示可能非常混乱。 因此，我们不建议在调试生成中使用 **/OPT：ICF，** 除非较小的代码的优点大于这些缺点。

> [!NOTE]
> 因为 **/OPT：ICF**会导致将同一地址分配给不同的函数或只读数据成员（即，使用 **/Gy**编译时**的 const**变量），因此它可以破坏依赖于函数的唯一地址或只读数据成员的程序。 有关详细信息，请参阅 [/Gy （启用函数级链接）](gy-enable-function-level-linking.md)。

**LBR** &#124; **NOLBR**

**/OPT：LBR**和 **/OPT：NOLBR**选项仅适用于 ARM 二进制文件。 由于某些 ARM 处理器分支指令的范围有限，因此如果链接器检测到跳转到范围外的地址，它将分支指令的目标地址替换为包含指向实际目标的分支指令的代码"island"的地址。 您可以使用 **/OPT：LBR**优化长分支指令的检测和中间代码孤岛的位置，以最小化总体代码大小。 **/OPT：NOLBR**指示链接器在遇到长分支指令时生成代码孤岛，而不进行优化。

默认情况下，如果未启用增量链接，则设置 **/OPT：LBR**选项。 如果需要非增量链接，但分支优化时间不长，请指定 **/OPT：NOLBR**。 **/OPT：LBR**选项禁用增量链接。

## <a name="remarks"></a>备注

在命令行使用时，链接器默认为 **/OPT：REF、ICF、LBR**。 如果指定 **/DEBUG，** 则默认值为 **/OPT：NOREF、NOICF、NOLBR**。

**/OPT**优化通常会减小图像大小并提高程序速度。 这些改进在较大的程序中可能很大，这就是为什么默认情况下为零售生成启用这些改进的原因。

Linker 优化确实需要额外的时间，但优化的代码也会节省时间，当链接器的重新定位较少以进行修复并创建较小的最终映像时，当它具有较少的调试信息来处理并写入 PDB 时，它可以节省更多的时间。 启用优化后，它可能会导致整体链接时间更快，因为分析中的少量额外成本可能会因链接器通过较小的二进制文件所节省的时间而抵消。

**/OPT**参数可以一起指定，用逗号分隔。 例如，您可以指定 **/OPT：REF，而不是** **：REF /OPT：NOICF。**

您可以使用[/VERBOSE](verbose-print-progress-messages.md)链接器选项查看 **/OPT：REF**删除的函数以及 **/OPT：ICF**折叠的函数。

**/OPT**参数通常设置为使用 Visual Studio IDE 中的 **"新项目**"对话框创建的项目，并且通常具有不同的调试和发布配置值。 如果项目中未为这些链接器选项设置任何值，则您可能会获取项目默认值，这可能与命令行链接器使用的默认值不同。

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 OPT:ICF 或 OPT:REF 链接器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **优化**属性页面。

1. 修改以下属性之一：

   - **启用 COMDAT 折叠**

   - **reference**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 OPT:LBR 链接器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 在 **"其他选项**" 中输入选项 ：

   `/opt:lbr` 或 `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> 属性。

## <a name="see-also"></a>另请参阅

- [MSVC 链接器参考](linking.md)
- [MSVC 链接器选项](linker-options.md)

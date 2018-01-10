---
title: "-OPT （优化） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
dev_langs: C++
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86427dbf1ac6c3404daa36d2e02786aa80ed6453
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="opt-optimizations"></a>/OPT（优化）
控制 LINK 在生成期间执行的优化。  
  
## <a name="syntax"></a>语法  
  
```  
/OPT:{REF | NOREF}  
/OPT:{ICF[=iterations] | NOICF}  
/OPT:{LBR | NOLBR}  
```  
  
## <a name="arguments"></a>自变量  
 **REF** &#124;**NOREF**  
 **/Opt: ref**消除函数和从未引用; 的数据**/OPT:NOREF**保留函数和从未引用的数据。  
  
 当启用 /OFT:REF 时，LINK 会移除未引用的已打包函数和数据。 如果通过使用编译后，对象将包含打包的函数和数据 (Comdat) [/Gy](../../build/reference/gy-enable-function-level-linking.md)选项。 此优化称为可传递的 COMDAT 消除。 默认情况下， **/opt: ref**在非调试生成中启用。 若要覆盖此默认设置，并在程序中保留未引用的 Comdat，请指定**/OPT:NOREF**。 你可以使用[/包括](../../build/reference/include-force-symbol-references.md)选项重写特定符号的删除。  
  
 当**/opt: ref**显式或默认情况下，受限形式的启用**/opt: icf**已启用，仅会折叠相同的函数。 如果你想**/opt: ref**但不是**/opt: icf**，您必须指定**/opt: ref、 NOICF**或**/OPT:NOICF**。  
  
 如果[/调试](../../build/reference/debug-generate-debug-info.md)指定，则默认为**/选择**是**NOREF**，和所有函数都保留在映像中。 若要覆盖此默认设置，并优化调试生成，指定**/opt: ref**。 因为**/opt: ref**意味着**/opt: icf**，我们建议你还指定**/OPT:NOICF**保留在调试生成中相同的函数。 这样更容易读取堆栈跟踪以及在本应折叠在一起的函数中设置断点。 **/Opt: ref**选项禁用增量链接。  
  
 你必须显式标记`const`数据为 COMDAT; 使用[__declspec （selectany)](../../cpp/selectany.md)。  
  
 指定**/opt: icf**不会启用**/opt: ref**选项。  
  
 **ICF [=** `iterations` **] &#124;NOICF**   
 使用**/opt: icf [=**`iterations`**]**执行相同的 COMDAT 折叠。 可以从链接器输出中删除冗余 COMDAT。 可选 `iterations` 参数指定遍历符号以查找重复项的次数。 默认迭代次数是两次。 附加的迭代可以找到更多前一次迭代中未通过折叠发现的重复项。  
  
 链接器的行为方式不同时**/opt: ref**指定-和**ICF**实际上是默认情况下 — 不时**/opt: ref、 ICF**显式指定。 形式**ICF**启用了**/opt: ref**单独不折叠只读数据-这包括.rdata、.pdata 和.xdata。 因此，为 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 生成映像时将折叠较少的函数，因为这些模块中的函数更依赖于只读数据（例如 .pdata 和 .xdata）。 若要获取完整**ICF**折叠行为，请显式指定**/opt: icf**。  
  
 若要在 Comdat 中放置函数，请使用**/Gy**编译器选项; 若要放置`const`数据，你将其声明`__declspec(selectany)`。 有关如何指定折叠的数据的信息，请参阅[selectany](../../cpp/selectany.md)。  
  
 默认情况下， **ICF**位于如果**REF**上。 如果重写此默认**REF**是指定，使用**NOICF**。 当**/opt: ref**未指定在调试版本中，则必须显式指定**/opt: icf**以启用 COMDAT 折叠。 但是，因为**/opt: icf**可以合并相同的数据或函数，它可以更改显示在堆栈跟踪中的函数名。 它还能使你无法在某些函数中设置断点或在调试器中检查某些数据，并让你在单步执行代码时进入意外的函数。 因此，不建议你使用**/opt: icf**在调试生成中除非较小的代码的好处能弥补这些不足。  
  
> [!NOTE]
>  因为**/opt: icf**可以使同一地址分配给不同的函数或只读数据成员 (`const`变量使用编译的**/Gy**)，它能中断依赖于的程序对于函数或只读数据成员的唯一地址。 有关详细信息，请参阅 [/Gy （启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md)。  
  
 **LBR** &#124;**NOLBR**  
 **/Opt: lbr**和**/OPT:NOLBR**选项仅适用于 ARM 二进制文件。 由于某些 ARM 处理器分支指令的范围有限，因此如果链接器检测到跳转的地址超出范围，它就会将分支指令的目标地址替换成包含指向实际目标的分支指令的代码“岛”的地址。 你可以使用**/opt: lbr**来优化对长分支指令的检测和中间代码岛，若要最大程度减少总体代码大小的布局。 **/OPT:NOLBR**指示链接器生成的长分支指令的代码岛，为遇到，但不进行优化。  
  
 默认情况下， **/opt: lbr**增量链接未启用时，设置选项。 如果需要非增量链接而不是长分支优化，请指定**/OPT:NOLBR**。 **/Opt: lbr**选项禁用增量链接。  
  
## <a name="remarks"></a>备注  
 优化通常是以增加链接时间为代价，减小映像大小并加快程序速度。  
  
 你可以使用[/详细](../../build/reference/verbose-print-progress-messages.md)选项以查看通过删除的函数**/opt: ref**和通过折叠函数**/opt: icf**。  
  
### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 OPT:ICF 或 OPT:REF 链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在左窗格中，展开**配置属性**，**链接器**，**优化**。  
  
3.  修改以下属性之一：  
  
    -   **启用 COMDAT 折叠**  
  
    -   **参考资料**  
  
### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 OPT:LBR 链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**链接器**文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  输入中的选项**其他选项**:  
  
     `/opt:lbr`  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> 属性。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)
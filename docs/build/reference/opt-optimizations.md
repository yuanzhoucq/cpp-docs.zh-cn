---
title: "/OPT（优化） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.OptimizeReferences"
  - "/opt"
  - "VC.Project.VCLinkerTool.OptimizeForWindows98"
  - "VC.Project.VCLinkerTool.EnableCOMDATFolding"
  - "VC.Project.VCLinkerTool.OptimizeFolding"
  - "VC.Project.VCLinkerTool.FoldingIterations"
  - "VC.Project.VCLinkerTool.OptimizeFoldingIterations"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/OPT 链接器选项"
  - "LINK 工具 [C++], 控制优化"
  - "链接器 [C++], 优化"
  - "OPT 链接器选项"
  - "-OPT 链接器选项"
  - "优化, 链接器"
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# /OPT（优化）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制 LINK 在生成期间执行的优化。  
  
## 语法  
  
```  
/OPT:{REF | NOREF}  
/OPT:{ICF[=iterations] | NOICF}  
/OPT:{LBR | NOLBR}  
```  
  
## 参数  
 **REF** &#124; **NOREF**  
 **\/OPT:REF** 清除从未引用的函数和数据；**\/OPT:NOREF** 保留从未引用的函数和数据。  
  
 当启用 \/OFT:REF 时，LINK 会移除未引用的已打包函数和数据。  如果对象已经用 [\/Gy](../../build/reference/gy-enable-function-level-linking.md) 选项编译过，它将包含打包的函数和数据 \(COMDAT\)。  此优化称为可传递的 COMDAT 消除。  默认情况下，在非调试生成中启用 **\/OPT:REF**。  若要重写此默认值并在程序中保留未引用的 COMDAT，请指定 **\/OPT:NOREF**。  可以使用 [\/INCLUDE](../../build/reference/include-force-symbol-references.md) 选项重写特定符号的移除。  
  
 在显式或默认启用 **\/OPT:REF** 后，将启用受限形式的 **\/OPT:ICF**（仅会折叠相同的函数）。  如果需要 **\/OPT:REF** 而不是 **\/OPT:ICF**，则必须指定 **\/OPT:REF,NOICF** 或 **\/OPT:NOICF**。  
  
 如果指定了 [\/DEBUG](../../build/reference/debug-generate-debug-info.md)，则 **\/OPT** 的默认项是 **NOREF**，而且所有函数都保留在映像中。  若要重写此默认项并优化调试生成，请指定 **\/OPT:REF**。  由于 **\/OPT:REF** 隐式使用 **\/OPT:ICF**，建议你同时指定 **\/OPT:NOICF** 以在调试生成中保留相同的函数。  这样更容易读取堆栈跟踪以及在本应折叠在一起的函数中设置断点。  **\/OPT:REF** 选项禁用增量链接。  
  
 你必须将 `const` 数据显式标记为 COMDAT；使用 [\_\_declspec\(selectany\)](../../cpp/selectany.md)。  
  
 指定 **\/OPT:ICF** 不启用 **\/OPT:REF** 选项。  
  
 **ICF\[\=**  `iterations` **\] &#124; NOICF**  
 使用 **\/OPT:ICF\[\=**`iterations`**\]** 执行相同的 COMDAT 折叠。  可以从链接器输出中删除冗余 COMDAT。  可选 `iterations` 参数指定遍历符号以查找重复项的次数。  默认迭代次数是两次。  附加的迭代可以找到更多前一次迭代中未通过折叠发现的重复项。  
  
 指定 **\/OPT:REF** 并且 **ICF** 默认为有效时的链接器行为方式与显式指定 **\/OPT:REF,ICF** 时的行为方式不同。  单独使用 **\/OPT:REF** 启用的 **ICF** 的窗体不折叠只读数据（包括 .rdata、.pdata 和 .xdata）。  因此，为 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 生成映像时将折叠较少的函数，因为这些模块中的函数更依赖于只读数据（例如 .pdata 和 .xdata）。  若要获取完整的 **ICF** 折叠行为，请显式指定 **\/OPT:ICF**。  
  
 若要在 COMDAT 中放置函数，请使用 **\/Gy** 编译器选项；若要放置 `const` 数据，请将其声明为 `__declspec(selectany)`。  有关如何指定用于折叠的数据的详细信息，请参阅 [selectany](../../cpp/selectany.md)。  
  
 默认情况下，如果 **REF** 处于打开状态，则 **ICF** 处于打开状态。  若要重写此默认值，当指定 **REF** 时，请使用 **NOICF**。  当未在调试生成中指定 **\/OPT:ICF** 时，你必须显式指定 **\/OPT:REF** 以启用 COMDAT 折叠。  但是，由于 **\/OPT:ICF** 能合并相同的数据或函数，因此它也能更改显示在堆栈跟踪中的函数名。  它还能使你无法在某些函数中设置断点或在调试器中检查某些数据，并让你在单步执行代码时进入意外的函数。  因此，建议不在调试生成中使用 **\/OPT:ICF**，除非较小的代码的好处能弥补这些不足。  
  
> [!NOTE]
>  由于 **\/OPT:ICF** 可以使同一地址分配给不同的函数或只读数据成员（使用 **\/Gy** 编译的 `const` 变量），因此它能中断依赖于函数或只读数据成员的唯一地址的程序。  有关详细信息，请参阅 [\/Gy（启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md)。  
  
 **LBR** &#124; **NOLBR**  
 **\/OPT:LBR** 和 **\/OPT:NOLBR** 选项仅适用于 ARM 二进制文件。  由于某些 ARM 处理器分支指令的范围有限，因此如果链接器检测到跳转的地址超出范围，它就会将分支指令的目标地址替换成包含指向实际目标的分支指令的代码“岛”的地址。  可使用 **\/OPT:LBR** 来优化对长分支指令的检测和中间代码岛的布局，以便最大程度减少总体代码大小。  **\/OPT:NOLBR** 指示链接器为遇到的长分支指令生成代码岛，但不进行优化。  
  
 默认情况下，增量链接未启用时会设置 **\/OPT:LBR** 选项。  如果需要非增量链接而不是长分支优化，请指定 **\/OPT:NOLBR**。  **\/OPT:LBR** 选项禁用增量链接。  
  
## 备注  
 优化通常是以增加链接时间为代价，减小映像大小并加快程序速度。  
  
 你可使用 [\/VERBOSE](../../build/reference/verbose-print-progress-messages.md) 选项查看由 **\/OPT:REF** 移除的函数和由 **\/OPT:ICF** 折叠的函数。  
  
### 在 Visual Studio 开发环境中设置 OPT:ICF 或 OPT:REF 链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在左窗格中，展开**“配置属性”**、**“链接器”**和**“优化”**。  
  
3.  修改以下属性之一：  
  
    -   **启用 COMDAT 折叠**  
  
    -   **引用**  
  
### 在 Visual Studio 开发环境中设置 OPT:LBR 链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **Linker** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  在“附加选项”中输入选项：  
  
     `/opt:lbr`  
  
### 以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> 属性。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)
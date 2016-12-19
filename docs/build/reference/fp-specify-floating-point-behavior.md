---
title: "/fp（指定浮点行为） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.floatingPointModel"
  - "VC.Project.VCCLWCECompilerTool.FloatingPointExceptions"
  - "/fp"
  - "VC.Project.VCCLWCECompilerTool.floatingPointModel"
  - "VC.Project.VCCLCompilerTool.FloatingPointExceptions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/fp 编译器选项 [C++]"
  - "-fp 编译器选项 [C++]"
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /fp（指定浮点行为）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定源代码文件中的浮点行为。  
  
## 语法  
  
```  
/fp:[precise | except[-] | fast | strict ]  
```  
  
## Flags  
 **precise**  
 默认值。  
  
 通过禁用可更改浮点计算精度的优化，可提高等式和不等式的浮点测试的一致性。（若要严格遵守 ANSI，则必须保持特定的精度。）默认情况下，在针对 x86 体系结构的代码中，编译器使用协处理器的 80 位寄存器保存浮点计算的中间结果。  这提高了程序速度，并减小了程序大小。  但是，由于计算涉及浮点数据类型（在内存中用少于 80 位表示），在冗长计算中进位多余精度位（80 位减去较小浮点型的位数）会产生不一致的结果。  
  
 在 x86 处理器上使用 **\/fp:precise** 时，编译器将对 `float` 类型的变量执行舍入，使其达到赋值、强制转换以及将参数传递给函数时所需的准确精度。  这种舍入保证了数据不会保留任何超出其类型的容量的有效数字。  与不使用 **\/fp:precise** 编译的程序相比，使用 **\/fp:precise** 编译的程序可能更大，运行速度更慢。  **\/fp:precise** 会禁用内部函数，转而使用标准运行库例程。  有关详细信息，请参阅 [\/Oi（生成内部函数）](../../build/reference/oi-generate-intrinsic-functions.md)。  
  
 以下浮点行为用 **\/fp:precise** 实现：  
  
-   缩写，即，使用在末尾只进行一次舍入的复合运算来替换多个运算。  
  
-   不允许使用对特殊值（NaN、\+infinity、\-infinity、\+0、\-0）无效的表达式优化。  出于各种原因，优化 x\-x \=\> 0、x\*0 \=\> 0、x\-0 \=\> x、x\+0 \=\> x 和 0\-x \=\> \-x 无效。（请参见 IEEE 754 和 C99 标准。）  
  
-   编译器会正确地处理涉及 NaN 的比较。  例如，如果 `x` 为 NaN 并且涉及 NaN 的有序比较引发了异常，则 x \!\= x 的计算结果为 **true**。  
  
-   表达式计算在 C99 FLT\_EVAL\_METHOD\=2 后面进行，但以下情况除外：当你为 x86 处理器进行编程时，由于 FPU 设置为 53 位精度，因此被视为长双精度。  
  
-   乘数正好是 1.0 的乘法将转换为使用另一乘数。  x\*y\*1.0 将转换为 x\*y。  同样，x\*1.0\*y 将转换为 x\*y。  
  
-   除数正好是 1.0 的除法将转换为使用被除数。  x\*y\/1.0 将转换为 x\*y。  同样，x\/1.0\*y 将转换为 x\*y。  
  
 在打开 [fenv\_access](../../preprocessor/fenv-access.md) 时使用 **\/fp:precise** 将禁用某些优化，如浮点表达式的编译时计算。  例如，如果使用 [\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 更改舍入模式，并且编译器执行浮点计算，则指定的舍入模式将无效，除非打开 `fenv_access`。  
  
 **\/fp:precise** 替换了 **\/Op** 编译器选项。  
  
 **fast**  
 在大多数情况下，通过放松优化浮点运算的规则可创建最快的代码。  这使编译器能够优化浮点代码的速度，但会牺牲准确性和正确性。  如果指定 **\/fp:fast**，则编译器可能在赋值语句、类型强制转换或函数调用时无法执行舍入，并且可能无法执行中间表达式的舍入。  编译器可能对运算进行重新排序或执行代数转换（例如，通过遵循关联和分布式规则）而不考虑对有限的精度结果的效果。  编译器可能将运算和操作数更改为单精度而不遵循 C\+\+ 类型提升规则。  始终启用浮点特定缩写优化（打开 [fp\_contract](../../preprocessor/fp-contract.md)）。  始终禁用浮点异常和 FPU 环境访问（隐式使用 **\/fp:except\-** 并关闭 [fenv\_access](../../preprocessor/fenv-access.md)）。  
  
 **\/fp:fast** 不能与 **\/fp:strict** 或 **\/fp:precise** 一起使用。  使用命令行中指定的最后一个选项。  同时指定 **\/fp:fast** 和 **\/fp:except** 将产生编译器错误。  
  
 指定 [\/Za、\/Ze（禁用语言扩展）](../../build/reference/za-ze-disable-language-extensions.md)（ANSI 兼容性）和 **\/fp:fast** 可能导致意外行为。  例如，单精度浮点运算可能不会舍入为单精度。  
  
 **except\[\-\]**  
 可靠的浮点异常模型。  异常在触发后立即引发。  默认情况下关闭此选项。  将减号追加到此选项将显式禁用它。  
  
 **strict**  
 最严格的浮点模型。  **\/fp:strict** 会导致关闭 [fp\_contract](../../preprocessor/fp-contract.md)，并且打开 [fenv\_access](../../preprocessor/fenv-access.md)。  **\/fp:except** 是隐式使用的，并且可以通过显式指定 **\/fp:except\-** 来禁用。  与 **\/fp:except\-** 一起使用时，**\/fp:strict** 将强制执行严格的浮点语义，但不考虑异常事件。  
  
## 备注  
 在同一编译中可指定多个 **\/fp** 选项。  
  
 要通过函数控制浮点行为，请参见[浮点控制](../../preprocessor/float-control.md)杂注。  这会重写 **\/fp** 编译器设置。  建议你将保存并还原本地浮点业行为作为良好工程做法：  
  
```css  
#pragma float_control(precise, on, push)  
// Code that uses /fp:precise mode  
#pragma float_control(pop)  
```  
  
 与 **\/fp:strict**、**\/fp:except**（及其相应的杂注）和 `fp_contract` 杂注相关的大多数浮点优化是依赖于计算机的。  **\/fp:strict** 和 **\/fp:except** 与 **\/clr** 不兼容。  
  
 **\/fp:precise** 应能满足应用程序的大多数浮点要求。  可以使用 **\/fp:except** 和 **\/fp:strict**，但性能可能会有所下降。  如果性能最重要，则要考虑是否使用 **\/fp:fast**。  
  
 **\/fp:strict**、**\/fp:fast** 和 **\/fp:precise** 是精度（正确性）模式。  每次仅一个有效。  如果同时指定了 **\/fp:strict** 和 **\/fp:precise**，编译器将使用它最后处理的那一项。  不能同时指定 **\/fp:strict** 和 **\/fp:fast**。  
  
 有关详细信息，请参阅 [Microsoft Visual C\+\+ 浮点优化](http://msdn.microsoft.com/library/aa289157.aspx)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“C\/C\+\+”**节点。  
  
4.  选择**“代码生成”**属性页。  
  
5.  修改**“浮点模型”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [Microsoft Visual C\+\+ 浮点优化](http://msdn.microsoft.com/library/aa289157.aspx)
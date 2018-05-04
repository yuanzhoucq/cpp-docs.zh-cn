---
title: -fp （指定浮点行为） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
dev_langs:
- C++
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af796b7143b3600130e9405782d618a5960d22fc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fp-specify-floating-point-behavior"></a>/fp（指定浮点行为）
指定源代码文件中的浮点行为。  
  
## <a name="syntax"></a>语法  
  
```  
/fp:[precise | except[-] | fast | strict ]  
```  
  
## <a name="flags"></a>Flags  
 **精确**  
 默认值。  
  
 通过禁用可更改浮点计算精度的优化，可提高等式和不等式的浮点测试的一致性。 （若要严格遵守 ANSI，则必须保持特定的精度。）默认情况下，在针对 x86 体系结构的代码中，编译器使用协处理器的 80 位寄存器保存浮点计算的中间结果。 这提高了程序速度，并减小了程序大小。 但是，由于计算涉及浮点数据类型（在内存中用少于 80 位表示），在冗长计算中进位多余精度位（80 位减去较小浮点型的位数）会产生不一致的结果。  
  
 与 **/fp： 精确**在 x86 处理器，编译器将执行类型的变量舍入`float`到分配、 强制转换以及时传递给函数的参数的正确精度。 这种舍入保证了数据不会保留任何超出其类型的容量的有效数字。 程序编译时会出现 **/fp： 精确**更慢且大于不可以是 **/fp： 精确**。 **/fp： 精确**会禁用内部函数; 例程而使用标准运行时库。 有关详细信息，请参阅 [/Oi （生成内部函数）](../../build/reference/oi-generate-intrinsic-functions.md)。  
  
 使用启用以下浮点行为 **/fp： 精确**:  
  
-   缩写，即，使用在末尾只进行一次舍入的复合运算来替换多个运算。  
  
-   不允许使用对特殊值（NaN、+infinity、-infinity、+0、-0）无效的表达式优化。 优化 x-x = > 0，x * 0 = > 0，x-0 = > x、 x + 0 = > x 和 0-x = >-x 是无效的由于各种原因。 （请参见 IEEE 754 和 C99 标准。）  
  
-   编译器会正确地处理涉及 NaN 的比较。 例如，x ！ = x 计算到**true**如果`x`为 NaN 和涉及 NaN 的有序的比较引发异常。  
  
-   表达式计算在 C99 FLT_EVAL_METHOD=2 后面进行，但以下情况除外：当你为 x86 处理器进行编程时，由于 FPU 设置为 53 位精度，因此被视为长双精度。  
  
-   乘数正好是 1.0 的乘法将转换为使用另一乘数。 x * y\*1.0 将转换成 x\*y。 同样，x\*1.0\*y 将转换成 x\*y。  
  
-   除数正好是 1.0 的除法将转换为使用被除数。 x * y/1.0 将转换成 x\*y。 同样，x / 1.0\*y 将转换成 x\*y。  
  
 使用 **/fp： 精确**时[fenv_access](../../preprocessor/fenv-access.md)位于禁用如浮点表达式的编译时计算的优化。 例如，如果你使用[_control87、 _controlfp、 \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)更改舍入模式和编译器执行浮点计算时，你指定的舍入模式不会生效除非`fenv_access`为 ON。  
  
 **/fp： 精确**替换 **/Op**编译器选项。  
  
 **快速**  
 在大多数情况下，通过放松优化浮点运算的规则可创建最快的代码。 这使编译器能够优化浮点代码的速度，但会牺牲准确性和正确性。 当 **/fp:fast**指定，编译器可能不舍入运算正确在赋值语句、 类型强制转换或函数调用，并可能无法执行中间表达式的舍入。 编译器可能对运算进行重新排序或执行代数转换（例如，通过遵循关联和分布式规则）而不考虑对有限的精度结果的效果。 编译器可能将运算和操作数更改为单精度而不遵循 C++ 类型提升规则。 始终启用 point 特定浮点缩写式优化 ([fp_contract](../../preprocessor/fp-contract.md)为 ON)。 浮点异常和 FPU 环境访问将被禁用 (**/fp： 除-** 会进行隐式和[fenv_access](../../preprocessor/fenv-access.md)为 OFF)。  
  
 **/fp:fast**不能与使用 **/fp: strict**或 **/fp： 精确**。 使用命令行中指定的最后一个选项。 指定这两个 **/fp:fast**和 **/fp： 除**生成一个编译器错误。  
  
 指定[/Za、 /Ze （禁用语言扩展）](../../build/reference/za-ze-disable-language-extensions.md) （ANSI 兼容性） 和 **/fp:fast**可能导致意外的行为。 例如，单精度浮点运算可能不会舍入为单精度。  
  
 **除 [-]**  
 可靠的浮点异常模型。 异常在触发后立即引发。 默认情况下关闭此选项。 将减号追加到此选项将显式禁用它。  
  
 **严格**  
 最严格的浮点模型。 **/fp: strict**导致[fp_contract](../../preprocessor/fp-contract.md)为 OFF 和[fenv_access](../../preprocessor/fenv-access.md)为 ON。 **/fp： 除**会进行隐式，可通过显式指定禁用 **/fp： 除-**。 一起使用时 **/fp： 除-**， **/fp: strict**强制执行严格的浮点语义但不考虑异常事件。  
  
## <a name="remarks"></a>备注  
 多个 **/fp**同一编译中，可以指定选项。  
  
 若要通过函数控制浮点行为，请参阅[float_control](../../preprocessor/float-control.md)杂注。 此设置将替代 **/fp**编译器设置。 建议你将保存并还原本地浮点业行为作为良好工程做法：  
  
```cpp  
#pragma float_control(precise, on, push)  
// Code that uses /fp:precise mode  
#pragma float_control(pop)  
```  
  
 与相关的大多数浮点优化 **/fp: strict**， **/fp： 除**（和其相应的杂注），和`fp_contract`杂注是依赖于计算机的。 **/fp: strict**和 **/fp： 除**与不兼容 **/clr**。  
  
 **/fp： 精确**应能满足大多数应用程序的浮点要求。 你可以使用 **/fp： 除**和 **/fp: strict**，但可能存在性能有所下降。 如果性能最重要，请考虑是否使用 **/fp:fast**。  
  
 **/fp: strict**， **/fp:fast**，和 **/fp： 精确**精度 （正确性） 模式。 每次仅一个有效。 如果这两个 **/fp: strict**和 **/fp： 精确**指定，编译器将使用它最后处理的那一个。 同时 **/fp: strict**和 **/fp:fast**不能指定。  
  
 有关详细信息，请参阅[Microsoft Visual c + + 浮点优化](http://msdn.microsoft.com/library/aa289157.aspx)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  展开**C/c + +** 节点。  
  
4.  选择**代码生成**属性页。  
  
5.  修改**浮点模型**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [Microsoft Visual c + + 浮点点优化](http://msdn.microsoft.com/library/aa289157.aspx)
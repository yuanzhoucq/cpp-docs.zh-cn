---
title: "-Gd，-Gr，-Gv，-Gz （调用约定） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /gr
- /Gv
- /gz
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
dev_langs:
- C++
helpviewer_keywords:
- -Gd compiler option [C++]
- -Gv compiler option [C++]
- /Gv compiler option [C++]
- -Gr compiler option [C++]
- Gd compiler option [C++]
- Gr compiler option [C++]
- /Gz compiler option [C++]
- -Gz compiler option [C++]
- /Gd compiler option [C++]
- Gz compiler option [C++]
- Gv compiler option [C++]
- /Gr compiler option [C++]
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 26e88abf30c0f67fe5b104d560c40dd2adc57752
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd、/Gr、/Gv、/Gz（调用约定）
这些选项用于确定在哪一个函数自变量推送到堆栈，是否调用方函数或调用的函数自变量从堆栈中移除该调用，末尾的顺序，编译器用来标识名称修饰约定各个函数。  
  
## <a name="syntax"></a>语法  
  
```  
/Gd  
/Gr  
/Gv  
/Gz  
```  
  
## <a name="remarks"></a>备注  
 **/Gd**，默认设置，指定[__cdecl](../../cpp/cdecl.md)除 c + + 成员以外的所有函数都调用约定函数和标记的函数[__stdcall](../../cpp/stdcall.md)， [__fastcall](../../cpp/fastcall.md)，或[__vectorcall](../../cpp/vectorcall.md)。  
  
 **/Gr**指定`__fastcall`除 c + + 成员函数以外的所有函数的调用约定，函数名为`main`，和标记的函数`__cdecl`， `__stdcall`，或`__vectorcall`。 所有`__fastcall`函数必须具有原型。 此调用约定选项仅适用于面向 x86、 的编译器和面向其他体系结构的编译器忽略。  
  
 **/Gz**指定`__stdcall`除 c + + 成员函数以外的所有函数的调用约定，函数名为`main`，和标记的函数`__cdecl`， `__fastcall`，或`__vectorcall`。 所有`__stdcall`函数必须具有原型。 此调用约定选项仅适用于面向 x86、 的编译器和面向其他体系结构的编译器忽略。  
  
 **/Gv**指定`__vectorcall`除 c + + 成员函数以外的所有函数的调用约定，名为的 main 的函数、 函数与`vararg`变量自变量列表或函数标记有一个冲突的`__cdecl`，`__stdcall`，或`__fastcall`属性。 此调用约定仅提供支持 /arch:SSE2 的 x86 和 x64 体系结构和更高版本，并且由面向 ARM 体系结构的编译器忽略。  
  
 采用数量可变的自变量的函数必须标记`__cdecl`。  
  
 **/Gd**， **/Gr**， **/Gv**和**/Gz**与不兼容[/clr: safe](../../build/reference/clr-common-language-runtime-compilation.md)或**/clr: pure**. **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
> [!NOTE]
>  默认情况下，针对 x86 处理器上，c + + 成员函数使用[__thiscall](../../cpp/thiscall.md)。  
  
 适用于所有处理器，显式标记为成员函数`__cdecl`， `__fastcall`， `__vectorcall`，或`__stdcall`使用指定的调用约定，如果它不在该体系结构忽略。 成员函数采用数目可变的自变量始终使用`__cdecl`调用约定。  
  
 这些编译器选项不起作用的 c + + 方法和函数名称修饰。 除非声明为`extern "C"`，c + + 方法和函数使用不同的修饰名称的方案。 有关详细信息，请参阅[修饰名](../../build/reference/decorated-names.md)。  
  
 有关调用约定的详细信息，请参阅[调用约定](../../cpp/calling-conventions.md)。  
  
## <a name="cdecl-specifics"></a>__cdecl 细节  
 在 x86 处理器，所有函数参数都传递到堆栈上从右向左。 在 ARM 和 x64 体系结构，某些参数通过寄存器传递和从右到左，在堆栈上的其余部分传递。 调用的例程弹出堆栈中的自变量。  
  
 对于 C，`__cdecl`命名约定使用函数名前面带下划线 ( `_` ); 执行任何大小写转换。 除非声明为`extern "C"`，c + + 函数使用不同的修饰名称的方案。 有关详细信息，请参阅[修饰名](../../build/reference/decorated-names.md)。  
  
## <a name="fastcall-specifics"></a>__fastcall 细节  
 某些`__fastcall`在寄存器中传递函数的自变量 (针对 x86 处理器、 ECX 和 EDX 中)，，rest 从右到左推送到堆栈上。 返回之前调用的例程中弹出堆栈从这些自变量。 通常情况下， **/Gr**缩短执行时间。  
  
> [!NOTE]
>  请注意，当你使用`__fastcall`在内联程序集语言中编写的任何函数的调用约定。 你使用的寄存器可能与编译器的使用冲突。  
  
 对于 C，`__fastcall`命名约定使用函数名前面带 at 符号 (`@`) 跟以字节为单位的函数的自变量的大小。 是不完成的任何大小写转换。 编译器会使用此模板的命名约定：  
  
```  
@function_name@number  
```  
  
 当你使用`__fastcall`命名约定，使用标准包含文件。 否则，你将得到的未解析外部引用。  
  
## <a name="stdcall-specifics"></a>__stdcall 细节  
 A`__stdcall`函数的自变量推入到堆栈上从右到左，并且被调用的函数在返回之前弹出堆栈从这些自变量。  
  
 对于 C，`__stdcall`命名约定使用函数名前面带下划线 ( `_` ) 并且后跟 at 符号 (@) 和函数的自变量以字节为单位的大小。 不执行任何大小写转换。 编译器会使用此模板的命名约定：  
  
```  
_functionname@number  
```  
  
## <a name="vectorcall-specifics"></a>__vectorcall 细节  
 A`__vectorcall`函数的整数自变量通过值传递，使用最多两个 （在 x86) 或 （在 x64) 的四个整数寄存器，和最多六个 XMM 寄存器浮点和矢量值和 rest 堆栈上传递从右到左。 返回之前，被调用的函数从堆栈清除。 在 XMM0 中返回向量和浮点的返回值。  
  
 对于 C，`__vectorcall`命名约定使用函数名称后跟两个 at 符号 （@ @） 和函数的自变量以字节为单位的大小。 不执行任何大小写转换。 编译器会使用此模板的命名约定：  
  
```  
functionname@@number  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +**文件夹。  
  
3.  选择**高级**属性页。  
  
4.  修改**调用约定**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)
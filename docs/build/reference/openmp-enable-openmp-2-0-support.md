---
title: "-openmp （启用 OpenMP 2.0 支持） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
dev_langs:
- C++
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8217a901f071f50dbd2d7dfcbffccf4014a9444
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="openmp-enable-openmp-20-support"></a>/openmp（启用 OpenMP 2.0 支持）
使编译器处理`#pragma` [omp](../../preprocessor/omp.md)。  
  
## <a name="syntax"></a>语法  
  
```  
/openmp  
```  
  
## <a name="remarks"></a>备注  
 `#pragma omp`用于指定[指令](../../parallel/openmp/reference/openmp-directives.md)和[子句](../../parallel/openmp/reference/openmp-clauses.md)。 如果**/openmp**未指定在编译时，编译器将忽略 OpenMP 子句和指令。 [OpenMP 函数](../../parallel/openmp/reference/openmp-functions.md)调用处理的编译器即使**/openmp**未指定。  
  
 使用编译的应用程序**/openmp**和**/clr**仅在单个应用程序域进程中运行; 不支持多个应用程序域。 也就是说，当运行模块构造函数 (.cctor) 时，它会检测使用编译的进程**/openmp**和应用程序是否正在加载到非默认运行时。 有关详细信息，请参阅[appdomain](../../cpp/appdomain.md)， [/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)，和[初始化混合程序集的](../../dotnet/initialization-of-mixed-assemblies.md)。  
  
 如果你尝试加载使用编译的应用程序**/openmp**和**/clr**到非默认应用程序域中，<xref:System.TypeInitializationException>将会引发异常，在调试器外部和在调试器中，将引发 OpenMPWithMultipleAppdomainsException 异常。  
  
 此外可以在以下情况下引发这些异常：  
  
-   如果你的应用程序使用编译**/clr**，但不是能与**/openmp**，将会加载到非默认应用程序域但其中的过程包括的应用程序用编译**/openmp**。  
  
-   如果你通过你**/clr** regasm.exe 之类的实用工具，到应用程序 ([Regasm.exe （程序集注册工具）](/dotnet/framework/tools/regasm-exe-assembly-registration-tool))，这会将其目标程序集加载到非默认应用程序域。  
  
 在 OpenMP 区域中，公共语言运行时的代码访问安全性不起作用。 如果应用了并行区域外部的 CLR 代码访问安全特性，它实际上在将并行区域。  
  
 Microsoft 建议不对写入**/openmp**应用程序允许部分受信任调用方，使用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>，或任何 CLR 代码访问安全属性。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  展开**C/c + +**节点。  
  
4.  选择**语言**属性页。  
  
5.  修改**OpenMP 支持**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>。  
  
## <a name="example"></a>示例  
 下面的示例显示了一些与它启动后，使用线程池线程池启动的效果。 假设 x64，单核，双处理器线程池对大约 16ms年启动。 之后，但没有为线程池很少的费用。  
  
 使用编译**/openmp**，test2 第二次调用永远不会运行时间比你如果使用编译**/openmp-**，因为没有任何线程池启动。 在 100 万次迭代**/openmp**版本的速度快于**/openmp-** test2，与在 25 迭代这两个第二个调用的版本**/openmp-**和**/openmp**版本注册小于时钟粒度。  
  
 因此，如果你仅有一个循环中你的应用程序和小于 （调整您的计算机上的近似系统开销） 的时间运行**/openmp**可能不合适，但如果它是多于，你可能需要考虑使用**/openmp**。  
  
```  
// cpp_compiler_options_openmp.cpp  
#include <omp.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <windows.h>  
  
volatile DWORD dwStart;  
volatile int global = 0;  
  
double test2(int num_steps) {  
   int i;  
   global++;  
   double x, pi, sum = 0.0, step;  
  
   step = 1.0 / (double) num_steps;  
  
   #pragma omp parallel for reduction(+:sum) private(x)  
   for (i = 1; i <= num_steps; i++) {  
      x = (i - 0.5) * step;  
      sum = sum + 4.0 / (1.0 + x*x);  
   }  
  
   pi = step * sum;  
   return pi;  
}  
  
int main(int argc, char* argv[]) {  
   double   d;  
   int n = 1000000;  
  
   if (argc > 1)  
      n = atoi(argv[1]);  
  
   dwStart = GetTickCount();  
   d = test2(n);  
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);  
  
   dwStart = GetTickCount();  
   d = test2(n);  
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)
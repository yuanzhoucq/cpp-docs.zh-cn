---
title: "/openmp（启用 OpenMP 2.0 支持） | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/openmp"
  - "VC.Project.VCCLCompilerTool.OpenMP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/openmp 编译器选项 [C++]"
  - "-openmp 编译器选项 [C++]"
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /openmp（启用 OpenMP 2.0 支持）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

导致编译器处理 `#pragma` [omp](../../preprocessor/omp.md)。  
  
## 语法  
  
```  
/openmp  
```  
  
## 备注  
 `#pragma omp` 用于指定 [Directives](../../parallel/openmp/reference/openmp-directives.md) 和 [Clauses](../../parallel/openmp/reference/openmp-clauses.md)。  如果未在编译中指定 **\/openmp**，编译器将忽略 OpenMP 子句和指令。  即使未指定 **\/openmp**，[OpenMP 函数](../../parallel/openmp/reference/openmp-functions.md)调用也由编译器处理。  
  
 使用 **\/openmp** 编译且使用 [Libraries](../../parallel/openmp/reference/openmp-libraries.md) 的应用程序只能在 Windows 2000 或更高版本的操作系统上运行。  
  
 用 **\/openmp** 和 **\/clr** 编译的应用程序只能在单个应用程序域进程中运行；不支持多个应用程序域。  也就是说，当运行模块构造函数 \(.cctor\) 时，它将检测用 **\/openmp** 编译的进程以及应用程序是否正在加载到非默认运行时。  有关更多信息，请参见[appdomain](../../cpp/appdomain.md)、[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)和[混合程序集的初始化](../../dotnet/initialization-of-mixed-assemblies.md)。  
  
 如果尝试将用 **\/openmp** 和 **\/clr** 编译的应用程序加载到非默认应用程序域，则调试器外将引发 <xref:System.TypeInitializationException> 异常并且调试器内将引发 OpenMPWithMultipleAppdomainsException 异常。  
  
 在下列情形下，也可能引发这些异常：  
  
-   如果用 **\/clr**（而不是用 **\/openmp**）编译的应用程序加载到非默认应用程序域，但是其中的进程包括用 **\/openmp** 编译的应用程序。  
  
-   如果将 **\/clr** 应用程序传递给实用工具，例如 regasm.exe \([Regasm.exe（程序集注册工具）](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)\)，而该实用工具将其目标程序集加载到非默认应用程序域。  
  
 公共语言运行时的代码访问安全性在 OpenMP 区域中不起作用。  如果在并行区域外部应用 CLR 代码访问安全性特性，它在并行区域内将无效。  
  
 Microsoft 建议您不要通过使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 或任何 CLR 代码访问安全性特性，编写允许部分信任的调用方的 **\/openmp** 应用程序。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“C\/C\+\+”**节点。  
  
4.  选择**“语言”**属性页。  
  
5.  修改**“OpenMP 支持”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>。  
  
## 示例  
 下面的示例显示 threadpool 启动与启动它之后使用 threadpool 的一些效果比较。  假定 x64 单内核、双处理器 threadpool 花费大约 16 毫秒启动。  在此之后，threadpool 将花费极少的时间。  
  
 当使用 **\/openmp** 编译时，第二次调用 test2 所运行的时间决不会比用 **\/openmp\-** 编译时长，因为不需要 threadpool 启动。  在进行一百万次迭代的情况下，**\/openmp** 版本第二次调用 test2 的速度比 **\/openmp\-** 版本快；在进行 25 次迭代的情况下，**\/openmp\-** 和 **\/openmp** 两个版本的注册时间都小于时钟间隔大小。  
  
 因此，如果应用程序中仅有一个循环并且它运行的时间少于 15 毫秒（根据计算机上的大致系统开销而有所不同），**\/openmp** 可能不合适，但是如果它的时间多于 15 毫秒，则可能要考虑使用 **\/openmp**。  
  
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
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)
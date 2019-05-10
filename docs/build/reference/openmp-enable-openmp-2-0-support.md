---
title: /openmp （启用 OpenMP 支持）
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: caa06d89c590abd2b3a74a5a6b118d6ba4acd910
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320209"
---
# <a name="openmp-enable-openmp-support"></a>/openmp （启用 OpenMP 支持）

使编译器处理[ `#pragma omp` ](../../preprocessor/omp.md)支持 OpenMP 指令。

## <a name="syntax"></a>语法

::: moniker range=">= vs-2019"

> **/openmp**\[**:**__experimental__]

::: moniker-end

::: moniker range="<= vs-2017"

> **/openmp**

::: moniker-end

## <a name="remarks"></a>备注

`#pragma omp` 用于指定[指令](../../parallel/openmp/reference/openmp-directives.md)并[子句](../../parallel/openmp/reference/openmp-clauses.md)。 如果 **/openmp**未指定在编译时，编译器将忽略 OpenMP 子句和指令。 [OpenMP 函数](../../parallel/openmp/reference/openmp-functions.md)调用处理由编译器即使 **/openmp**未指定。

::: moniker range=">= vs-2019"

C++编译器当前支持 OpenMP 2.0 标准。 但是，Visual Studio 2019 现在还提供了单指令多数据的功能。 若要使用单指令多数据，通过使用编译 **/openmp： 实验性**选项。 此选项启用这两项的常用 OpenMP 功能，并附加 OpenMP SIMD 功能不可用时使用 **/openmp**切换。

::: moniker-end

使用编译的应用程序 **/openmp**并 **/clr**只能在单个应用程序域进程中运行。 不支持多个应用程序域。 也就是说，当模块构造函数 (`.cctor`) 是运行时，检测到如果使用编译的进程 **/openmp**，以及应用程序加载到非默认运行时。 有关详细信息，请参阅[appdomain](../../cpp/appdomain.md)， [/clr （公共语言运行时编译）](clr-common-language-runtime-compilation.md)，并[混合程序集初始化](../../dotnet/initialization-of-mixed-assemblies.md)。

如果尝试加载应用程序编译的同时使用这二者 **/openmp**并 **/clr**到非默认应用程序域，<xref:System.TypeInitializationException>在调试器外部引发异常和`OpenMPWithMultipleAppdomainsException`异常在调试器中引发。

此外可以在以下情况下引发这些异常：

- 如果使用你的应用程序进行编译 **/clr**但不是 **/openmp**，并加载到非默认应用程序域，其中的过程包括使用编译的应用 **/openmp**.

- 如果传递你 **/clr**应用到一个实用程序，如[regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)，这会将其目标程序集加载到非默认应用程序域。

公共语言运行时代码访问安全性在 OpenMP 区域中不起作用。 如果应用了并行区域之外的 CLR 代码访问安全特性，它不会生效并行区域中。

Microsoft 不建议编写 **/openmp**应用，其允许部分受信任调用方。 不要使用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>，或任何 CLR 代码访问安全属性。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 展开**配置属性** > **C /C++** > **语言**属性页。

1. 修改**OpenMP 支持**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>。

## <a name="example"></a>示例

下面的示例显示了一些与启动后将其使用线程池线程池启动的效果。 假设 x64，单核双处理器，线程池用大约 16 毫秒才能启动。 此后，收取稍有额外的费用为线程池。

当编译使用 **/openmp**，第二个调用 test2 永远不会运行时间超过如果编译使用 **/openmp-**，因为没有任何线程池启动。 在一百万次迭代 **/openmp**版本的速度快于 **/openmp-** test2 第二次调用的版本。 在 25 次迭代，同时 **/openmp-** 并 **/openmp**版本注册小于时钟粒度。

如果应用程序中有一个循环，并且它在少于 15 ms （调整你的计算机上的近似系统开销） 中运行 **/openmp**可能不太合适。 如果它是更高版本，您可能想要考虑使用 **/openmp**。

```cpp
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

[MSVC 编译器选项](compiler-options.md) \
[MSVC 编译器命令行语法](compiler-command-line-syntax.md) \
[MSVC 中的 OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md)

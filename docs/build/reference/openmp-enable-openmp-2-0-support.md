---
title: /打开（启用 OpenMP 支持）
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: d3454650bfaaacd756e5cfc73df056441a39f5ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336196"
---
# <a name="openmp-enable-openmp-support"></a>/打开（启用 OpenMP 支持）

使编译器处理[`#pragma omp`](../../preprocessor/omp.md)指令以支持 OpenMP。

## <a name="syntax"></a>语法

::: moniker range=">= vs-2019"

> **/openmp**\[**：**__实验__|

::: moniker-end

::: moniker range="<= vs-2017"

> **/openmp**

::: moniker-end

## <a name="remarks"></a>备注

`#pragma omp`用于指定[指令](../../parallel/openmp/reference/openmp-directives.md)和[子句](../../parallel/openmp/reference/openmp-clauses.md)。 如果在编译中未指定 **/openmp，** 编译器将忽略 OpenMP 子句和指令。 即使未指定 **/openmp，** 编译器也会处理[openMP 函数](../../parallel/openmp/reference/openmp-functions.md)调用。

::: moniker range=">= vs-2019"

C++编译器当前支持 OpenMP 2.0 标准。 然而，Visual Studio 2019 现在也提供 SIMD 功能。 要使用 SIMD，请使用 **/openmp：实验**选项进行编译。 此选项支持常用的 OpenMP 功能，以及使用 **/openmp**开关时不可用的其他 OpenMP SIMD 功能。

::: moniker-end

使用 **/openmp**和 **/clr**编译的应用程序只能在单个应用程序域进程中运行。 不支持多个应用程序域。 也就是说，当运行模块构造函数 （）`.cctor`时，它会检测进程是否使用 **/openmp**编译，以及应用是否加载到非默认运行时。 有关详细信息，请参阅[应用程序域](../../cpp/appdomain.md) [/clr（通用语言运行时编译）](clr-common-language-runtime-compilation.md)和[混合程序集的初始化](../../dotnet/initialization-of-mixed-assemblies.md)。

如果尝试将使用 **/openmp**和 **/clr**编译的应用加载到非默认应用程序域中，<xref:System.TypeInitializationException>则异常将引发调试器之外，调试器中将`OpenMPWithMultipleAppdomainsException`引发异常。

在以下情况下也可以引发这些异常：

- 如果应用程序使用 **/clr**编译，但使用 **/openmp**编译，并且加载到非默认应用程序域中，其中该过程包括使用 **/openmp**编译的应用程序。

- 如果将 **/clr**应用传递给实用程序，例如[regasm.exe，](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)该实用程序将其目标程序集加载到非默认应用程序域中。

通用语言运行时的代码访问安全性在 OpenMP 区域中不起作用。 如果在并行区域之外应用 CLR 代码访问安全属性，则该属性在并行区域中无效。

Microsoft 不建议您编写允许部分受信任的调用方的 **/openmp**应用。 不要使用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>或任何 CLR 代码访问安全属性。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 展开**配置属性** > **C/C++** > **语言**属性页。

1. 修改**OpenMP 支持**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>。

## <a name="example"></a>示例

下面的示例显示了线程池启动与启动后使用线程池的一些影响。 假设一个x64，单核，双处理器，线程池需要大约16毫秒启动。 之后，线程池的额外费用很小。

使用 **/openmp**编译时，对 test2 的第二个调用永远不会比使用 **/openmp-** 编译时运行的时间长，因为没有线程池启动。 在一百万次迭代中 **，/openmp**版本比第二个调用 test2 的 **/openmp 版本**快。 在 25 次迭代中 **，/openmp 和** **/openmp**版本注册小于时钟粒度。

如果应用程序中只有一个循环，并且运行在小于 15 ms（根据计算机上的大致开销进行调整）中 **，/openmp**可能不合适。 如果它更高，您可能需要考虑使用 **/openmp**。

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

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md) \
[MSVC 编译器命令行语法](compiler-command-line-syntax.md) \
[MSVC 中的 OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md)

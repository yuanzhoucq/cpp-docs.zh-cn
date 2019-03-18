---
title: 优化代码
ms.date: 12/10/2018
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.openlocfilehash: ae60070959c683a6365992e7b6cc510fd4111b36
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825184"
---
# <a name="optimizing-your-code"></a>优化代码

通过优化可执行文件，可以实现快速执行速度和较小代码大小之间的平衡。 本主题讨论了一些 Visual c + + 提供的用于帮助您优化代码的机制。

## <a name="language-features"></a>语言功能

以下主题介绍了一些 C/c + + 语言中的优化功能。

[优化杂注和关键字](optimization-pragmas-and-keywords.md)<br/>
关键字和杂注，您可以使用在代码中以提高性能的列表。

[按类别列出的编译器选项](reference/compiler-options-listed-by-category.md)<br/>
一系列 **/O**专门影响执行速度或代码大小的编译器选项。

[规则引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)<br/>
右值引用支持的实现*移动语义*。 如果可以显著提高的移动语义用于实现模板库，使用这些模板的应用程序的性能。

### <a name="the-optimize-pragma"></a>优化杂注

如果已优化的代码节将导致错误或速度减慢，则可以使用[优化](../preprocessor/optimize.md)杂注来关闭该部分的优化。

将两个杂注，代码如下所示：

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>编程做法

当编译使用优化代码时，可能会注意到其他警告消息。 需要此行为，因为一些警告仅与优化的代码。 如果注意到这些警告，则可以避免很多优化问题。

自相矛盾的是，优化速度的程序可能会导致代码运行速度变慢。 这是因为一些优化速度增加代码大小。 例如，内联函数消除函数调用的开销。 但是，内联太多代码可能会使您的程序很大的错误的虚拟内存页面数增加。 因此，获得通过消除函数调用的速度可能会丢失对内存换用。

以下主题讨论最佳编程实践。

[提高时间关键代码的技巧](tips-for-improving-time-critical-code.md)<br/>
更好地编码技术可产生更好的性能。 本主题建议的编码技术可以帮助您确保你的代码的时间关键部分满意地执行。

[优化最佳做法](optimization-best-practices.md)<br/>
提供有关如何最好地优化您的应用程序的常规指南。

## <a name="debugging-optimized-code"></a>调试优化的代码

因为优化可能会更改由编译器创建的代码，我们建议您调试应用程序和测量其性能，然后优化您的代码。

以下主题提供有关如何调试版本生成的信息。

- [在 Visual Studio 中进行调试](/visualstudio/debugger/debugging-in-visual-studio)

- [如何：调试优化的代码](/visualstudio/debugger/how-to-debug-optimized-code)

- [为何浮点数可能丢失精度](why-floating-point-numbers-may-lose-precision.md)


以下主题提供有关如何优化生成、 加载和执行代码的信息。

- [提高编译器吞吐量](improving-compiler-throughput.md)

- [使用没有 () 的函数名不产生代码](using-function-name-without-parens-produces-no-code.md)

- [优化内联程序集](../assembler/inline/optimizing-inline-assembly.md)

- [为 ATL 项目指定编译器优化](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [我应该使用哪些优化技术来提高时加载的客户端应用程序的性能？](../build/dll-frequently-asked-questions.md#mfc_optimization)


## <a name="in-this-section"></a>本节内容

[优化杂注和关键字](optimization-pragmas-and-keywords.md)<br/>
[提高编译器吞吐量](improving-compiler-throughput.md)<br/>
[为何浮点数可能丢失精度](why-floating-point-numbers-may-lose-precision.md)<br/>
[IEEE 浮点表示形式](ieee-floating-point-representation.md)<br/>
[提高时间关键代码的技巧](tips-for-improving-time-critical-code.md)<br/>
[使用没有 () 的函数名不产生代码](using-function-name-without-parens-produces-no-code.md)<br/>
[优化最佳做法](optimization-best-practices.md)<br/>
[按配置文件优化](profile-guided-optimizations.md)<br/>
[用于按配置文件优化的环境变量](environment-variables-for-profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgomgr](pgomgr.md)<br/>
[pgosweep](pgosweep.md)<br/>
[如何：将多个 PGO 配置文件合并成一个配置文件](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
[性能和诊断中心内的 Visual Studio 2013 PGO 加载项](profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)<br/>

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](reference/c-cpp-building-reference.md)

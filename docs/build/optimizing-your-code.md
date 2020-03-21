---
title: 优化代码
ms.date: 05/06/2019
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.openlocfilehash: 00356cf50ca8e50c80e8a1142adf654816490c9b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078496"
---
# <a name="optimizing-your-code"></a>优化代码

通过优化可执行文件，可以在快速执行速度与小代码大小之间实现平衡。 本主题讨论 Visual Studio 提供的用于帮助优化代码的部分机制。

## <a name="language-features"></a>语言功能

以下主题描述了 C/C++语言中的一些优化功能。

[优化杂注和关键字](optimization-pragmas-and-keywords.md) \
可以在代码中使用的关键字和杂注的列表，用于提高性能。

[按类别列出的编译器选项](reference/compiler-options-listed-by-category.md) \
专门影响执行速度或代码大小的 **/o**编译器选项的列表。

[右值引用声明符： & &](../cpp/rvalue-reference-declarator-amp-amp.md) \
右值引用支持*移动语义*的实现。 如果使用移动语义来实现模板库，使用这些模板的应用程序的性能可能会显著提高。

### <a name="the-optimize-pragma"></a>Optimize 杂注

如果代码的优化部分导致错误或减速，则可以使用[optimize](../preprocessor/optimize.md)杂注关闭该部分的优化。

将代码包含在两个杂注之间，如下所示：

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>编程做法

在编译代码时，您可能会注意到其他警告消息。 此行为是预期行为，因为某些警告仅与优化代码相关。 如果注意这些警告，可以避免很多优化问题。

自相矛盾，优化程序的速度可能导致代码运行速度变慢。 这是因为速度的某些优化会增加代码大小。 例如，内联函数可消除函数调用的开销。 但是，内联太多的代码可能会导致程序很大，以致虚拟内存页错误的数量会增加。 因此，消除函数调用所获得的速度可能会丢失内存交换。

以下主题介绍了良好的编程做法。

[提高时间关键代码的技巧](tips-for-improving-time-critical-code.md) \
更好的编码方法可以提高性能。 本主题提供了可帮助您确保代码的时间关键部分执行满意的编码技术。

[优化最佳实践](optimization-best-practices.md) \
提供有关如何最好地优化应用程序的一般准则。

## <a name="debugging-optimized-code"></a>调试优化的代码

因为优化可能会更改编译器创建的代码，所以建议调试应用程序并度量其性能，然后优化代码。

以下主题提供有关如何调试发布版本的信息。

- [在 Visual Studio 中进行调试](/visualstudio/debugger/debugging-in-visual-studio)

- [如何：调试优化的代码](/visualstudio/debugger/how-to-debug-optimized-code)

- [为何浮点数可能丢失精度](why-floating-point-numbers-may-lose-precision.md)

以下主题提供了有关如何优化生成、加载和执行代码的信息。

- [提高编译器吞吐量](improving-compiler-throughput.md)

- [使用没有 () 的函数名不产生代码](using-function-name-without-parens-produces-no-code.md)

- [优化内联程序集](../assembler/inline/optimizing-inline-assembly.md)

- [为 ATL 项目指定编译器优化](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [在加载时，应该使用哪种优化方法来改善客户端应用程序的性能？](../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="in-this-section"></a>在本节中

[优化杂注和关键字](optimization-pragmas-and-keywords.md) \
[提高编译器吞吐量](improving-compiler-throughput.md) \
[为何浮点数可能丢失精度](why-floating-point-numbers-may-lose-precision.md) \
[IEEE 浮点表示形式](ieee-floating-point-representation.md) \
[提高时间关键代码的技巧](tips-for-improving-time-critical-code.md) \
[使用没有（）的函数名不产生任何代码](using-function-name-without-parens-produces-no-code.md) \
[优化最佳实践](optimization-best-practices.md) \
[按配置优化](profile-guided-optimizations.md) \
[按配置文件优化的环境变量](environment-variables-for-profile-guided-optimizations.md) \
[PgoAutoSweep](pgoautosweep.md) \
[pgomgr](pgomgr.md) \
[pgosweep](pgosweep.md) \
[如何：将多个 PGO 配置文件合并成一个配置文件](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)

## <a name="see-also"></a>另请参阅

[C/C++ 生成参考](reference/c-cpp-building-reference.md)

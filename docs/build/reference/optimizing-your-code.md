---
title: 优化代码 |Microsoft 文档
ms.custom: ''
ms.date: 12/28/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4306f825b9925dbdcdc994d287a2c4287ea7bfc2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="optimizing-your-code"></a>优化代码

通过优化可执行文件，你可以实现快速执行速度和较小代码大小之间的平衡。 本主题讨论一些 Visual c + + 提供帮助你优化代码的机制。

## <a name="language-features"></a>语言功能

以下主题介绍一些 C/c + + 语言中的优化功能。

[优化杂注和关键字](../../build/reference/optimization-pragmas-and-keywords.md)  
关键字和杂注，你可以使用在你的代码来提高性能的列表。

[按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)  
一份**/O**专门影响执行速度或代码大小的编译器选项。

[规则引用声明符：&&](../../cpp/rvalue-reference-declarator-amp-amp.md)  
右值引用支持的实现*移动语义*。 如果移动语义用于实现模板库，使用这些模板的应用程序的性能可以显著提高。

### <a name="the-optimize-pragma"></a>优化杂注

如果代码的优化的节将导致错误或速度变慢，则可以使用[优化](../../preprocessor/optimize.md)杂注关闭该部分的优化。

将代码包含的两个杂注，如下所示：

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>编程做法

编译用优化代码时，可能会注意到附加的警告消息。 需要此行为，因为一些警告仅与优化的代码。 如果你注意到这些警告，则可避免许多优化问题。

自相矛盾，优化速度的程序，这种情况可能会导致代码运行速度变慢。 这是因为某些优化速度，请增加代码大小。 例如，内联函数消除函数调用的开销。 但是，内联太多代码可能会使你的程序很大的虚拟内存页面数错误增加。 因此，通过消除函数调用获得的速度可能会丢失对内存换用。

以下主题讨论好的编程做法。

[提高时间关键代码的技巧](../../build/reference/tips-for-improving-time-critical-code.md)  
更好的编码技术可以产生更好的性能。 此主题建议的编码方法，可帮助你确保你的代码的时间关键部分满意地执行。

[优化最佳做法](../../build/reference/optimization-best-practices.md)  
提供有关如何最好地优化你的应用程序的一般准则。

## <a name="debugging-optimized-code"></a>由于调试优化的代码

因为优化可能更改由编译器创建的代码，我们建议你调试应用程序和测量其性能，并随后优化代码。

以下主题提供有关如何调试的基本信息。

- [在 Visual Studio 中进行调试](/visualstudio/debugger/debugging-in-visual-studio)

- [创建发行版本时遇到的常见问题](../../build/reference/common-problems-when-creating-a-release-build.md)

以下主题提供有关如何调试更高级的信息。

- [如何：调试优化的代码](/visualstudio/debugger/how-to-debug-optimized-code)

- [为何浮点数可能丢失精度](../../build/reference/why-floating-point-numbers-may-lose-precision.md)

以下主题提供有关如何优化生成、 加载和执行代码的信息。

- [提高编译器吞吐量](../../build/reference/improving-compiler-throughput.md)

- [使用没有 () 的函数名不产生代码](../../build/reference/using-function-name-without-parens-produces-no-code.md)

- [优化内联程序集](../../assembler/inline/optimizing-inline-assembly.md)

- [为 ATL 项目指定编译器优化](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [我应使用哪些优化技术来提高客户端应用程序的性能，在加载时？](../../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)  

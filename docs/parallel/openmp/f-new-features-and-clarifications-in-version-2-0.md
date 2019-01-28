---
title: F. 2.0 版中新功能和说明
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 2e186bbc82f4f43e831dd05cdded2a9e946d1dd2
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087205"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. 2.0 版中新功能和说明

本附录总结了对从版本 1.0 迁移到 2.0 版中的 OpenMP C/c + + 规范所做的关键更改。 以下各项是新功能添加到规范：

- OpenMP 中允许使用逗号[指令](2-directives.md#21-directive-format)。

- 添加`num_threads`子句。 该子句也允许用户请求特定的线程数[并行构造](2-directives.md#23-parallel-construct)。

- [Threadprivate](2-directives.md#271-threadprivate-directive)指令已扩展为接受静态块范围变量。

- C99 变量长度数组是完整的类型，可以指定任意位置完整的类型是允许、 此类如下所示的列表`private`， `firstprivate`，并`lastprivate`子句 (请参阅[部分 2.7.2](2-directives.md#272-data-sharing-attribute-clauses))。

- 并行区域中的私有变量可以将标记[专用](2-directives.md#2721-private)再次在嵌套指令中。

- `copyprivate`子句已添加。 它提供了一种机制来使用私有变量广播来自团队的成员的其他成员的值。 它是使用共享的变量值时提供此类共享的变量会很困难 （例如，在需要在每个级别的不同变量的递归） 的替代方法。 [Copyprivate](2-directives.md#2728-copyprivate)子句仅可出现在`single`指令。

- 添加了计时例程[omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function)并[omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function)类似于 MPI 例程。 这些函数所需执行墙上的时钟计时。

- 附录介绍了一系列[实现定义的行为](e-implementation-defined-behaviors-in-openmp-c-cpp.md)OpenMP C/c + + 中已添加。 需要定义并记录其行为在这些情况下实现。

- 以下更改用来阐明或更正以前 OpenMP API 规范中为 C/c + + 的功能：

  - 阐明了的行为[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)并[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)时`omp_in_parallel`返回非零值是不确定。

  - 阐明[指令嵌套](2-directives.md#29-directive-nesting)嵌套的并行使用时。

  - [锁定初始化](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions)并[锁定析构](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函数可以调用并行区域中。

  - 已添加到新的示例[附录 A](a-examples.md)。
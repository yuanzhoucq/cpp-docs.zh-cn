---
title: F. 2.0 版中新功能和说明
ms.date: 11/04/2016
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: c8a597c6af397bd162d92a945d96409b1839e2a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657133"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. 2.0 版中新功能和说明

本附录总结了对从版本 1.0 迁移到 2.0 版中的 OpenMP C/c + + 规范所做的关键更改。 以下各项是新功能添加到规范：

- OpenMP 指令中允许使用逗号 ([部分 2.1](../../parallel/openmp/2-1-directive-format.md)页 7 上)。

- 添加`num_threads`子句。 该子句也允许用户请求特定数量的线程的并行构造 ([2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页上)。

- `threadprivate`指令已扩展为接受静态块范围变量 ([部分 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) 23 页上)。

- C99 变量长度数组是完整的类型，因此可以指定任意位置完整的类型，例如中允许的列表`private`， `firstprivate`，并`lastprivate`子句 ([部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上)。

- 并行区域中的私有变量可以将标记为私有再次中嵌套指令 ([部分 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)第 25 页上)。

- `copyprivate`子句已添加。 它提供了一种机制来使用私有变量广播来自团队的成员的其他成员的值。 它是使用共享的变量值时提供此类共享的变量会很困难 （例如，在需要在每个级别的不同变量的递归） 的替代方法。 `copyprivate`子句仅可出现在**单个**指令 ([部分 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md)第 32 页上)。

- 添加了计时例程`omp_get_wtick`和`omp_get_wtime`类似于 MPI 例程。 这些函数所需的执行墙上的时钟计时 ([第 3.3.1 节](../../parallel/openmp/3-3-1-omp-get-wtime-function.md)第 44 页上和[的第 3.3.2 节](../../parallel/openmp/3-3-2-omp-get-wtick-function.md)在第 45 页)。

- 已添加的附录介绍了实现定义的行为在 OpenMP C/c + + 的列表。 实现所需定义并记录在这些情况下其行为 ([附录 E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md) 97 页上)。

- 以下更改用来阐明或更正以前 OpenMP API 规范中为 C/c + + 的功能：

   - 阐明了的行为`omp_set_nested`并`omp_set_dynamic`时`omp_in_parallel`返回非零值是不确定 ([部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)本页 39，和[部分 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 40 页上)。

   - 使用嵌套的并行时阐明指令嵌套 ([部分 2.9](../../parallel/openmp/2-9-directive-nesting.md)第 33 页上)。

   - 可在并行区域中调用的锁初始化和锁析构函数 ([部分 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) 42 页上和[部分 3.2.2](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md) 42 页上)。

   - 已添加新示例 ([附录 A](../../parallel/openmp/a-examples.md) 51 页)。
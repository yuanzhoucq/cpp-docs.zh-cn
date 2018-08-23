---
title: F. 新功能和 2.0 版中的说明 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e48f299e66ed1b4c075757a9cd143d0afe897db
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693138"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. 新功能和 2.0 版中的说明
本附录总结了对从版本 1.0 移动到 2.0 版中的 OpenMP C/c + + 规范的密钥的更改。 以下各项是新功能添加到规范：  
  
-   OpenMP 指令中允许使用逗号 ([部分 2.1](../../parallel/openmp/2-1-directive-format.md) 7 页上)。  
  
-   添加`num_threads`子句。 子句也允许用户请求特定数量的线程的并行构造 ([2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页上)。  
  
-   `threadprivate`指令已扩展为接受静态的块范围变量 ([部分 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) 23 页上)。  
  
-   C99 变量长度数组是完整的类型，因此可以指定任意位置完整的类型，例如中允许的列表`private`， `firstprivate`，和`lastprivate`子句 ([部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上)。  
  
-   并行区域中的私有变量可以再次在嵌套指令中为私有标记 ([部分 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)第 25 页上)。  
  
-   `copyprivate`已添加子句。 它提供一种机制来使用的私有变量的其他成员广播来自团队的成员的一个值。 它是另一种共享的变量的值时提供此类共享的变量是非常困难的 （例如，在需要一个不同的变量在每个级别的递归）。 `copyprivate`子句只能出现在**单个**指令 ([部分 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md)在页上 32)。  
  
-   添加计时例程`omp_get_wtick`和`omp_get_wtime`类似于 MPI 例程。 这些函数所需的执行墙时钟计时 ([部分 3.3.1](../../parallel/openmp/3-3-1-omp-get-wtime-function.md)在页上 44 和[第 3.3.2 节](../../parallel/openmp/3-3-2-omp-get-wtick-function.md)页 45 上)。  
  
-   已添加附录，以实现定义的行为在 OpenMP C/c + + 的列表。 实现是需要定义并记录在这些情况下其行为 ([附录 E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md)页 97 上)。  
  
-   以下更改用于阐明或更正以前 OpenMP API 规范中为 C/c + + 的功能：  
  
    -   阐明了的行为`omp_set_nested`和`omp_set_dynamic`时`omp_in_parallel`返回非零是不确定 ([部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)在页上 39，和[部分 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 40 页上)。  
  
    -   使用嵌套的并行时阐明指令嵌套 ([部分 2.9](../../parallel/openmp/2-9-directive-nesting.md)在页上 33)。  
  
    -   可以在并行区域中调用锁初始化和锁析构函数 ([部分 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)页 42 上和[部分 3.2.2](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)页 42 上)。  
  
    -   已添加新示例 ([附录 A](../../parallel/openmp/a-examples.md)页 51 上)。
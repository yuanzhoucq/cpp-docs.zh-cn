---
title: 2.4.1 for 构造 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 27d2cbce-786b-4819-91d3-d55b2cc57a5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac142c628f3c2bef0bc29a2ffd50df8a9efda400
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216532"
---
# <a name="241-for-construct"></a>2.4.1 for 构造

**为**指令标识的指定将并行执行的相关联的循环迭代的迭代工作共享构造。 迭代**为**循环分布在线程中执行绑定到并行构造团队已经存在。 语法**为**构造如下所示：

```
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

子句是以下值之一：

**private(** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**lastprivate(** *variable-list* **)**

**减少 (** *运算符* **:** *变量列表* **)**

**排序**

**计划 (** *种类*[**，** *使用 chunk_size*] **)**

**nowait**

**有关**指令在相应的结构上放置限制**为**循环。 具体而言，在相应**为**循环必须具有规范形状：

**为 (** *init expr* **;***var 逻辑操作 b*;*incr expr* **)**

*init expr*<br/>
以下项之一：

*var* = *lb*

*整数类型 var* = *lb*

*incr expr*<br/>
以下项之一：

++ *var*

*var* ++

-- *var*

*var* --

*var* += *incr*

*var* -= *incr*

*var* = *var* + *incr*

*var* = *incr* + *var*

*var* = *var* - *incr*

*var*<br/>
一个有符号的整数的变量。 如果此变量将否则共享，它隐式设为私有的持续时间内**为**。   在正文中不能修改此变量**为**语句。 除非另有指定变量**lastprivate**之后循环是不确定, 其值。

*逻辑操作*<br/>
以下项之一：

<

\<=

>

\>=

*lb*， *b*，和*incr*<br>
循环固定的整数表达式。 不存在的两个表达式计算期间同步。 因此，任何计算的方面的副作用产生不确定的结果。

请注意，使用规范格式允许数量的循环迭代将在进入循环进行计算。 使用中的类型的值执行此计算*var*之后整型提升。 特别地，如果值为*b* - *lb* + *incr* ，结果是不确定的类型，不能表示。 此外，如果*逻辑操作*是 < 或\<= then *incr expr*必须导致*var*以提高在每个循环迭代。   如果*逻辑操作*是 > 或 > = then *incr expr*必须导致*var*以减少在每个循环迭代。

**计划**子句指定如何迭代**为**循环分别位于若干个团队的线程。 程序的正确性必须不依赖于哪些线程执行的特定小版本。 值*使用 chunk_size*，如果指定，必须用正值是循环固定的整数表达式。 没有此表达式的计算期间同步。 因此，任何计算的方面的副作用产生不确定的结果。 计划*种类*可以是以下之一：

表 2-1**计划**子句*种类*值

|||
|-|-|
|静态|当**计划 (静态的***使用 chunk_size* **)** 迭代被分到指定的大小的区块的指定*使用 chunk_size*。 区块以静态方式分配给团队以轮循机制方式按线程号顺序中的线程。 如果未*使用 chunk_size*迭代空间划分为与分配给每个线程一个区块的大小，大致相等的块的指定。|
|dynamic|当**计划 (动态的***使用 chunk_size* **)** 迭代划分为区块，每个包含的一系列的指定*使用 chunk_size*迭代。 每个区块被分配给正在等待分配一个线程。 线程执行迭代的区块，并等待其下一步的分配，没有块保持可以被指定。 请注意，要分配的最后一个块区可能具有较小数目的迭代。 如果未*使用 chunk_size*指定，则默认为 1。|
|引导式|当**计划 (引导式，** *使用 chunk_size* **)** 迭代分配与减小大小的区块中的线程的指定。 当线程完成其已分配的块的迭代时，它是之前未保留任何动态分配另一个块区。 有关*使用 chunk_size*的每个块区大小为 1，是大约未分配的线程数除以的迭代数。 这些大小大约按指数规律减小到 1。 有关*使用 chunk_size*值*k*大于 1，大小约减少指数级增长到*k*，但最后一个区块可能有较少的比*k*迭代。 如果未*使用 chunk_size*指定，则默认为 1。|
|Runtime — 运行时|当**schedule （runtime)** 指定，则有关计划被延迟到运行时的决定。 计划*种类*并可以通过设置环境变量在运行时选择的消息块的大小**OMP_SCHEDULE**。 如果未设置此环境变量，生成的计划是实现定义的。 当**schedule （runtime)** 指定，则*使用 chunk_size*不能指定。|

在没有显式定义**计划**子句，则默认**计划**是实现定义的。

OpenMP 兼容的程序不应依赖于正确的执行的特定计划。 程序不应依赖于计划*种类*精确地符合更高版本，提供的说明，因为它是可以使位于同一个计划的实现中的变体*种类*跨不同的编译器。 描述可以用于选择适合于特定的情况的计划。

**排序**子句必须存在时**排序**指令将绑定到**为**构造。

末尾没有隐式屏障**有关**构造，除非**nowait**指定子句。

限制**为**指令如下所示：

-   **有关**循环必须是结构化的块中，并且，此外，其执行必须未终止的**中断**语句。

-   循环的值控制的表达式**有关**与关联的循环**为**指令必须是相同的团队中的所有线程。

-   **为**循环迭代变量必须具有带符号的整数类型。

-   只有一个**计划**子句可出现在**为**指令。

-   只有一个**排序**子句可出现在**为**指令。

-   只有一个**nowait**子句可出现在**为**指令。

-   它是未指定的 if 或任何一侧效果内的何种频率*使用 chunk_size*， *lb*， *b*，或者*incr*表达式发生。

-   值*使用 chunk_size*表达式必须是相同的团队中的所有线程。

## <a name="cross-references"></a>交叉引用：

-   **私有**， **firstprivate**， **lastprivate**，和**减少**子句，请参阅[部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。

-   **OMP_SCHEDULE**环境变量，请参阅[第 4.1 节](../../parallel/openmp/4-1-omp-schedule.md)第 48 页。

-   **按序**构造，请参阅[部分 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) 22 页上。

-   [附录 D](../../parallel/openmp/d-using-the-schedule-clause.md)，93，页提供了有关使用 schedule 子句的详细信息。
---
title: 2.3 parallel 构造 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 190eacdf-2c16-4c06-8cb7-ac60eb211425
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4be5bdc40f69cfa0a326ffa6a7f8465e401cfd33
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448228"
---
# <a name="23-parallel-construct"></a>2.3 parallel 构造

以下指令定义并行区域，这是由多个线程并行执行的程序的区域。 这是开始并行执行的基本构造。

```
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*子句*是以下之一：

**if(** *scalar-expression* **)**

**private(** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**default(shared &#124; none)**

**shared(** *variable-list* **)**

**copyin(** *variable-list* **)**

**reduction(** *operator* **:**  *variable-list* **)**

**num_threads(** *integer-expression* **)**

当线程遇到并行构造时，以下情况之一，则会创建线程的团队：

- 否**如果**子句。

- **如果**表达式的计算结果为非零值。

此线程将成为团队使用的线程编号是 0，主线程和团队，其中包括，在主线程中的所有线程并行都执行区域。 如果的值**如果**表达式为零，则序列化该区域。

若要确定请求的线程数，将按顺序考虑以下规则。 将应用第一个满足其条件的规则：

1. 如果**num_threads**子句为存在，则整数表达式的值是所请求的线程数。

1. 如果**omp_set_num_threads**尚未调用库函数，则最近执行的调用中参数的值是所请求的线程数。

1. 如果环境变量**OMP_NUM_THREADS**定义，则此环境变量的值是所请求的线程数。

1. 如果使用了任何上述两种方法，请求的线程数是实现定义。

如果**num_threads**子句存在，则它将取代请求的线程数**omp_set_num_threads**库函数或**OMP_NUM_THREADS**仅对它应用于并行区域的环境变量。 后续并行区域不受它。

执行并行区域的线程数还取决于启用动态调整线程数。 如果禁用了动态调整，则请求的线程数会执行并行区域。 如果启用了动态调整请求的线程数是最大的可能执行并行区域的线程数。

如果禁用动态调整线程数，并为并行区域请求的线程数超过了运行时系统可以提供的号时遇到并行区域，则该程序的行为是实现定义。 实现可能会例如，中断执行程序，或者它可能将并行区域的序列化。

**Omp_set_dynamic**库函数和**OMP_DYNAMIC**环境变量可用于启用和禁用动态调整线程数。

在任何给定时间实际托管线程的物理处理器的数目是实现定义的。 创建后，团队中的线程数保持不变的并行区域内。 可以由用户显式或通过从一个并行区域到另一个运行时系统会自动对其进行更改。

并行区域的动态范围内包含的语句执行的每个线程，并且每个线程可以执行不同于其他线程的语句的路径。 并行区域的词法范围之外遇到指令称为孤立的指令。

没有隐式的屏障并行区域的末尾。 只有团队的主线程继续执行并行区域的末尾。

如果团队执行并行区域中的线程遇到其他并行构造，它会创建一个新的团队，并成为该新团队的主节点。 默认情况下，嵌套并行区域进行序列化。 因此，默认情况下，嵌套并行区域执行由团队组成一个线程。 通过使用运行时库函数可能会更改默认行为**omp_set_nested**或环境变量**OMP_NESTED**。 但是，在团队中执行嵌套并行区域的线程数是实现定义的。

限制**并行**指令如下所示：

- 在最多**如果**子句可以出现在指令中。

- 它是未指定是否任何副作用 if 表达式或**num_threads**表达式出现。

- 一个**引发**执行并行区域必须在使执行相同的结构化块的动态范围之内恢复并且它必须由同一个线程引发了异常捕获。

- 只有一个**num_threads**子句可以出现在指令中。 **Num_threads**表达式计算上下文之外的并行区域，并计算结果必须为正整数值。

- 计算顺序**如果**并**num_threads**子句未指定。

## <a name="cross-references"></a>交叉引用：

- **私有**， **firstprivate**，**默认**，**共享**， **copyin**，和**减少**子句，请参阅[部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。

- **OMP_NUM_THREADS**环境变量[4.2 节](../../parallel/openmp/4-2-omp-num-threads.md)第 48 页。

- **omp_set_dynamic**库函数，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)第 39 页上。

- **OMP_DYNAMIC**环境变量，请参阅[4.3 节](../../parallel/openmp/4-3-omp-dynamic.md)49 页上。

- **omp_set_nested**函数中，请参阅[部分 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 40 页上。

- **OMP_NESTED**环境变量，请参阅[部分 4.4](../../parallel/openmp/4-4-omp-nested.md) 49 页上。

- **omp_set_num_threads**库函数，请参阅[部分 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)第 36 页上。
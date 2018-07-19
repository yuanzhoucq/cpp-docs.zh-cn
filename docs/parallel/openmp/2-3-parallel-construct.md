---
title: 2.3 parallel 构造 |Microsoft 文档
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
ms.openlocfilehash: 121454f6a98901a6c1b695a80c6ec774737b95e0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692739"
---
# <a name="23-parallel-construct"></a>2.3 parallel 构造
下面的指令定义并行区域，这是由多个线程并行执行的程序的区域。 这是启动并行执行的基本构造。  
  
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
  
 当线程遇到并行构造时，如果以下情况之一，则创建一个团队的线程：  
  
-   不**如果**子句不存在。  
  
-   **如果**表达式的计算结果为非零值。  
  
 此线程即成为主线程的团队，线程次数 0，并在团队中，包括主线程中，所有线程并行都执行区域。 如果值**如果**表达式为零，序列化的区域。  
  
 若要确定请求的线程数，将顺序视为以下规则。 将应用满足其条件的第一个规则：  
  
1.  如果**num_threads**子句不存在，则整数表达式的值是请求的线程数。  
  
2.  如果**omp_set_num_threads**已调用库函数，则最近执行的调用中的自变量的值是请求的线程数。  
  
3.  如果环境变量**OMP_NUM_THREADS**定义，则此环境变量的值是请求的线程数。  
  
4.  如果使用了任何上述两种方法，请求的线程数是实现定义。  
  
 如果**num_threads**子句不存在，则它会取代通过请求的线程数**omp_set_num_threads**库函数或**OMP_NUM_THREADS**仅为应用于的并行区域的的环境变量。 后续的并行区域不受它。  
  
 执行并行区域的线程数还取决于启用动态调整的线程数。 如果禁用了动态调整，请求的线程数将执行并行区域。 如果启用了动态调整请求的线程数是最大可能执行并行区域的线程数。  
  
 如果禁用了动态调整的线程数，并且并行区域为请求的线程数超过的运行时系统可以提供最数目时遇到并行区域，则该程序的行为是实现定义。 实现可能会例如，中断执行程序，或者它可能将并行区域的序列化。  
  
 **Omp_set_dynamic**库函数和**OMP_DYNAMIC**环境变量可用来启用和禁用动态调整的线程数。  
  
 在任何给定时间实际托管线程的物理处理器的数目是实现定义的。 创建后，团队中的线程数保持不变的持续时间内的该并行区域。 可以由用户显式或从一个并行区域到另一个运行时系统会自动对其进行更改。  
  
 在并行区域的动态范围内包含的语句执行的每个线程，并且每个线程可以执行不同于其他线程的语句的路径。 遇到外部并行区域的词法范围的指令称为孤立的指令。  
  
 没有在并行区域末尾隐含的屏障。 只有团队的主线程继续执行并行区域的末尾。  
  
 如果团队执行并行区域中的线程遇到其他并行构造，它会创建一个新的团队，然后它会成为该新团队的主机。 默认情况下，嵌套并行区域进行序列化。 因此，默认情况下，嵌套并行区域执行由团队组成一个线程。 通过使用运行时库函数中的默认行为可能会发生更改**omp_set_nested**或环境变量**OMP_NESTED**。 但是，执行嵌套并行区域在团队中的线程数为实现定义。  
  
 限制到**并行**指令如下所示：  
  
-   最多一个**如果**子句可以在指令上出现。  
  
-   它是未指定任何是否端效果置于 if 表达式或**num_threads**出现表达式。  
  
-   A**引发**执行内并行区域必须导致继续在相同的结构化块的动态范围内执行，并且它必须被捕获相同的线程引发异常。  
  
-   只有一个**num_threads**子句可以在指令上出现。 **Num_threads**上下文之外的并行区域中，计算表达式，并计算结果必须为正整数值。  
  
-   计算顺序**如果**和**num_threads**子句未指定。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   **私有**， **firstprivate**，**默认**，**共享**， **copyin**，和**缩减**子句，请参阅[部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。  
  
-   **OMP_NUM_THREADS**环境变量，[部分 4.2](../../parallel/openmp/4-2-omp-num-threads.md)第 48 页。  
  
-   **omp_set_dynamic**库函数，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)页 39 上。  
  
-   **OMP_DYNAMIC**环境变量，请参阅[部分 4.3](../../parallel/openmp/4-3-omp-dynamic.md)页 49 上。  
  
-   **omp_set_nested**函数中，请参阅[部分 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 40 页上。  
  
-   **OMP_NESTED**环境变量，请参阅[部分 4.4](../../parallel/openmp/4-4-omp-nested.md)页 49 上。  
  
-   **omp_set_num_threads**库函数，请参阅[部分 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)页 36 上。
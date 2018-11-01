---
title: 2.4.2 sections 构造
ms.date: 11/04/2016
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
ms.openlocfilehash: 2d9fca08eecd382c9d3df60159c13ac188a1ab85
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486809"
---
# <a name="242-sections-construct"></a>2.4.2 sections 构造

**各节**指令标识一个 noniterative 工作共享构造，它指定一组要在团队中的线程之间划分的构造。 每个部分由团队中的线程执行一次。 语法**各节**指令是按如下所示：

```
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

子句是以下值之一：

**private(** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**lastprivate(** *variable-list* **)**

**reduction(** *operator* **:**  *variable-list* **)**

**nowait**

每个部分的前面有**一节**指令，尽管**部分**指令是可选的第一个部分。 **一节**指令必须出现在的词法范围内**部分**指令。 末尾没有隐式屏障**各节**构造，除非**nowait**指定。

限制**各节**指令如下所示：

- 一个**一节**之外的词法范围不能出现指令**部分**指令。

- 只有一个**nowait**子句可出现在**部分**指令。

## <a name="cross-references"></a>交叉引用：

- **私有**， **firstprivate**， **lastprivate**，和**减少**子句，请参阅[部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。
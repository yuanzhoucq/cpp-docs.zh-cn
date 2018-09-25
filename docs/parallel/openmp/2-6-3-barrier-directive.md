---
title: 2.6.3 barrier 指令 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8654534143e6feed06e93406c8fe03983ee9c2fc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429144"
---
# <a name="263-barrier-directive"></a>2.6.3 barrier 指令

**屏障**指令会同步在团队中的所有线程。 当遇到，团队中的每个线程等待，直到所有其他已达到此点。 语法**屏障**指令是按如下所示：

```
#pragma omp barrier new-line
```

团队中的所有线程都遇到屏障后，团队中的每个线程开始后的屏障指令中并行执行的语句。 请注意，由于**屏障**指令不具有 C 语言语句作为其语法的一部分，有一些限制其放置在程序中。 请参阅[附录 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)正式语法。 下面的示例说明了这些限制。

```
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```
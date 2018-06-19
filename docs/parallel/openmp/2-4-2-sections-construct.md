---
title: 2.4.2 sections 构造 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20b24c5b7d2458294da6280acb2ba7e8be5961fb
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688279"
---
# <a name="242-sections-construct"></a>2.4.2 sections 构造
**部分**指令标识一个 noniterative 工作共享构造，用于指定要作为被除数线程在团队间的构造的一组。 每个部分由团队中的线程的执行一次。 语法**部分**指令是，如下所示：  
  
```  
#pragma omp sections [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-linestructured-block ]  
...  
}  
```  
  
 子句是以下项之一：  
  
 **private(** *variable-list* **)**  
  
 **firstprivate(** *variable-list* **)**  
  
 **lastprivate(** *variable-list* **)**  
  
 **reduction(** *operator* **:**  *variable-list* **)**  
  
 **nowait**  
  
 每个部分都附有**部分**指令，尽管**部分**指令是可选的第一个部分。 **部分**指令必须出现在的词法范围内**部分**指令。 在末尾没有隐式屏障**部分**构造，除非**nowait**指定。  
  
 限制到**部分**指令如下所示：  
  
-   A**部分**指令不能出现之外的词法范围**部分**指令。  
  
-   只有一个**nowait**子句可以出现在**部分**指令。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   **私有**， **firstprivate**， **lastprivate**，和**缩减**子句，请参阅[部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。
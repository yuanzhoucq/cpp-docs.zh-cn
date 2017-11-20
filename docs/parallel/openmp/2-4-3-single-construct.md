---
title: "2.4.3 single 构造 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3efb6c833227140440d327ea47906f8239769689
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="243-single-construct"></a>2.4.3 single 构造
**单个**指令标识一个构造，用于指定关联的结构化的块只能由团队 （不一定的主线程） 中的一个线程执行。 语法**单个**指令是，如下所示：  
  
```  
#pragma omp single [clause[[,] clause] ...] new-linestructured-block  
```  
  
 子句是以下项之一：  
  
 **私有 (** *变量列表* **)**  
  
 **firstprivate (** *变量列表* **)**  
  
 **copyprivate (** *变量列表* **)**  
  
 **nowait**  
  
 没有隐式屏障后的**单个**构造，除非**nowait**指定子句。  
  
 限制到**单个**指令如下所示：  
  
-   只有一个**nowait**子句可以出现在**单个**指令。  
  
-   **Copyprivate**必须不能使用带有子句**nowait**子句。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   **私有**， **firstprivate**，和**copyprivate**子句，请参阅[部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。
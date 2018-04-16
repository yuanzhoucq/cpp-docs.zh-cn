---
title: "2.7.2.2 firstprivate |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1e4f73b3cb418204008fda9962cf67797c8182f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="2722-firstprivate"></a>2.7.2.2 firstprivate
**Firstprivate**子句提供的提供的功能超集**私有**子句。 语法**firstprivate**子句是，如下所示：  
  
```  
firstprivate(variable-list)  
```  
  
 中指定的变量*变量列表*具有**私有**子句语义中, 所述[部分 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)第 25 页上。 初始化或构造发生就像它是一次每个线程之前的构造的线程的执行。 有关**firstprivate**并行构造的子句，新的私有对象的初始值是在遇到它的线程的并行构造之前存在的原始对象的值。 有关**firstprivate**工作共享构造上的子句，为每个线程执行的工作共享构造新的私有对象的初始值是时间点之前存在的原始对象的值，在同一线程遇到工作共享构造。 此外，对于 c + + 对象，每个线程的新专用对象是从原始对象构造的副本。  
  
 对限制**firstprivate**子句如下所示：  
  
-   中指定的变量**firstprivate**子句必须没有不完整类型或引用类型。  
  
-   具有指定为类类型的变量**firstprivate**必须具有可访问的明确的复制构造函数。  
  
-   变量的是专用的并行区域内或出现在**缩减**子句**并行**指令不能指定**firstprivate**上的子句将绑定到并行构造的工作共享指令。
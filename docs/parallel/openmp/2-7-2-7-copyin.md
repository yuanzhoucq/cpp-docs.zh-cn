---
title: 2.7.2.7 copyin |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ee711bfb24e7a2a1cbada1a7e01a243e204f4a8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689371"
---
# <a name="2727-copyin"></a>2.7.2.7 copyin
**Copyin**子句提供了一种机制来将同一值赋给**threadprivate**团队执行的并行区域中的每个线程的变量。 对于每个变量中指定**copyin**子句，团队的主线程中的变量的值进行复制，就像对并行区域的开始处的线程专用副本分配。 语法**copyin**子句是，如下所示：  
  
```  
  
copyin(  
variable-list  
)  
  
```  
  
 对限制**copyin**子句如下所示：  
  
-   中指定的变量**copyin**子句必须具有可访问的明确复制赋值运算符。  
  
-   中指定的变量**copyin**子句必须**threadprivate**变量。
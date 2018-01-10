---
title: "2.7.2.7 copyin |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5ba09b70b3a3591b1f8b427ac107576cfcac7935
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
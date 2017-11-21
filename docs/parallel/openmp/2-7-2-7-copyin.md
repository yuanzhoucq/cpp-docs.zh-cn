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
ms.openlocfilehash: cd296192146e76085e1b987e29a377eb621917ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
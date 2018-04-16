---
title: "2.7.2.8 copyprivate |Microsoft 文档"
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
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21d739fb3ead0512776cfd996b59f1ceab5e8250
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="2728-copyprivate"></a>2.7.2.8 copyprivate
**Copyprivate**子句提供了一种机制来使用的私有变量的其他成员广播来自团队的成员的一个值。 它是另一种共享的变量的值时提供此类共享的变量是非常困难的 （例如，在需要一个不同的变量在每个级别的递归）。 **Copyprivate**子句只能出现在**单个**指令。  
  
 语法**copyprivate**子句是，如下所示：  
  
```  
  
copyprivate(  
variable-list  
)  
  
```  
  
 效果**copyprivate**其变量列表中的变量上的子句发生在与关联的结构化块执行后**单个**构造，以及在任何中的线程之前团队已离开构造末尾屏障。 然后，在团队成员，以在每个变量中的所有其他线程*变量列表*，该变量将成为 （就像分配） 包含定义相应的值中的线程来执行构造的变量的结构化块。  
  
 限制到**copyprivate**子句如下所示：  
  
-   中指定的变量**copyprivate**子句不得出现在**私有**或**firstprivate**子句相同**单**指令。  
  
-   如果**单个**指令与**copyprivate**在并行区域的动态范围中遇到子句中的所有变量都指定**copyprivate**子句必须在封闭上下文中为私有。  
  
-   中指定的变量**copyprivate**子句必须具有可访问的明确复制赋值运算符。
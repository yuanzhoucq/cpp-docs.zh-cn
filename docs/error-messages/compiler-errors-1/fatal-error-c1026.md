---
title: "错误 C1026 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 187cfc1a59fc40a721be09aef9e78ef36c68f66a
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1026"></a>错误 C1026
分析器堆栈溢出，程序太复杂  
  
 分析程序所需的空间导致编译器堆栈溢出。  
  
 降低通过表达式的复杂性：  
  
-   减少在中的使用嵌套`for`和`switch`语句。 将更深入地嵌套的语句放置在单独的函数。  
  
-   中断性长涉及逗号运算符或函数调用的表达式。

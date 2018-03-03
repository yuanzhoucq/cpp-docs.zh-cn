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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 206e9843fd8566f4f595a46918548af14f119439
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1026"></a>错误 C1026
分析器堆栈溢出，程序太复杂  
  
 分析程序所需的空间导致编译器堆栈溢出。  
  
 降低通过表达式的复杂性：  
  
-   减少在中的使用嵌套`for`和`switch`语句。 将更深入地嵌套的语句放置在单独的函数。  
  
-   中断性长涉及逗号运算符或函数调用的表达式。
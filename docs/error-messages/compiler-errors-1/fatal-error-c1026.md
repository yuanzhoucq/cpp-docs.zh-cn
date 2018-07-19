---
title: 错误 C1026 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24c034d45b7f8b222471094f4580902ae1b8dc66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198100"
---
# <a name="fatal-error-c1026"></a>错误 C1026
分析器堆栈溢出，程序太复杂  
  
 分析程序所需的空间导致编译器堆栈溢出。  
  
 降低通过表达式的复杂性：  
  
-   减少在中的使用嵌套`for`和`switch`语句。 将更深入地嵌套的语句放置在单独的函数。  
  
-   中断性长涉及逗号运算符或函数调用的表达式。
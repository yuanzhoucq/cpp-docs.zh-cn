---
title: "副作用 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- expression evaluation, side effects
- side effects in expression evaluation
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e6e6dff87e447a3885906130b6a08286643d6a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="side-effects"></a>副作用
表达式的计算顺序由特定实现定义，但语言保证特定的计算顺序时除外（如[计算的优先级和顺序](../c-language/precedence-and-order-of-evaluation.md)中概述）。 例如，下列函数调用中将出现副作用：  
  
```  
add( i + 1, i = j + 2 );  
myproc( getc(), getc() );  
```  
  
 函数调用的参数可按任意顺序进行计算。 表达式 `i + 1` 可以在 `i = j + 2` 前计算，或者 `i = j + 2` 可以在 `i + 1` 前计算。 每种情况下的结果都不同。 同样，无法保证将哪些字符会实际传递到 `myproc`。 由于一元递增和递减运算涉及赋值，因此此类运算可能导致副作用，如以下示例中所示：  
  
```  
x[i] = i++;  
```  
  
 在此示例中，修改后的 `x` 值不可预知。 下标的值可以是 `i` 的新值或旧值。 结果因编译器或优化级别而异。  
  
 由于 C 未定义副作用的计算顺序，因此上面讨论的两种计算方式都是正确的，并且其中一个是可以实现的。 若要确保你的代码可移植且清晰明了，请避免使用依赖于副作用的特定计算顺序的语句。  
  
## <a name="see-also"></a>请参阅  
 [表达式计算](../c-language/expression-evaluation-c.md)
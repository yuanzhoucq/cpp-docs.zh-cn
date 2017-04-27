---
title: "前缀增量和减量运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: b6922d841af51b2133ba3a5fb1b7f6bdbcc02a62
ms.lasthandoff: 04/01/2017

---
# <a name="prefix-increment-and-decrement-operators"></a>前缀增量和减量运算符
当增量和减量运算符出现在操作数的前面时，一元运算符（`++` 和 **--**）称作“前缀”增量和减量运算符。 与前缀递增和递减相比，后缀递增和递减的优先级更高。 操作数必须具有整型、浮点型或指针类型且必须是可修改的左值表达式（不带 **const** 特性的表达式）。 结果为一个左值。  
  
 当运算符出现在其操作数的前面时，操作数会递增或递减，并且其新值为表达式的结果。  
  
 整型或浮动类型的操作数将按整数值 1 递增或递减。 结果的类型与操作数类型相同。 指针类型的操作数将按其所寻址对象的大小递增或递减。 递增的指针将指向下一个对象；递减的指针将指向上一个对象。  
  
## <a name="example"></a>示例  
 此示例阐释一元前缀递减运算符：  
  
```  
if( line[--i] != '\n' )  
    return;  
```  
  
 在此示例中，变量 `i` 在用作 `line` 的下标之前是递减的。  
  
## <a name="see-also"></a>另请参阅  
 [C 一元运算符](../c-language/c-unary-operators.md)

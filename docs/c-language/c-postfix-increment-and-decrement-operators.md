---
title: "C 后缀增量和减量运算符 | Microsoft Docs"
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
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
caps.latest.revision: 8
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
ms.openlocfilehash: a67e01fe0555a628c8b2178cc580bcaa8f84cd83
ms.lasthandoff: 04/01/2017

---
# <a name="c-postfix-increment-and-decrement-operators"></a>C 后缀增量和减量运算符
后缀递增和递减运算符的操作数是可修改的左值的标量类型。  
  
## <a name="syntax"></a>语法  
 *postfix-expression*:  
 *postfix-expression*  **++**  
  
 *postfix-expression*  **--**  
  
 后缀递增或递减运算的结果是操作数的值。 获取结果后，操作数的值将增加（或减少）。 以下代码演示了后缀递增运算符。  
  
```  
if( var++ > 0 )  
    *p++ = *q++;  
```  
  
 在本示例中，变量 `var` 先与 0 进行比较，然后增加。 如果 `var` 在增加之前为正数，则执行下一条语句。 首先，`q` 所指向的对象的值赋给 `p`所指向的对象。 然后，`q` 和 `p` 增加。  
  
## <a name="see-also"></a>另请参阅  
 [后缀增量和减量运算符：++ 和 --](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)

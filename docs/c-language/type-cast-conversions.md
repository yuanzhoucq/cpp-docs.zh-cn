---
title: "类型强制转换的转换 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data type conversion [C++], type-cast conversions
- conversions [C++], type-cast
- type casts
- explicit type conversions
- type casts [C++], about type-cast conversion
- type-cast conversions [C++]
ms.assetid: 57ab5902-f12f-4326-a2f6-6282f1d4025a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f402eb49e86c8d6d3ce6c332172375125f577a2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="type-cast-conversions"></a>类型强制转换的转换
可以使用类型强制转换来显式转换类型。  
  
 **语法**  
  
 *cast-expression*：  
 unary expression  
  
 **(**  *type-name*  **)**  *cast-expression*  
  
 *type-name*：  
 specifier-qualifier-list abstract-declarator opt  
  
 type-name 是类型，cast-expression 是要转换为该类型的值。 具有类型强制转换的表达式不是左值。 cast-expression 也会被转换，就好像它已分配到 type-name 类型的变量一样。 赋值的转换规则（在[赋值转换](../c-language/assignment-conversions.md)中进行了概述）也适用于类型强制转换。 下表显示了可强制转换为任何给定类型的类型。  
  
### <a name="legal-type-casts"></a>合法类型强制转换  
  
|目标类型|可能的源|  
|-----------------------|-----------------------|  
|整型|整数类型或浮点类型，或者指向对象的指针|  
|浮点|任何算术类型|  
|指向对象的指针或 (void **\***)|任何整数类型、(void **\***)、指向对象的指针或函数指针|  
|函数指针|任何整数类型、指向对象的指针或函数指针|  
|结构、联合或数组|无|  
|Void 类型|任何类型|  
  
 任何标识符均可强制转换为 `void` 类型。 但是，如果 type-cast 表达式中指定的类型不是 `void`，则要强制转换为该类型的标识符不能是 `void` 表达式。 任何表达式均可转换为 `void`，但 `void` 类型的表达式不能强制转换为其他类型。 例如，带有 `void` 返回类型的函数不能将其返回值强制转换为另一类型。  
  
 请注意，void **\*** 表达式具有指向 `void` 的类型指针，而不具有类型 `void`。 如果对象强制转换为 `void` 类型，则生成的表达式不能分配给任何项。 同样，type-cast 对象是不可接受的左值，因此不能对 type-cast 对象进行任何分配。  
  
 **Microsoft 专用**  
  
 只要标识符的大小不变，类型强制转换就可以是左值表达式。 有关左值表达式的信息，请参阅[左值和右值表达式](../c-language/l-value-and-r-value-expressions.md)。  
  
 **结束 Microsoft 专用**  
  
 可以使用强制转换将表达式转换为类型 `void`，但生成的表达式仅能用于不需要值的位置。 转换为 void **\*** 再转换回原始类型的对象指针将返回到其原始值。  
  
## <a name="see-also"></a>请参阅  
 [类型转换](../c-language/type-conversions-c.md)
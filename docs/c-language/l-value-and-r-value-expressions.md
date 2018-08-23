---
title: 左值和右值表达式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 654805750b3cd17e2157fa3710791493970b371f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386259"
---
# <a name="l-value-and-r-value-expressions"></a>左值和右值表达式
引用内存位置的表达式称为“左值”表达式。 左值表示存储区域的“locator”值或“left”值，并暗示它可以出现在等号 (**=**) 的左侧。 左值通常是标识符。  
  
 引用可修改的位置的表达式称为“可修改的左值”。 可修改的左值不能具有数组类型、不完整的类型或带 **const** 特性的类型。 对于要成为可修改的左值的结构和联合，它们不得具有带 **const** 特性的任何成员。 标识符的名称表示存储位置，而变量的值是存储在该位置的值。  
  
 如果标识符引用内存位置且如果其类型为算术、结构、联合或指针，则该标识符是可修改的左值。 例如，如果 `ptr` 是指向存储区域的指针，则 `*ptr` 是指定 `ptr` 所指向的存储区域的可修改的左值。  
  
 以下任一 C 表达式可为左值表达式：  
  
-   整型、浮点、指针、结构或联合类型的标识符  
  
-   计算结果不为数组的下标 (**[ ]**) 表达式  
  
-   成员选择表达式（**->** 或 **.**）  
  
-   不引用数组的一元间接寻址 (**\***) 表达式  
  
-   包含在括号内的左值表达式  
  
-   **const** 对象（不可修改的左值）  
  
 术语“右值”有时用于描述表达式的值以及将其与左值区分开来。 所有左值都是右值，但并不是所有右值都是左值。  
  
 **Microsoft 专用**  
  
 Microsoft C 包括对 ANSI C 标准的扩展，该扩展允许将左值的转换用作左值，只要对象的大小不通过转换来扩展即可。 （有关详细信息，请参阅[类型强制转换](../c-language/type-cast-conversions.md)。）下面的示例阐释了此功能：  
  
```  
char *p ;  
short  i;  
long l;  
  
(long *) p = &l ;       /* Legal cast   */  
(long) i = l ;          /* Illegal cast */  
```  
  
 Microsoft C 的默认设置是启用 Microsoft 扩展。 使用 /Za 编译器选项禁用这些扩展。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [操作数和表达式](../c-language/operands-and-expressions.md)
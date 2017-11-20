---
title: "C 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ternary operators
- operators [C]
- symbols, operators
- binary operators
- associativity of operators
- binary data, binary expressions
ms.assetid: 13bc4c8e-2dc9-4b23-9f3a-25064e8777ed
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fee64f3d5c5e26783745961f4aa5dc076dd472c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="c-operators"></a>C 运算符
C 运算符是 [C++ 的内置运算符](../cpp/cpp-built-in-operators-precedence-and-associativity.md)的子集。  
  
 有三种类型的运算符。 一元表达式包括附加到操作数的一元运算符或后跟表达式的 `sizeof` 关键字。 该表达式可以是变量的名称，也可以是强制转换表达式。 如果表达式是强制转换表达式，则它必须括在括号中。 二进制表达式包括通过二元运算符联接的两个操作数。 三元表达式包括通过条件表达式运算符联接的三个操作数。  
  
 C 包含以下一元运算符：  
  
|符号|名称|  
|------------|----------|  
|**- ~ !**|求反和补数运算符|  
|**\* &**|间接寻址运算符和 address-of 运算符|  
|`sizeof`|Size 运算符|  
|**+**|一元加运算符|  
|**++ --**|一元递增和减量运算符|  
  
 二元运算符从左至右关联。 C 提供了以下二进制运算符：  
  
|符号|名称|  
|------------|----------|  
|**\* / %**|乘法运算符|  
|**+ -**|相加运算符|  
|**<\< >>**|移位运算符|  
|**\<   >   \<=   >=   ==   !=**|关系运算符|  
|**&   &#124; ^**|位运算符|  
|**&&   &#124;&#124;**|逻辑运算符|  
|**，**|有序评估运算符|  
  
 Microsoft 16 位 C 编译器的早期版本所支持的基本运算符 (**:>**) 在 [C 语言语法摘要](../c-language/c-language-syntax-summary.md)中进行了介绍。  
  
 条件表达式运算符的优先级低于二进制表达式的优先级并与其在右关联上存在差异。  
  
 使用运算符的表达式还包括赋值表达式，该表达式使用一元或二元赋值运算符。 一元赋值运算符是增量 (`++`) 和减量 (**--**) 运算符；二元赋值运算符是简单赋值运算符 (**=**) 和复合赋值运算符。 每个复合赋值运算符是另一个二元运算符与简单赋值运算符的组合。  
  
## <a name="see-also"></a>另请参阅  
 [表达式和赋值](../c-language/expressions-and-assignments.md)
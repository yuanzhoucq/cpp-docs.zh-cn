---
title: 范围和可见性 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- scope, levels
- visibility
- file scope [C++]
ms.assetid: a019eb7c-66ed-46a7-bc9f-89a963930a56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b85f0ca180fc60b1281440845289d2f2a39d71af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389184"
---
# <a name="scope-and-visibility"></a>范围和可见性
标识符的“可见性”确定其可以引用的程序部分，即其“范围”。 标识符仅在其“范围”包含的程序部分中可见（即可使用），这可能仅限于（按限制增长的顺序）它显示在其中的文件、函数、块或函数原型。 标识符的范围是可使用名称的程序的一部分。 这有时被称为“词法范围”。 有四种范围：函数、文件、块和函数原型。  
  
 除标签之外，所有标识符的范围都由在其上进行声明的级别决定。 以下针对每种范围的规则将管理标识符在程序中的可见性：  
  
 文件范围  
 带文件范围的标识符的声明符或类型说明符显示在任何块或参数列表的外部，并且可以从其声明后的翻译单元中的任何位置进行访问。 带文件范围的标识符名称通常称为“全局”或“外部”。 全局标识符的范围开始于其定义或声明的点，结束于翻译单元的末尾。  
  
 函数范围  
 标签是唯一一种具有函数范围的标识符。 通过在语句中使用标签来隐式声明标签。 标签名称在函数中必须是唯一的。 （有关标签和标签名称的详细信息，请参阅 [goto 和 Labeled 语句](../c-language/goto-and-labeled-statements-c.md)。）  
  
 块范围  
 带块范围的标识符的声明符或类型说明符显示在块中或函数定义中的形参声明列表中。 它仅从其声明或定义的点到包含其声明或定义的块的结尾可见。 其范围限制为该块以及嵌入该块中的任何块，并结束于封闭该关联块的大括号处。 此类标识符有时称为“局部变量”。  
  
 函数原型范围  
 带函数原型范围的标识符的声明符或类型说明符显示在函数原型（不是函数声明的一部分）中的参数声明列表中。 其范围在函数声明符的末尾终止。  
  
 [存储类别](../c-language/c-storage-classes.md)中介绍了可使变量在其他源文件中可见的适当声明。 但是，使用 static 存储类说明符在外部级别声明的变量和函数仅在定义它们的源文件中可见。 所有其他函数都是全局可见的。  
  
## <a name="see-also"></a>请参阅  
 [生存期、范围、可见性和链接](../c-language/lifetime-scope-visibility-and-linkage.md)
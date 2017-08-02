---
title: "标记的计算 | Microsoft Docs"
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
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 72ed41d37222046f6dfa594aedaa30a0bb38756b
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="evaluation-of-tokens"></a>标记的计算
当编译器解释标记时，它在移到下一个标记之前，会在单个标记中包括尽可能多的字符。 由于此行为，编译器可能不会按预期方式解释标记（如果没有用空格正确分隔标记）。 考虑下面的表达式：  
  
```  
i+++j  
```  
  
 在此示例中，编译器首先从三个加号生成可能最长的运算符 (`++`)，然后将剩余的加号视为加法运算符 (`+`)。 因此，该表达式将解释为 `(i++) + (j)` 而不是 `(i) + (++j)`。 在此情况以及类似的情况下，使用空格和括号以避免多义性，并确保适当的表达式计算。  
  
 **Microsoft 专用**  
  
 C 编译器将 CTRL+Z 字符视为文件尾指示符。 它忽略 CTRL+Z 后的所有文本。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [C 标记](../c-language/c-tokens.md)

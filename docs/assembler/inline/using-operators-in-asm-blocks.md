---
title: "在 __asm 块中使用运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 27f01f38e25aac7a7418f24af24e2a58b2ec232b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="using-operators-in-asm-blocks"></a>在 __asm 块中使用运算符
## <a name="microsoft-specific"></a>Microsoft 专用  
 `__asm`块不能使用 C 或 c + + 特定运算符，如 **<<** 运算符。 但是，共享的运算符 C 和 MASM，如\*运算符，都会被解释为汇编语言运算符。 例如，外部`__asm`阻止，方括号 (**[]**) 都会被解释为封闭数组下标，C，自动缩放到数组中元素的大小。 在 `__asm` 块的内部，它们被视为 MASM 索引运算符，该运算符将从任何数据对象或标签（不仅仅是数组）中生成未缩放的字节偏移量。 下面的代码阐释了差异：  
  
```  
int array[10];  
  
__asm mov array[6], bx ;  Store BX at array+6 (not scaled)  
  
array[6] = 0;         /* Store 0 at array+24 (scaled) */  
```  
  
 不缩放对 `array` 的第一个引用，但缩放第二个引用。 请注意，你可以使用**类型**运算符以实现缩放基于常量。 例如，下面的语句是等效的：  
  
```  
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24  
  
array[6] = 0;                   /* Store 0 at array + 24 */  
```  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [在 __asm 块中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)
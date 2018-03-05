---
title: "goto 和标记语句 (C) (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- labeled statement
- statements, labeled
- goto keyword [C]
ms.assetid: 3d0473dc-4b18-4fcc-9616-31a38499d7d7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea0543a13d16850be4259d2d93f763dd0edcbda3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="goto-and-labeled-statements-c"></a>goto 和标记语句 (C)
`goto` 语句将控制权转交给一个标签。 给定标签必须位于同一函数中，并且只可以出现在同一函数中的一个语句前面。  
  
## <a name="syntax"></a>语法  
 *statement*：  
 labeled-statement  
  
 jump-statement  
  
 *jump-statement*:  
 goto  identifier  ;  
  
 *labeled-statement*:  
 identifier  :  statement  
  
 语句标签仅对 `goto` 语句有意义；在任何其他上下文中，在不考虑标签的情况下执行已标记的语句。  
  
 jump-statement 必须位于同一函数中，并且只能出现在同一函数中的一个语句前面。 跟在 `goto` 后的 identifier 名称集具有自己的命名空间，因此这些名称不影响其他标识符。 不能重新声明标签。 有关详细信息，请参阅[命名空间](../c-language/name-spaces.md)。  
  
 尽可能优先使用 break、continue 和 `return` 语句而不是 `goto` 是一种好的编程风格。 由于 break 语句只从一层循环中退出，因此从深度嵌套的循环中退出循环可能需要使用 `goto`。  
  
 此示例演示了 `goto` 语句：  
  
```  
// goto.c  
#include <stdio.h>  
  
int main()  
{  
    int i, j;  
  
    for ( i = 0; i < 10; i++ )  
    {  
        printf_s( "Outer loop executing. i = %d\n", i );  
        for ( j = 0; j < 3; j++ )  
        {  
            printf_s( " Inner loop executing. j = %d\n", j );  
            if ( i == 5 )  
                goto stop;  
        }  
    }  
  
    /* This message does not print: */  
    printf_s( "Loop exited. i = %d\n", i );  
  
    stop: printf_s( "Jumped to stop. i = %d\n", i );  
}  
```  
  
 在此示例中，当 `goto` 等于 5 时，`stop` 语句将控制权转交给标记为 `i` 的点。  
  
## <a name="see-also"></a>请参阅  
 [语句](../c-language/statements-c.md)
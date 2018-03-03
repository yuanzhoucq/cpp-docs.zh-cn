---
title: "最后一个字符串中的字符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b766bec977f35f9f346723cbaf3f62e48c8c878
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="last-character-in-a-string"></a>字符串中的最后一个字符
使用以下提示：  
  
-   尾字节范围重叠设置在许多情况下的 ASCII 字符。 可安全地用于按字节扫描任何控制字符 (小于 32)。  
  
-   请考虑以下监视器可能会检查以查看是否在字符串中的最后一个字符是反斜杠字符的代码行：  
  
    ```  
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?  
        // . . .  
    ```  
  
     因为`strlen`不是 MBCS 感知型，它返回的字节数，不字符数中的多字节字符串。 此外，请注意，在某些代码页 (932，例如)，\\(0x5c) 是一个有效的结尾字节 (`sz`是一个 C 字符串)。  
  
     一个可能的解决方案是将代码重写这种方式：  
  
    ```  
    char *pLast;  
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz  
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )  
        // . . .  
    ```  
  
     此代码使用 MBCS 函数`_mbsrchr`和`_mbsinc`。 由于这些函数是 mbcs，因此它们可以区分\\字符和一个尾字节\\。 如果字符串中的最后一个字符为 null (\0)，该代码执行某些操作。  
  
## <a name="see-also"></a>请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [字符赋值](../text/character-assignment.md)
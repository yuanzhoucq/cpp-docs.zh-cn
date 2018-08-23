---
title: 最后一个字符在字符串中的 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c5783fcdb1bccbfe7e2a316fa1ea4285519bb1b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593553"
---
# <a name="last-character-in-a-string"></a>字符串中的最后一个字符
使用以下提示：  
  
-   尾字节范围重叠在许多情况下设置的 ASCII 字符。 可安全地用于按字节扫描任何控制字符 (小于 32)。  
  
-   请考虑以下可能会检查以查看是否在字符串中的最后一个字符是反斜杠字符的代码行：  
  
    ```  
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?  
        // . . .  
    ```  
  
     因为`strlen`不是 MBCS 感知型，它将返回的字节，不是数字的字符，数中的多字节字符串。 另请注意，在某些代码页 (932，例如)，'\\(0x5c) 是一个有效的结尾字节 (`sz`是一个 C 字符串)。  
  
     一个可能的解决方案是重写此方法的代码：  
  
    ```  
    char *pLast;  
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz  
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )  
        // . . .  
    ```  
  
     此代码使用 MBCS 函数`_mbsrchr`和`_mbsinc`。 由于这些函数是 mbcs，它们可以区分 '\\字符和结尾字节\\。 如果在字符串中的最后一个字符为 null (\0)，代码将执行一些操作。  
  
## <a name="see-also"></a>请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [字符赋值](../text/character-assignment.md)
---
title: "字符串中的最后一个字符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字符串中的最后一个字符"
  - "MBCS [C++], 字符串中的最后一个字符"
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 字符串中的最后一个字符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用下列提示：  
  
-   在许多情况下，尾字节范围与 ASCII 字符集重叠。  对任何控制字符（小于 32）可以安全地使用按字节扫描。  
  
-   请看下列代码行，这些代码行可能检查字符串中最后一个字符是否为反斜杠字符：  
  
    ```  
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?  
        // . . .  
    ```  
  
     由于 `strlen` 不能识别 MBCS，因此在多字节字符串中它将返回字节数而非字符数。  同样，注意某些代码页（如 932）中“\\”\(0x5c\) 是一个有效的尾字节（`sz` 是一个 C 字符串）。  
  
     一个可能的解决方案是以下列方式重写代码：  
  
    ```  
    char *pLast;  
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz  
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )  
        // . . .  
    ```  
  
     此代码使用 MBCS 函数 `_mbsrchr` 和 `_mbsinc`。  由于这些函数能识别 MBCS，因此它们可以区分“\\”字符和尾字节“\\”。  当字符串中最后一个字符为空（“\\0”）时，代码将执行某些操作。  
  
## 请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [字符赋值](../text/character-assignment.md)
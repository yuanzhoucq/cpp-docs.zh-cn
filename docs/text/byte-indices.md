---
title: "字节索引 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字节索引 [C++]"
  - "MBCS [C++], 字节索引"
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# 字节索引
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用下列提示：  
  
-   在字符串中使用按字节索引引起的问题类似于指针操作所引起的问题。  请看下例，此例扫描字符串以查找反斜杠字符：  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i++;  
    ```  
  
     这可能索引尾字节，而非前导字节，因此可能不指向 `character`。  
  
-   使用 [\_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) 函数解决前面的问题：  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i += _mbclen ( rgch + i );  
    ```  
  
     它正确地索引到前导字节，因此能指向 `character`。  `_mbclen` 函数确定字符大小（单字节或双字节）。  
  
## 请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [字符串中的最后一个字符](../text/last-character-in-a-string.md)
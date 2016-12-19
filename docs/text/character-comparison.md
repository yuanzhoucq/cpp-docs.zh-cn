---
title: "字符比较 | Microsoft Docs"
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
  - "字符 [C++], 比较"
  - "比较字符"
  - "MBCS [C++], 字符比较"
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
caps.latest.revision: 8
caps.handback.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 字符比较
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用下列提示：  
  
-   将一个已知前导字节与一个 ASCII 字符进行比较的正确方法如下：  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   比较两个未知字符需要使用 Mbstring.h 中定义的一个宏：  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     它确保对一个双字节字符的两个字节都进行比较以判断是否相等。  
  
## 请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [缓冲区溢出](../text/buffer-overflow.md)
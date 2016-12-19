---
title: "递增和递减指针 | Microsoft Docs"
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
  - "递减指针"
  - "递增指针"
  - "MBCS [C++], 指针"
  - "指针 [C++], 多字节字符"
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 递增和递减指针
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用下列提示：  
  
-   指向前导字节而非尾字节。  通常使指针指向尾字节是不安全的。  通常向前扫描字符串比反向扫描更安全。  
  
-   存在可在整个字符上移动的指针增量\/减量函数和宏：  
  
    ```  
    sz1++;  
    ```  
  
     变成：  
  
    ```  
    sz1 = _mbsinc( sz1 );  
    ```  
  
     `_mbsinc` 和 `_mbsdec` 函数以 `character` 为单位正确地增量和减量，与字符大小无关。  
  
-   对于减量，需要将指针指向字符串前面，如下所示：  
  
    ```  
    sz2--;  
    ```  
  
     变成：  
  
    ```  
    sz2 = _mbsdec( sz2Head, sz2 );  
    ```  
  
     或者，头指针可以指向字符串中的有效字符，如：  
  
    ```  
    sz2Head < sz2  
    ```  
  
     必须使指针指向已知的有效前导字节。  
  
-   可能需要维护一个指向上一个字符的指针以便更快地调用 `_mbsdec`。  
  
## 请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [字节索引](../text/byte-indices.md)
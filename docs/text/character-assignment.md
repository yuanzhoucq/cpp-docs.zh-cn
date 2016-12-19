---
title: "字符赋值 | Microsoft Docs"
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
  - "字符 [C++], 赋值"
  - "MBCS [C++], 字符赋值"
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
caps.latest.revision: 9
caps.handback.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 字符赋值
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

请看下例，在此例中 `while` 循环扫描字符串，将除“X”外的所有字符复制到另一个字符串中：  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
        *sz1++ = *sz2++;  
    else  
        sz2++;  
}  
```  
  
 代码将位于 `sz2` 的字节复制到 `sz1` 指向的位置，然后递增 `sz1` 以接收下一个字节。  但如果 `sz2` 中的下一个字符为双字节字符，则 `sz1` 的赋值仅复制第一个字节。  下列代码使用一个可移植函数安全地复制字符，使用另一个可移植函数正确地递增 `sz1` 和 `sz2`：  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
    {  
        _mbscpy_s( sz1, 1, sz2 );  
        sz1 = _mbsinc( sz1 );  
        sz2 = _mbsinc( sz2 );  
    }  
    else  
        sz2 = _mbsinc( sz2 );  
}  
```  
  
## 请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [字符比较](../text/character-comparison.md)
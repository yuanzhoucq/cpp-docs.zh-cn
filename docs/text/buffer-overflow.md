---
title: "缓冲区溢出 | Microsoft Docs"
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
  - "缓冲区溢出 [C++]"
  - "缓冲区 [C++], 字符大小"
  - "MBCS [C++], 缓冲区溢出"
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# 缓冲区溢出
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将字符放到缓冲区中时，改变字符大小可能导致一些问题。  请看下列代码，此代码将 `sz` 字符串中的字符复制到 `rgch` 缓冲区中：  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 问题是：最后复制的一个字节是否是前导字节？  由于下列代码可能存在缓冲区溢出，因此并不能解决此问题：  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 `_mbccpy` 调用尝试正确执行，即无论此代码是单字节或双字节都将复制全部字符。  但它未考虑如果复制的最后一个字符为双字节宽，则可能不适合缓冲区。  正确的解决方案是：  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 此代码使用 `_mbclen` 测试由 `sz` 指向的当前字符的大小，从而在循环测试中测试可能的缓冲区溢出。  通过调用 `_mbsnbcpy` 函数，可以用单个代码行替换 `while` 循环中的代码。  例如：  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## 请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)
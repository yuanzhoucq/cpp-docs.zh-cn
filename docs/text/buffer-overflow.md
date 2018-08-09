---
title: 缓冲区溢出 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9bb362be360986371200c8cde292b3fff5acd7cd
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020182"
---
# <a name="buffer-overflow"></a>缓冲区溢出
将字符放入缓冲区时，不同的字符大小可能导致问题。 请考虑以下代码，它从字符串的字符复制， `sz`，到缓冲区中， `rgch`:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 问题是： 是的最后一个字节复制前导字节？ 以下原因可能使缓冲区溢出，不会解决问题：  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 `_mbccpy`调用尝试执行正确的做法 — 无论它是 1 或 2 个字节复制的完整字符。 但不考虑复制的最后一个字符可能不适合缓冲区，如果字符是 2 个字节宽的帐户。 正确的解决方案是：  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 此代码测试循环中可能发生缓冲区溢出测试，请使用`_mbclen`若要测试的当前指向的字符大小`sz`。 通过调用`_mbsnbcpy`函数，您可以替换中的代码**虽然**循环使用一行代码。 例如：  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## <a name="see-also"></a>请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)
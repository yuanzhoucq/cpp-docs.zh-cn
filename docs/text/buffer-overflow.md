---
title: 缓冲区溢出 |Microsoft 文档
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
ms.openlocfilehash: 13d01460e7ed9cb95d92303d82ea136803737331
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854647"
---
# <a name="buffer-overflow"></a>缓冲区溢出
将字符放入缓冲区时，改变字符大小可能会导致问题。 请考虑下面的代码，从字符串的字符复制， `sz`，到缓冲区中， `rgch`:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 问题： 最后一字节复制前导字节？ 以下由于潜在使缓冲区溢出，不会解决问题：  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 `_mbccpy`调用试图执行正确的操作-复制完整的字符，无论它是 1 或 2 个字节。 但不是会考虑复制的最后一个字符可能不适合缓冲区，如果字符是双字节宽的帐户。 正确的解决方案是：  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 此代码测试可能会发生缓冲区溢出循环中使用的测试`_mbclen`测试指向的当前字符的大小`sz`。 通过调用`_mbsnbcpy`函数，你可以替换中的代码`while`循环一行代码。 例如：  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## <a name="see-also"></a>请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)
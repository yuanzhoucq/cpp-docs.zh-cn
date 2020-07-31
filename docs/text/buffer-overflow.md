---
title: 缓冲区溢出
ms.date: 11/04/2016
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
ms.openlocfilehash: 71877ed770384190cb7f856567d9e7e845e3da19
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217319"
---
# <a name="buffer-overflow"></a>缓冲区溢出

将字符放入缓冲区时，改变字符大小可能会导致问题。 请考虑以下代码，它将字符从字符串复制 `sz` 到缓冲区中 `rgch` ：

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
    rgch[ cb++ ] = *sz++;
```

问题在于：最后一个字节是否复制了前导字节？ 下面的方法不能解决该问题，因为它可能会溢出缓冲区：

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

此 `_mbccpy` 调用尝试执行正确的操作，复制完整字符，无论是1字节还是2字节。 但如果字符是2字节宽，则不会考虑最后复制的最后一个字符可能不适合缓冲区。 正确的解决方案是：

```cpp
cb = 0;
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

此代码使用测试所指向的当前字符的大小，测试循环测试中可能的缓冲区溢出 `_mbclen` `sz` 。 通过调用 `_mbsnbcpy` 函数，可以将循环中的代码替换为 **`while`** 单个代码行。 例如：

```cpp
_mbsnbcpy( rgch, sz, sizeof( rgch ) );
```

## <a name="see-also"></a>另请参阅

[MBCS 编程提示](../text/mbcs-programming-tips.md)

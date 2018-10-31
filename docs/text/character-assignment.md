---
title: 字符赋值
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
ms.openlocfilehash: 9099382a212f9f7bd6c071f4e4d9a0c2bc8887de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435368"
---
# <a name="character-assignment"></a>字符赋值

请考虑以下示例中的，在其中**虽然**循环扫描一个字符串，将 X 以外的所有字符都复制到另一个字符串：

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
        *sz1++ = *sz2++;
    else
        sz2++;
}
```

代码将复制的字节位置`sz2`指向的位置`sz1`，然后递增`sz1`接收的下一个字节。 但是，如果中的下一个字符`sz2`是一个双字节字符，分配到`sz1`仅复制第一个字节。 下面的代码使用可移植的函数来安全地复制字符，另一个用于递增`sz1`和`sz2`正确：

```cpp
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

## <a name="see-also"></a>请参阅

[MBCS 编程提示](../text/mbcs-programming-tips.md)<br/>
[字符比较](../text/character-comparison.md)
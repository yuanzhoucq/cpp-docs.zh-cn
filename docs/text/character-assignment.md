---
title: 字符赋值
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
ms.openlocfilehash: 0f627f88ca2b1d3533d3690cd0316ee047a327ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217306"
---
# <a name="character-assignment"></a>字符赋值

请考虑以下示例，其中循环会 **`while`** 扫描字符串，将除 "X" 之外的所有字符复制到另一个字符串中：

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
        *sz1++ = *sz2++;
    else
        sz2++;
}
```

代码将中的字节复制 `sz2` 到所指向的位置 `sz1` ，然后递增 `sz1` 以接收下一个字节。 但如果中的下一个字符 `sz2` 是双字节字符，则赋值 `sz1` 仅复制第一个字节。 下面的代码使用可移植函数来安全地复制字符，并使用另一个函数来递增 `sz1` 和 `sz2` 正确地：

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

## <a name="see-also"></a>另请参阅

[MBCS 编程提示](../text/mbcs-programming-tips.md)<br/>
[字符比较](../text/character-comparison.md)

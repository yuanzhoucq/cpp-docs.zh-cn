---
title: 缓冲区操作
ms.date: 04/04/2018
f1_keywords:
- c.memory
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
ms.openlocfilehash: e8a449cbfa6a52ccc2346e2215ce187c09d677e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590497"
---
# <a name="buffer-manipulation"></a>缓冲区操作

通过以下例程逐字节使用内存区域。

## <a name="buffer-manipulation-routines"></a>缓冲区操作例程

|例程所返回的值|使用|
|-------------|---------|
|[_memccpy](../c-runtime-library/reference/memccpy.md)|将字符从一个缓冲区复制到另一个缓冲区，直到已复制给定字符或给定字符数|
|[memchr、wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|在指定的字符数范围内，将指针返回到缓冲区中给定字符的第一个匹配项|
|[memcmp、wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|比较两个缓冲区中指定数量的字符|
|[memcpy、wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)、[memcpy_s、wmemcpy_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|将指定数量的字符从一个缓冲区复制到另一个缓冲区|
|[_memicmp、_memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|在不考虑大小写的情况下比较两个缓冲区中指定数量的字符|
|[memmove、wmemmove](../c-runtime-library/reference/memmove-wmemmove.md)、[memmove_s、wmemmove_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|将指定数量的字符从一个缓冲区复制到另一个缓冲区|
|[memset、wmemset](../c-runtime-library/reference/memset-wmemset.md)|使用给定的字符初始化缓冲区中指定数量的字节|
|[_swab](../c-runtime-library/reference/swab.md)|交换数据字节并将其存储在指定位置|

当源和目标区域重叠时，仅 memmove 可保证正确复制完整源。

## <a name="see-also"></a>请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)

---
title: "缓冲区操作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.memory
dev_langs:
- C++
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 942d0f881ed6453921f6082024be5247a1bb1b65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="buffer-manipulation"></a>缓冲区操作
通过以下例程逐字节使用内存区域。  
  
### <a name="buffer-manipulation-routines"></a>缓冲区操作例程  
  
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
  
 当源和目标区域重叠时，仅 `memmove` 可保证正确复制完整源。  
  
## <a name="see-also"></a>请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)
---
title: "缓冲区操作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: d80ef9f47ea97443ba90af41bbe63cac31987367
ms.lasthandoff: 02/24/2017

---
# <a name="buffer-manipulation"></a>缓冲区操作
通过以下例程逐字节使用内存区域。  
  
### <a name="buffer-manipulation-routines"></a>缓冲区操作例程  
  
|例程|使用|.NET Framework 等效项|  
|-------------|---------|-------------------------------|  
|[_memccpy](../c-runtime-library/reference/memccpy.md)|将字符从一个缓冲区复制到另一个缓冲区，直到已复制给定字符或给定字符数|[System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)、[System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)|  
|[memchr、wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|在指定的字符数范围内，将指针返回到缓冲区中给定字符的第一个匹配项|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[memcmp、wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|比较两个缓冲区中指定数量的字符|[System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)、[System::String::Equals](https://msdn.microsoft.com/en-us/library/system.string.equals.aspx)|  
|[memcpy、wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)、[memcpy_s、wmemcpy_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|将指定数量的字符从一个缓冲区复制到另一个缓冲区|[System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)、[System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)|  
|[_memicmp、_memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|在不考虑大小写的情况下比较两个缓冲区中指定数量的字符|[System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)、[System::String::Equals](https://msdn.microsoft.com/en-us/library/system.string.equals.aspx)|  
|[memmove、wmemmove](../c-runtime-library/reference/memmove-wmemmove.md)、[memmove_s、wmemmove_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|将指定数量的字符从一个缓冲区复制到另一个缓冲区|[System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)|  
|[memset、wmemset](../c-runtime-library/reference/memset-wmemset.md)|使用给定的字符初始化缓冲区中指定数量的字节|[System::Buffer::SetByte](https://msdn.microsoft.com/en-us/library/system.buffer.setbyte.aspx)|  
|[_swab](../c-runtime-library/reference/swab.md)|交换数据字节并将其存储在指定位置|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
  
 当源和目标区域重叠时，仅 `memmove` 可保证正确复制完整源。  
  
## <a name="see-also"></a>另请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)

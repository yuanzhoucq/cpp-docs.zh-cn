---
title: "memcpy、wmemcpy | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- memcpy
- wmemcpy
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- wmemcpy
- memcpy
dev_langs: C++
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 312e4a63803f3661799c6ad832fdfee22af876c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="memcpy-wmemcpy"></a>memcpy、wmemcpy
在缓冲区之间复制字节。 提供这些函数的更多安全版本；请参阅 [memcpy_s、wmemcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
void *memcpy(  
   void *dest,  
   const void *src,  
   size_t count   
);  
wchar_t *wmemcpy(  
   wchar_t *dest,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dest`  
 新缓冲区。  
  
 `src`  
 从中进行复制操作的缓冲区。  
  
 `count`  
 要复制的字符数。  
  
## <a name="return-value"></a>返回值  
 `dest` 的值。  
  
## <a name="remarks"></a>备注  
 `memcpy` 从 `count` 中将 `src` 个字节复制到 `dest` 中；`wmemcpy` 复制 `count` 个宽字符（两个字节）。 如果源和目标重叠，则 `memcpy` 的行为是未定义的。 使用 `memmove` 处理重叠区域。  
  
> [!IMPORTANT]
>  确保目标缓冲区等于或大于源缓冲区。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
> [!IMPORTANT]
>  由于因不恰当使用 `memcpy` 而跟踪到了过多的缓冲区溢出以及因此产生的潜在安全漏洞，因此安全开发生命周期 (SDL) 将此函数列在“禁用”函数中。  你可能会发现一些 VC++ 库类仍然继续使用 `memcpy`。  此外，你还可能发现 VC++ 编译优化器有时会向 `memcpy` 发出调用。  Visual C++ 产品的开发需符合 SDL 过程，因此对此禁止函数的使用进行了仔细评估。  在库使用情况下，已经对调用进行了仔细审查，确保通过这些调用不会产生缓冲区溢出。  对于编译器，某些代码模式有时会被视为与 `memcpy` 模式相同，因此会被函数的调用替代。  在一些情况下，使用 `memcpy` 安全性并不比原始指令差，它们只是优化了对 `memcpy` 性能调整函数的调用。  与使用“安全”CRT 函数不保证安全性一样（仅难以加重不安全性），使用“禁止”函数并不能保证不出现危险（需更严格的审查以确保安全性）。  
>   
>  由于已经仔细审查了 VC++ 编译器和库对 `memcpy` 的使用，因此允许在不符合 SDL 的代码中出现这些调用。  应用程序源代码中引用的 `memcpy` 调用只有在安全专家审查了其使用时才符合 SDL。  
  
 仅当为了弃用函数而将常量 `memcpy` 先于包含语句定义时，才会弃用 `wmemcpy` 和 `_CRT_SECURE_DEPRECATE_MEMORY` 函数，如以下示例所示：  
  
```  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <memory.h>  
```  
  
 或  
  
```  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <wchar.h>  
```  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`memcpy`|\<memory.h> 或 \<string.h>|  
|`wmemcpy`|\<wchar.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
 有关如何使用 `memcpy` 的示例，请参阅 [memmove](../../c-runtime-library/reference/memmove-wmemmove.md)。  
  
## <a name="see-also"></a>请参阅  
 [缓冲区操作](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr、wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp、wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memmove、wmemmove](../../c-runtime-library/reference/memmove-wmemmove.md)   
 [memset、wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcpy_s、wcscpy_s、_mbscpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)   
 [strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)
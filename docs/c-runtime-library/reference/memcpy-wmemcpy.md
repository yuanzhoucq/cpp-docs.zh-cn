---
title: memcpy、wmemcpy
ms.date: 11/04/2016
api_name:
- memcpy
- wmemcpy
api_location:
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemcpy
- memcpy
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
ms.openlocfilehash: e9d947dc4e9ecea654e8cb16e957887fe4360161
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951851"
---
# <a name="memcpy-wmemcpy"></a>memcpy、wmemcpy

在缓冲区之间复制字节。 提供这些函数的更多安全版本；请参阅 [memcpy_s、wmemcpy_s](memcpy-s-wmemcpy-s.md)。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

dest<br/>
新缓冲区。

*src*<br/>
从中进行复制操作的缓冲区。

*count*<br/>
要复制的字符数。

## <a name="return-value"></a>返回值

*Dest*的值。

## <a name="remarks"></a>备注

**memcpy**将*计数*字节从*src*复制到*目标*;**wmemcpy**复制*计数*宽字符（两个字节）。 如果源和目标重叠，则**memcpy**的行为是不确定的。 使用**memmove**处理重叠区域。

> [!IMPORTANT]
> 确保目标缓冲区等于或大于源缓冲区。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

> [!IMPORTANT]
> 由于如此多的缓冲区溢出，进而导致**潜在的安全漏洞，因此**已被安全开发生命周期（SDL）的 "禁止" 函数列出。  你可能会发现一些 VC + + 库类继续使用**memcpy**。  此外，您可能会发现 VC + + 编译器优化器有时会发出对**memcpy**的调用。  Visual C++ 产品的开发需符合 SDL 过程，因此对此禁止函数的使用进行了仔细评估。  在库使用情况下，已经对调用进行了仔细审查，确保通过这些调用不会产生缓冲区溢出。  对于编译器，某些代码模式有时会被识别为与**memcpy**模式相同，因此会将其替换为对函数的调用。  在这种情况下，使用**memcpy**的方法并不比原始指令更安全;它们只是经过优化，可以调用性能优化的**memcpy**函数。  与使用“安全”CRT 函数不保证安全性一样（仅难以加重不安全性），使用“禁止”函数并不能保证不出现危险（需更严格的审查以确保安全性）。
>
> 由于 VC + + 编译器和库的**memcpy**使用已经过仔细审查，因此在其他符合 SDL 的代码中，允许进行这些调用。  在应用程序源代码中引入的**memcpy**调用只有在安全专家审查了该使用时才符合 SDL。

仅当在包含语句之前定义了常量 **_CRT_SECURE_DEPRECATE_MEMORY** ，才能弃用**memcpy**和**wmemcpy**函数，如以下示例中所示：

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <memory.h>
```

或

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**memcpy**|\<memory.h> 或 \<string.h>|
|**wmemcpy**|\<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

有关如何使用**memcpy**的示例，请参阅[memmove](memmove-wmemmove.md) 。

## <a name="see-also"></a>请参阅

[缓冲区操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr、wmemchr](memchr-wmemchr.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove、wmemmove](memmove-wmemmove.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[strcpy_s、wcscpy_s、_mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>

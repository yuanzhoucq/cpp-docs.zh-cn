---
title: memcpy、wmemcpy
ms.date: 11/04/2016
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wmemcpy
- memcpy
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
ms.openlocfilehash: afdb854bd28b55735cc6b5e26788307e2db0caa6
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211051"
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

*dest*<br/>
新缓冲区。

*src*<br/>
从中进行复制操作的缓冲区。

*count*<br/>
要复制的字符数。

## <a name="return-value"></a>返回值

值*dest*。

## <a name="remarks"></a>备注

**memcpy**副本*计数*个字节从*src*到*dest*;**wmemcpy**副本*计数*宽字符 （两个字节为单位）。 如果源和目标重叠的行为**memcpy**是不确定的。 使用**memmove**处理重叠区域。

> [!IMPORTANT]
> 确保目标缓冲区等于或大于源缓冲区。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/desktop/SecBP/avoiding-buffer-overruns)。

> [!IMPORTANT]
> 由于具有这么多的缓冲区溢出以及因此产生的潜在安全漏洞，到使用不当的已跟踪**memcpy**，此函数列出在"禁止"函数之间的安全开发生命周期 (SDL)。  您可能会发现一些 VC + + 库类继续使用**memcpy**。  此外，您可能会观察到 VC + + 编译器优化器有时会发出对调用**memcpy**。  Visual C++ 产品的开发需符合 SDL 过程，因此对此禁止函数的使用进行了仔细评估。  在库使用情况下，已经对调用进行了仔细审查，确保通过这些调用不会产生缓冲区溢出。  对于编译器，有时某些代码模式被识别为相同的模式**memcpy**，并因此将替换为对函数的调用。  在这种情况下，使用**memcpy**是安全性并不比原始指令; 它们只是优化性能调整的调用**memcpy**函数。  与使用“安全”CRT 函数不保证安全性一样（仅难以加重不安全性），使用“禁止”函数并不能保证不出现危险（需更严格的审查以确保安全性）。
>
> 因为**memcpy** VC + + 编译器和库的使用情况因此要认真仔细审查、 格式不符合 SDL 的代码中允许这些调用。  **memcpy**时使用已审阅的安全专家，在应用程序源代码中引入的调用才符合 SDL。

**Memcpy**并**wmemcpy**函数将仅会弃用常量 **_CRT_SECURE_DEPRECATE_MEMORY**顺序中的包含语句之前定义要为不推荐使用，例如以下示例所示的函数：

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

请参阅[memmove](memmove-wmemmove.md)有关如何使用的示例**memcpy**。

## <a name="see-also"></a>请参阅

[缓冲区操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr、wmemchr](memchr-wmemchr.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove、wmemmove](memmove-wmemmove.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[strcpy_s、wcscpy_s、_mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>

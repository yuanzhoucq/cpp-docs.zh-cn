---
title: memcpy、wmemcpy | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9880bdbc608933a1b6cfffe3473a9b07f0252ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405351"
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
> 确保目标缓冲区等于或大于源缓冲区。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

> [!IMPORTANT]
> 因为这么多的缓冲区溢出以及因此产生的潜在安全漏洞，跟踪到了过不当使用**memcpy**，此函数列在"禁用"函数的安全开发生命周期 (SDL)。  您可能会发现一些 VC + + 库类继续使用**memcpy**。  此外，你可能会观察 VC + + 编译器优化器有时发出调用**memcpy**。  Visual C++ 产品的开发需符合 SDL 过程，因此对此禁止函数的使用进行了仔细评估。  在库使用情况下，已经对调用进行了仔细审查，确保通过这些调用不会产生缓冲区溢出。  对于编译器，某些代码模式有时会被相同的模式**memcpy**，并因此替换为对函数的调用。  在这种情况下，使用**memcpy**是安全性并不比原始说明进行操作以后已经是; 它们只需优化性能优化的调用**memcpy**函数。  与使用“安全”CRT 函数不保证安全性一样（仅难以加重不安全性），使用“禁止”函数并不能保证不出现危险（需更严格的审查以确保安全性）。
>
> 因为**memcpy**已因此仔细审查了 VC + + 编译器和库的使用情况，这些调用允许在不符合 SDL 的代码。  **memcpy**调用引入应用程序源代码中使用评审了安全专家时才符合 SDL。

**Memcpy**和**wmemcpy**如果才会弃用函数常量 **_CRT_SECURE_DEPRECATE_MEMORY**之前以便于包含语句定义函数已弃用，如以下示例所示：

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

|例程|必需的标头|
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

---
title: memmove、wmemmove | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- memmove
- wmemmove
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
- ntdll.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- memmove
- wmemmove
dev_langs:
- C++
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11f474675d8ba5b370b1f13f048e989d9c283bde
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204623"
---
# <a name="memmove-wmemmove"></a>memmove、wmemmove

将一个缓冲区移到另一个缓冲区。 提供这些函数的更多安全版本；请参阅 [memmove_s、wmemmove_s](memmove-s-wmemmove-s.md)。

## <a name="syntax"></a>语法

```C
void *memmove(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemmove(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>参数

*dest*<br/>
目标对象。

*src*<br/>
源对象。

*count*<br/>
字节数 (**memmove**) 或多个字符 (**wmemmove**) 复制。

## <a name="return-value"></a>返回值

值*dest*。

## <a name="remarks"></a>备注

副本*计数*字节 (**memmove**) 或多个字符 (**wmemmove**) 从*src*到*dest*。 如果源区域的某些区域和目标重叠，则两个函数都可确保在重叠区域中的原始源字节被覆盖之前对其进行复制。

**安全说明** 确保目标缓冲区的大小等于或大于源缓冲区的大小。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/desktop/SecBP/avoiding-buffer-overruns)。

**Memmove**并**wmemmove**函数将仅会弃用常量 **_CRT_SECURE_DEPRECATE_MEMORY**顺序中的包含语句之前定义要为不推荐使用，例如以下示例所示的函数：

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <string.h>
```

或

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**memmove**|\<string.h>|
|**wmemmove**|\<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_memcpy.c
// Illustrate overlapping copy: memmove
// always handles it correctly; memcpy may handle
// it correctly.
//

#include <memory.h>
#include <string.h>
#include <stdio.h>

char str1[7] = "aabbcc";

int main( void )
{
   printf( "The string: %s\n", str1 );
   memcpy( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );

   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string

   printf( "The string: %s\n", str1 );
   memmove( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );
}
```

```Output
The string: aabbcc
New string: aaaabb
The string: aabbcc
New string: aaaabb
```

## <a name="see-also"></a>请参阅

[缓冲区操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy、wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy、wcscpy、_mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>

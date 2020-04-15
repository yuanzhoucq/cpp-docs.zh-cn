---
title: memcpy_s、wmemcpy_s
ms.date: 4/2/2020
api_name:
- memcpy_s
- wmemcpy_s
- _o_memcpy_s
- _o_wmemcpy_s
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemcpy_s
- memcpy_s
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
ms.openlocfilehash: dc5e49115b65b6883e55df13d0610231a87c1c55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333337"
---
# <a name="memcpy_s-wmemcpy_s"></a>memcpy_s、wmemcpy_s

在缓冲区之间复制字节。 如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述，这些版本的 [memcpy、wmemcpy](memcpy-wmemcpy.md) 具有安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t memcpy_s(
   void *dest,
   size_t destSize,
   const void *src,
   size_t count
);
errno_t wmemcpy_s(
   wchar_t *dest,
   size_t destSize,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>参数

dest**<br/>
新缓冲区。

*放大缩小字体功能 放大缩小字体功能*<br/>
目标缓冲区的大小，memcpy_s 以字节为单位），wmemcpy_s 以宽字符 (wchar_t) 为单位。

*src*<br/>
从中进行复制操作的缓冲区。

*count*<br/>
要复制的字符数。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。

### <a name="error-conditions"></a>错误条件

|dest**|*放大缩小字体功能 放大缩小字体功能*|*src*|*count*|返回值|*dest*的内容|
|------------|----------------|-----------|---|------------------|------------------------|
|any|any|any|0|0|未修改|
|**空**|any|any|非零|**埃因瓦尔**|未修改|
|any|any|**空**|非零|**埃因瓦尔**|*dest*被归零|
|any|< *计数*|any|非零|**ERANGE**|*dest*被归零|

## <a name="remarks"></a>备注

**memcpy_s**副本*计数*字节从*src*到*dest*;**wmemcpy_s**副本*计数*宽字符（两个字节）。 如果源和目标重叠，则**memcpy_s**的行为未定义。 使用**memmove_s**来处理重叠区域。

这些函数验证其参数。 如果*计数*是非零，并且*dest*或*src*是空指针，或者*destSize*小于*计数*，则这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数将返回**EINVAL**或**ERANGE，** 并将**errno**设置为返回值。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**memcpy_s**|\<memory.h> 或 \<string.h>|
|**wmemcpy_s**|\<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_memcpy_s.c
// Copy memory in a more secure way.

#include <memory.h>
#include <stdio.h>

int main()
{
   int a1[10], a2[100], i;
   errno_t err;

   // Populate a2 with squares of integers
   for (i = 0; i < 100; i++)
   {
      a2[i] = i*i;
   }

   // Tell memcpy_s to copy 10 ints (40 bytes), giving
   // the size of the a1 array (also 40 bytes).
   err = memcpy_s(a1, sizeof(a1), a2, 10 * sizeof (int) );
   if (err)
   {
      printf("Error executing memcpy_s.\n");
   }
   else
   {
     for (i = 0; i < 10; i++)
       printf("%d ", a1[i]);
   }
   printf("\n");
}
```

```Output
0 1 4 9 16 25 36 49 64 81
```

## <a name="see-also"></a>另请参阅

[缓冲区操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr、wmemchr](memchr-wmemchr.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove、wmemmove](memmove-wmemmove.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[strcpy、wcscpy、_mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>

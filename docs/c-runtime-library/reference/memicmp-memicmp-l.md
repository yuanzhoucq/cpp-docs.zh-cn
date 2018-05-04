---
title: _memicmp、_memicmp_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _memicmp_l
- _memicmp
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _memicmp
- memicmp_l
- _memicmp_l
dev_langs:
- C++
helpviewer_keywords:
- memicmp function
- _memicmp function
- memicmp_l function
- _memicmp_l function
ms.assetid: 0a6eb945-4077-4f84-935d-1aaebe8db8cb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3ddd09fbfbfd4de095bfbc67bc669cf9c794dee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="memicmp-memicmpl"></a>_memicmp、_memicmp_l

比较两个缓冲区中的字符（不区分大小写）。

## <a name="syntax"></a>语法

```C
int _memicmp(
   const void *buffer1,
   const void *buffer2,
   size_t count
);
int _memicmp_l(
   const void *buffer1,
   const void *buffer2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*buffer1*<br/>
第一个缓冲区。

*buffer2*<br/>
第二个缓冲区。

*count*<br/>
字符数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回值指示缓冲区之间的关系。

|返回值|buf1 和 buf2 的第一个计数字节的关系|
|------------------|--------------------------------------------------------|
|< 0|*buffer1*小于*buffer2*。|
|0|*buffer1*等于*buffer2*。|
|> 0|*buffer1*大于*buffer2*。|
|**_NLSCMPERROR**|出现了错误。|

## <a name="remarks"></a>备注

**_Memicmp**函数将进行比较的第一个*计数*的两个缓冲区的字符*buffer1*和*buffer2*逐字节。 该比较不区分大小写。

如果任一*buffer1*或*buffer2*是 null 指针，此函数调用无效参数处理程序中, 所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，函数将返回 **_NLSCMPERROR**和设置**errno**到**EINVAL**。

**_memicmp**的区域设置相关行为，则使用当前区域设置 **_memicmp_l**具有完全相同，只不过它改用已传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_memicmp**|\<memory.h> 或 \<string.h>|
|**_memicmp_l**|\<memory.h> 或 \<string.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_memicmp.c
// This program uses _memicmp to compare
// the first 29 letters of the strings named first and
// second without regard to the case of the letters.

#include <memory.h>
#include <stdio.h>
#include <string.h>

int main( void )
{
   int result;
   char first[] = "Those Who Will Not Learn from History";
   char second[] = "THOSE WHO WILL NOT LEARN FROM their mistakes";
   // Note that the 29th character is right here ^

   printf( "Compare '%.29s' to '%.29s'\n", first, second );
   result = _memicmp( first, second, 29 );
   if( result < 0 )
      printf( "First is less than second.\n" );
   else if( result == 0 )
      printf( "First is equal to second.\n" );
   else if( result > 0 )
      printf( "First is greater than second.\n" );
}
```

```Output
Compare 'Those Who Will Not Learn from' to 'THOSE WHO WILL NOT LEARN FROM'
First is equal to second.
```

## <a name="see-also"></a>请参阅

[缓冲区操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr、wmemchr](memchr-wmemchr.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy、wmemcpy](memcpy-wmemcpy.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>

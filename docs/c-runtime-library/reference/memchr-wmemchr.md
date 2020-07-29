---
title: memchr、wmemchr
ms.date: 03/31/2019
api_name:
- wmemchr
- memchr
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
- memchr
- wmemchr
helpviewer_keywords:
- memchr function
- wmemchr function
ms.assetid: 5a348581-28f1-4256-8434-687245f7fc9f
ms.openlocfilehash: b4640004526eda4ff26e9601e15298bcb8ba3c79
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232464"
---
# <a name="memchr-wmemchr"></a>memchr、wmemchr

在缓冲区中查找字符。

## <a name="syntax"></a>语法

```C
void *memchr(
   const void *buffer,
   int c,
   size_t count
); // C only
void *memchr(
   void *buffer,
   int c,
   size_t count
); // C++ only
const void *memchr(
   const void *buffer,
   int c,
   size_t count
); // C++ only
wchar_t *wmemchr(
   const wchar_t * buffer,
   wchar_t c,
   size_t count
); // C only
wchar_t *wmemchr(
   wchar_t * buffer,
   wchar_t c,
   size_t count
); // C++ only
const wchar_t *wmemchr(
   const wchar_t * buffer,
   wchar_t c,
   size_t count
); // C++ only
```

### <a name="parameters"></a>参数

*宽限*<br/>
指向缓冲区的指针。

*ansi-c*<br/>
要查找的字符。

*计数*<br/>
要检查的字符数。

## <a name="return-value"></a>返回值

如果成功，则返回指向*缓冲区*中第一个*c*位置的指针。 否则，它将返回 NULL。

## <a name="remarks"></a>备注

`memchr`并 `wmemchr` 在*缓冲区*的第一个*计数*字符中查找*c*的第一个匹配项。 它在找到*c*或已检查第一个*计数*字符时停止。

在 C 中，这些函数采用 **`const`** 第一个参数的指针。 在 C++ 中，有两个重载可用。 采用指向的指针的重载 **`const`** 返回指向的指针 **`const`** ; 采用指向非的指针的版本返回指向 **`const`** 非的指针 **`const`** 。 \_ \_ \_ \_ 如果 **`const`** 这些函数的和非版本都可用，则会定义宏 CRT 常量正确重载 **`const`** 。 如果 **`const`** 在 c + + 中需要两个 c + + 重载的非行为，请定义符号 \_ CONST \_ 返回。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`memchr`|\<memory.h> 或 \<string.h>|
|`wmemchr`|\<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_memchr.c

#include <memory.h>
#include <stdio.h>

int  ch = 'r';
char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int result;
   printf( "String to be searched:\n             %s\n", string );
   printf( "             %s\n             %s\n\n", fmt1, fmt2 );

   printf( "Search char: %c\n", ch );
   pdest = memchr( string, ch, sizeof( string ) );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "Result:      %c found at position %d\n", ch, result );
   else
      printf( "Result:      %c not found\n" );
}
```

### <a name="output"></a>Output

```Output
String to be searched:
             The quick brown dog jumps over the lazy fox
                      1         2         3         4         5
             12345678901234567890123456789012345678901234567890

Search char: r
Result:      r found at position 12
```

## <a name="see-also"></a>请参阅

[缓冲区操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy、wmemcpy](memcpy-wmemcpy.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[strchr、wcschr、_mbschr、_mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>

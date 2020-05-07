---
title: _mktemp、_wmktemp
ms.date: 4/2/2020
api_name:
- _wmktemp
- _mktemp
- _o__mktemp
- _o__wmktemp
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
helpviewer_keywords:
- _wmktemp function
- _mktemp function
- files [C++], temporary
- tmktemp function
- _tmktemp function
- wmktemp function
- mktemp function
- temporary files [C++]
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
ms.openlocfilehash: 536a63841c6e29fa003eb8b99c896f6d1cf5519f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919091"
---
# <a name="_mktemp-_wmktemp"></a>_mktemp、_wmktemp

创建唯一的文件名。 提供这些函数的更多安全版本，请参阅 [_mktemp_s、_wmktemp_s](mktemp-s-wmktemp-s.md)。

## <a name="syntax"></a>语法

```C
char *_mktemp(
   char *nameTemplate
);
wchar_t *_wmktemp(
   wchar_t *nameTemplate
);
template <size_t size>
char *_mktemp(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
wchar_t *_wmktemp(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>参数

*nameTemplate*<br/>
文件名模式。

## <a name="return-value"></a>返回值

其中每个函数都会返回指向修改后的 nameTemplate 的指针。 如果*nameTemplate*的格式不正确，或者无法从给定的 nameTemplate 创建更多唯一名称，则函数将返回**NULL** 。

## <a name="remarks"></a>备注

**_Mktemp**函数通过修改*nameTemplate*参数创建唯一的文件名。 **_mktemp**会根据需要自动处理多字节字符串参数，根据运行时系统当前使用的多字节代码页识别多字节字符序列。 **_wmktemp**是 **_mktemp**的宽字符版本;**_wmktemp**的参数和返回值是宽字符字符串。 除非 **_wmktemp**不处理多字节字符字符串，否则 **_wmktemp**和 **_mktemp**的行为相同。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

*NameTemplate*参数的格式为*base*XXXXXX，其中*base*是你提供的新文件名的一部分，每个 X 是 **_mktemp**提供的字符的占位符。 *NameTemplate*中的每个占位符字符都必须是大写的 x。 **_mktemp**保留*基*，并将第一个尾随 X 替换为字母字符。 **_mktemp**将以下尾随 X 替换为五位值;此值是标识调用进程的唯一数字，或在多线程程序中调用线程。

**_Mktemp**的每个成功调用都将修改*nameTemplate*。 在来自具有相同*nameTemplate*参数的相同进程或线程的每个后续调用中， **_mktemp**将检查与以前的调用中的 **_mktemp**返回的名称匹配的文件名。 如果给定名称中不存在任何文件， **_mktemp**将返回该名称。 如果所有以前返回的名称都存在文件， **_mktemp**会通过将之前返回的名称中使用的字母字符替换为下一个可用小写字母（按顺序从 "a" 到 "z"）来创建新名称。 例如，如果*base*为：

> **fn**

**_mktemp**提供的五位数值为12345，则返回的第一个名称为：

> **fna12345**

如果此名称用于创建文件 FNA12345，但该文件仍然存在，则在调用时返回的下一个名称与*nameTemplate*具有相同*基准*的相同进程或线程相同：

> **fnb12345**

如果 FNA12345 不存在，则返回的下一个名称又是：

> **fna12345**

**_mktemp**可以为*base*和*nameTemplate*值的任意给定组合创建最多26个唯一文件名。 因此，FNZ12345 是 **_mktemp**可以为本示例中使用的*base*和*nameTemplate*值创建的最后一个唯一文件名。

失败时，将设置**errno** 。 如果*nameTemplate*具有无效的格式（例如，少于6个 X），则**errno**将设置为**EINVAL**。 如果 **_mktemp**因为所有26个可能的文件名都已存在而无法创建唯一名称，则 **_mktemp**将 nameTemplate 设置为空字符串并返回**EEXIST**。

在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<io.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_mktemp.c
// compile with: /W3
/* The program uses _mktemp to create
* unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>
#include <errno.h>

char *template = "fnXXXXXX";
char *result;
char names[27][9];

int main( void )
{
   int i;
   FILE *fp;

   for( i = 0; i < 27; i++ )
   {
      strcpy_s( names[i], sizeof( names[i] ), template );
      /* Attempt to find a unique filename: */
      result = _mktemp( names[i] );  // C4996
      // Note: _mktemp is deprecated; consider using _mktemp_s instead
      if( result == NULL )
      {
         printf( "Problem creating the template\n" );
         if (errno == EINVAL)
         {
             printf( "Bad parameter\n");
         }
         else if (errno == EEXIST)
         {
             printf( "Out of unique filenames\n");
         }
      }
      else
      {
         fopen_s( &fp, result, "w" );
         if( fp != NULL )
            printf( "Unique filename is %s\n", result );
         else
            printf( "Cannot open %s\n", result );
         fclose( fp );
      }
   }
}
```

```Output
Unique filename is fna03912
Unique filename is fnb03912
Unique filename is fnc03912
Unique filename is fnd03912
Unique filename is fne03912
Unique filename is fnf03912
Unique filename is fng03912
Unique filename is fnh03912
Unique filename is fni03912
Unique filename is fnj03912
Unique filename is fnk03912
Unique filename is fnl03912
Unique filename is fnm03912
Unique filename is fnn03912
Unique filename is fno03912
Unique filename is fnp03912
Unique filename is fnq03912
Unique filename is fnr03912
Unique filename is fns03912
Unique filename is fnt03912
Unique filename is fnu03912
Unique filename is fnv03912
Unique filename is fnw03912
Unique filename is fnx03912
Unique filename is fny03912
Unique filename is fnz03912
Problem creating the template.
Out of unique filenames.
```

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile](tmpfile.md)<br/>

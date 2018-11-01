---
title: _mktemp、_wmktemp
ms.date: 11/04/2016
apiname:
- _wmktemp
- _mktemp
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 9dbaba9e4a68523c0d79762c6a7ff54c238e397d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554152"
---
# <a name="mktemp-wmktemp"></a>_mktemp、_wmktemp

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

每个函数返回指向修改后的 nameTemplate 的指针。 该函数将返回**NULL**如果*nameTemplate*格式不正确，或者可以从给定 nameTemplate 创建没有更多的唯一名称。

## <a name="remarks"></a>备注

**_Mktemp**函数创建唯一的文件名通过修改*nameTemplate*参数。 **_mktemp**自动处理多字节字符字符串参数，根据需要，通过运行时系统识别根据当前正在使用的多字节代码页的多字节字符序列。 **_wmktemp**是宽字符版本 **_mktemp**; 的自变量和返回值 **_wmktemp**都是宽字符字符串。 **_wmktemp**并 **_mktemp**行为方式相同，不同之处在于 **_wmktemp**不处理多字节字符字符串。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

*NameTemplate*自变量具有窗体*基 * * XXXXXX*，其中*基*为您提供的新文件名称的一部分并且每个 X 为提供的字符的占位符 **_mktemp**。 中的每个占位符字符*nameTemplate*必须是大写 x。 **_mktemp**保留*基*并将第一个尾随 X 替换为字母字符。 **_mktemp**替换将后面的尾随 five 位数字值; 此值是标识调用进程中，或在多线程程序中，调用线程的唯一编号。

每次成功调用 **_mktemp**修改*nameTemplate*。 在每个后续调用中从同一个进程或线程具有相同*nameTemplate*自变量， **_mktemp**检查返回的名称匹配的文件名称 **_mktemp**中以前的调用。 如果给定名称的文件不存在 **_mktemp**返回该名称。 如果文件存在之前返回的所有名称， **_mktemp**通过将它与下一个可用小写字母，按顺序，从 a 到 z 的以前返回名称中使用的字母字符替换为创建的新名称。 例如，如果*基*是：

> **fn**

和提供的五位数值 **_mktemp**为 12345，返回的第一个名称为：

> **fna12345**

如果此名称用于创建文件 FNA12345 并且此文件仍然存在，从相同进程或线程具有相同调用返回的下一个名称*基*有关*nameTemplate*是：

> **fnb12345**

如果 FNA12345 不存在，则返回的下一个名称又是：

> **fna12345**

**_mktemp**可以创建最多 26 的唯一文件名的任意给定组合*基*并*nameTemplate*值。 因此，FNZ12345 是最后一个唯一的文件名 **_mktemp**可以为创建*基*并*nameTemplate*在此示例中使用的值。

在失败时， **errno**设置。 如果*nameTemplate*具有无效的格式 (例如，少于 6 个 X)， **errno**设置为**EINVAL**。 如果 **_mktemp**不能创建唯一的名称，因为所有 26 可能的文件名称已存在，所以 **_mktemp** nameTemplate 设置为空字符串并返回**EEXIST**。

在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<io.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile](tmpfile.md)<br/>

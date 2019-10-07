---
title: fscanf、_fscanf_l、fwscanf、_fwscanf_l
ms.date: 11/04/2016
api_name:
- fscanf
- _fwscanf_l
- _fscanf_l
- fwscanf
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fscanf
- fwscanf
- _ftscanf_l
- _fwscanf_l
- _ftscanf
- _fscanf_l
helpviewer_keywords:
- fscanf function
- fwscanf function
- formatted data [C++], reading from streams
- ftscanf_l function
- _ftscanf_l function
- _fwscanf_l function
- data [CRT], reading from streams
- _fscanf_l function
- ftscanf function
- fscanf_l function
- streams [C++], reading formatted data from
- _ftscanf function
- fwscanf_l function
ms.assetid: 9004e978-6c5f-4bb2-98fd-51e5948933f2
ms.openlocfilehash: 1c143cbc1bf642e7efc6f10b9615fdaca8a236d1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956619"
---
# <a name="fscanf-_fscanf_l-fwscanf-_fwscanf_l"></a>fscanf、_fscanf_l、fwscanf、_fwscanf_l

从流中读取带格式的数据。 这些函数的更安全版本已发布。请参阅 [fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)。

## <a name="syntax"></a>语法

```C
int fscanf(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fscanf_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int fwscanf(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwscanf_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>参数

*stream*<br/>
指向**文件**结构的指针。

*format*<br/>
窗体控件字符串。

*实际*<br/>
可选参数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

每个函数都将返回成功转换并分配的字段数；返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。 如果发生错误，或者在第一次转换之前到达文件流的末尾，则返回值为**fscanf**和**fwscanf**的**EOF** 。

这些函数验证其参数。 如果*stream*或*format*为空指针，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回**EOF** ，并将**Errno**设置为**EINVAL**。

## <a name="remarks"></a>备注

**Fscanf**函数从*流*的当前位置将数据读取到由*参数*（如果有）指定的位置。 每个*参数*都必须是指向类型的变量的指针，该类型与*格式*中的类型说明符对应。 *format*控制输入字段的解释，其形式和函数与**scanf**的*格式*参数相同;有关*格式*的说明，请参阅[scanf](scanf-scanf-l-wscanf-wscanf-l.md) 。

**fwscanf**是**fscanf**的宽字符版本;**fwscanf**的格式参数是宽字符字符串。 如果在 ANSI 模式下打开流，则这些函数行为相同。 **fscanf**当前不支持 UNICODE 流的输入。

这些带有 **_l**后缀的函数的版本相同，只不过它们使用传入的区域设置参数而不是当前线程区域设置。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftscanf**|**fscanf**|**fscanf**|**fwscanf**|
|**_ftscanf_l**|**_fscanf_l**|**_fscanf_l**|**_fwscanf_l**|

有关详细信息，请参阅[格式规范字段-scanf 函数和 Wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fscanf**、 **_fscanf_l**|\<stdio.h>|
|**fwscanf**、 **_fwscanf_l**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fscanf.c
// compile with: /W3
// This program writes formatted
// data to a file. It then uses fscanf to
// read the various data back from the file.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long l;
   float fp;
   char s[81];
   char c;

   if( fopen_s( &stream, "fscanf.out", "w+" ) != 0 )
      printf( "The file fscanf.out was not opened\n" );
   else
   {
      fprintf( stream, "%s %ld %f%c", "a-string",
               65000, 3.14159, 'x' );
      // Security caution!
      // Beware loading data from a file without confirming its size,
      // as it may lead to a buffer overrun situation.

      // Set pointer to beginning of file:
      fseek( stream, 0L, SEEK_SET );

      // Read data back from file:
      fscanf( stream, "%s", s );   // C4996
      fscanf( stream, "%ld", &l ); // C4996

      fscanf( stream, "%f", &fp ); // C4996
      fscanf( stream, "%c", &c );  // C4996
      // Note: fscanf is deprecated; consider using fscanf_s instead

      // Output data read:
      printf( "%s\n", s );
      printf( "%ld\n", l );
      printf( "%f\n", fp );
      printf( "%c\n", c );

      fclose( stream );
   }
}
```

```Output
a-string
65000
3.141590
x
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>

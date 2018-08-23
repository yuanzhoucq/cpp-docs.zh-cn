---
title: _tempnam、_wtempnam、tmpnam、_wtmpnam | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
dev_langs:
- C++
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55ff069d72d68493eee524ea2f9c012d2fc7f534
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417008"
---
# <a name="tempnam-wtempnam-tmpnam-wtmpnam"></a>_tempnam、_wtempnam、tmpnam、_wtmpnam

生成可用于创建临时文件的名称。 提供这些函数的更多安全版本；请参阅 [tmpnam_s、_wtmpnam_s](tmpnam-s-wtmpnam-s.md)。

## <a name="syntax"></a>语法

```C
char *_tempnam(
   const char *dir,
   const char *prefix
);
wchar_t *_wtempnam(
   const wchar_t *dir,
   const wchar_t *prefix
);
char *tmpnam(
   char *str
);
wchar_t *_wtmpnam(
   wchar_t *str
);
```

### <a name="parameters"></a>参数

*prefix*<br/>
将通过返回的名称的前面附加的字符串 **_tempnam**。

*dir*<br/>
文件名中使用的路径（如果不存在 TMP 环境变量或 TMP 不是有效的目录）。

*str*<br/>
指针将保留生成的名称，该名称将与函数所返回的名称相同。 这是保存生成的名称的简便方法。

## <a name="return-value"></a>返回值

其中每个函数返回一个指向生成的名称或**NULL**故障时。 如果你尝试，则可能发生失败多个**TMP_MAX** （请参阅 STDIO。H） 使用调用**tmpnam**或如果你使用 **_tempnam**且存在 TMP 环境变量在和中指定了无效的目录名称*dir*参数。

> [!NOTE]
> 返回的指针**tmpnam**和 **_wtmpnam**指向内部静态缓冲区。 不应调用 [free](free.md) 来释放这些指针。 **免费**需要通过分配的指针调用 **_tempnam**和 **_wtempnam**。

## <a name="remarks"></a>备注

这些函数返回的文件名当前不存在。 **tmpnam**返回在当前工作目录中唯一的名称和 **_tempnam**允许您在当前之外的目录中生成一个唯一的名称。 请注意，如果一个文件名称使用反斜杠作为前缀（如 \fname21），表示该名称对当前工作目录有效。

有关**tmpnam**，你可以存储在此生成的文件名称*str*。 如果*str*是**NULL**，然后**tmpnam**将结果留在内部静态缓冲区中。 因此，任何后续调用都会破坏该值。 由生成的名**tmpnam**包含的程序生成的文件名称，并在第一个调用后**tmpnam**，顺序中的数字基 32 文件扩展名 (.1.vvu，当**TMP_MAX** STDIO 中。H 是 32,767）。

**_tempnam**将生成目录由以下规则选择唯一的文件名：

- 如果定义了 TMP 环境变量并将其设置为有效的目录名称，则 TMP 所指定的目录将生成唯一文件名。

- 如果未定义 TMP 环境变量，或如果设置为不存在，目录的名称 **_tempnam**将使用*dir*它将为其生成唯一的名称的路径作为参数。

- 如果未定义 TMP 环境变量或如果设置为的名称的目录中不存在，并且如果*dir*是**NULL**或将设置为不存在，目录的名称 **_tempnam**将要使用的当前工作目录生成唯一的名称。 目前，如果这两个 TMP 和*dir*指定名称的目录不存在， **_tempnam**函数调用将失败。

返回的名称 **_tempnam**将的串联*前缀*和组合到一起以创建唯一的文件名指定的目录的顺序号。 **_tempnam**生成具有无扩展名的文件名称。 **_tempnam**使用[malloc](malloc.md)文件名; 的分配空间的程序负责在不再需要时释放此空间。

**_tempnam**和**tmpnam**句柄多字节字符字符串自变量，根据的 OEM 代码页识别多字节字符序列中自动从操作系统获取。 **_wtempnam**是宽字符版本的 **_tempnam**; 的自变量和返回值 **_wtempnam**是宽字符字符串。 **_wtempnam**和 **_tempnam**行为方式相同，只不过 **_wtempnam**不处理多字节字符字符串。 **_wtmpnam**是宽字符版本的**tmpnam**; 的自变量和返回值 **_wtmpnam**是宽字符字符串。 **_wtmpnam**和**tmpnam**行为方式相同，只不过 **_wtmpnam**不处理多字节字符字符串。

如果 **_DEBUG**和 **_CRTDBG_MAP_ALLOC**定义， **_tempnam**和 **_wtempnam**对的调用替换为[_tempnam_dbg 和 _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_tempnam**|\<stdio.h>|
|**_wtempnam**， **_wtmpnam**|\<stdio.h> 或 \<wchar.h>|
|**tmpnam**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_tempnam.c
// compile with: /W3
// This program uses tmpnam to create a unique filename in the
// current working directory, then uses _tempnam to create
// a unique filename with a prefix of stq.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char* name1 = NULL;
   char* name2 = NULL;

   // Create a temporary filename for the current working directory:
   if( ( name1 = tmpnam( NULL ) ) != NULL ) // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf( "%s is safe to use as a temporary file.\n", name1 );
   else
      printf( "Cannot create a unique filename\n" );

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if( ( name2 = _tempnam( "c:\\tmp", "stq" ) ) != NULL )
      printf( "%s is safe to use as a temporary file.\n", name2 );
   else
      printf( "Cannot create a unique filename\n" );

   // When name2 is no longer needed :
   if(name2)
     free(name2);

}
```

```Output
\s1gk. is safe to use as a temporary file.
C:\DOCUME~1\user\LOCALS~1\Temp\2\stq2 is safe to use as a temporary file.
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>

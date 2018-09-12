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
ms.openlocfilehash: bdd853affc343a4f07c64d025cd73122fdb8d458
ms.sourcegitcommit: 32fd693d092ea0b43c3916703364f494a5b502cf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2018
ms.locfileid: "44389479"
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
将前悬移到返回的名称的字符串 **_tempnam**。

*dir*<br/>
文件名中使用的路径（如果不存在 TMP 环境变量或 TMP 不是有效的目录）。

*str*<br/>
指针将保留生成的名称，该名称将与函数所返回的名称相同。 这是保存生成的名称的简便方法。

## <a name="return-value"></a>返回值

每个函数返回一个指向生成的名称或**NULL**故障时。 如果你尝试，则会发生故障超过**TMP_MAX** （请参阅 STDIO。使用 H） 调用**tmpnam**或者如果您使用 **_tempnam** ，并且没有在 TMP 环境变量并在指定了无效的目录名称*dir*参数。

> [!NOTE]
> 通过返回的指针**tmpnam**并 **_wtmpnam**指向内部静态缓冲区。 不应调用 [free](free.md) 来释放这些指针。 **免费**需要通过分配的指针调用 **_tempnam**并 **_wtempnam**。

## <a name="remarks"></a>备注

这些函数返回的文件名当前不存在。 **tmpnam**返回在指定返回的 Windows 临时目录中是唯一的名称[GetTempPathW](/windows/desktop/api/fileapi/nf-fileapi-gettemppathw)。 **\_tempnam**以外指定目录中生成的唯一名称。 请注意，如果一个文件名称使用反斜杠作为前缀（如 \fname21），表示该名称对当前工作目录有效。 

有关**tmpnam**，可以存储在此生成的文件名称*str*。 如果*str*是**NULL**，然后**tmpnam**将结果留在内部静态缓冲区中。 因此，任何后续调用都会破坏该值。 通过生成的名称**tmpnam**包含的程序生成的文件名称，并在首次调用后**tmpnam**，基数 32 连续数字的文件扩展名 (.1-.vvu，当**TMP_MAX** STDIO 中。H 是 32,767）。

**_tempnam**将生成唯一的文件名由以下规则为所选目录：

- 如果定义了 TMP 环境变量并将其设置为有效的目录名称，则 TMP 所指定的目录将生成唯一文件名。

- 如果未定义 TMP 环境变量，或如果设置为不存在的目录的名称 **_tempnam**将使用*dir*参数，因为它将为其生成的唯一名称的路径。

- 如果未定义 TMP 环境变量或如果设置为不存在的目录的名称并且如果*dir*可以是**NULL**设置为不存在的目录的名称或 **_tempnam**将使用当前工作目录生成唯一的名称。 目前，如果 TMP 和*dir*指定的目录不存在，名称 **_tempnam**函数调用将失败。

返回的名称 **_tempnam**将是一个串连*前缀*和顺序号的组合到一起以创建唯一的文件名为指定的目录。 **_tempnam**生成无扩展名的文件名。 **_tempnam**使用[malloc](malloc.md)为 filename; 分配空间的程序是负责在不再需要时释放此空间。

**_tempnam**并**tmpnam**从操作系统句柄多字节字符字符串参数，根据 OEM 代码页识别多字节字符序列中自动获取。 **_wtempnam**是宽字符版本 **_tempnam**; 的参数和返回值 **_wtempnam**都是宽字符字符串。 **_wtempnam**并 **_tempnam**行为方式相同，只不过 **_wtempnam**不处理多字节字符字符串。 **_wtmpnam**是宽字符版本**tmpnam**; 的自变量和返回值 **_wtmpnam**都是宽字符字符串。 **_wtmpnam**并**tmpnam**行为方式相同，只不过 **_wtmpnam**不处理多字节字符字符串。

如果 **_DEBUG**并 **_CRTDBG_MAP_ALLOC**定义了， **_tempnam**并 **_wtempnam**对的调用替换为[_tempnam_dbg 和 _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
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

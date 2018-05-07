---
title: tmpnam_s、_wtmpnam_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- tmpnam_s
- _wtmpnam_s
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
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
dev_langs:
- C++
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8c6298c7b66c8967a4e5e23a37c3614edcddf3d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="tmpnams-wtmpnams"></a>tmpnam_s、_wtmpnam_s

生成可用于创建临时文件的名称。 这些版本的 [tmpnam 和 _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

## <a name="syntax"></a>语法

```C
errno_t tmpnam_s(
   char * str,
   size_t sizeInChars
);
errno_t _wtmpnam_s(
   wchar_t *str,
   size_t sizeInChars
);
template <size_t size>
errno_t tmpnam_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _wtmpnam_s(
   wchar_t (&str)[size]
); // C++ only
```

### <a name="parameters"></a>参数

*str*<br/>
保留生成的名称的指针。

*sizeInChars*<br/>
以字符为单位的缓冲区的大小。

## <a name="return-value"></a>返回值

如果成功，则这两个函数均返回 0，如果失败，则返回错误号。

### <a name="error-conditions"></a>错误条件

|||||
|-|-|-|-|
|*str*|*sizeInChars*|**返回值**|**内容***str* |
|**NULL**|任何|**EINVAL**|未修改|
|不**NULL** （指向有效的内存）|过短|**ERANGE**|未修改|

如果*str*是**NULL**，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将设置**errno**到**EINVAL**并返回**EINVAL**。

## <a name="remarks"></a>备注

这些函数返回的文件名当前不存在。 **tmpnam_s**返回在当前工作目录中唯一的名称。 请注意，如果一个文件名称使用反斜杠作为前缀（如 \fname21），表示该名称对当前工作目录有效。

有关**tmpnam_s**，你可以存储在此生成的文件名称*str*。 通过返回的字符串的最大长度**tmpnam_s**是**L_tmpnam_s**在 STDIO 中定义。H。 如果*str*是**NULL**，然后**tmpnam_s**将结果留在内部静态缓冲区中。 因此，任何后续调用都会破坏该值。 由生成的名**tmpnam_s**包含的程序生成的文件名称，并在第一个调用后**tmpnam_s**，顺序中的数字基 32 文件扩展名 (.1.1vvvvvu，当**TMP_MAX_S** STDIO 中。H 是**INT_MAX**)。

**tmpnam_s**句柄多字节字符字符串自变量，根据的 OEM 代码页识别多字节字符序列中自动从操作系统获取。 **_wtmpnam_s**是宽字符版本的**tmpnam_s**; 的自变量和返回值 **_wtmpnam_s**是宽字符字符串。 **_wtmpnam_s**和**tmpnam_s**行为方式相同，只不过 **_wtmpnam_s**不处理多字节字符字符串。

在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**tmpnam_s**|\<stdio.h>|
|**_wtmpnam_s**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_tmpnam_s.c
// This program uses tmpnam_s to create a unique filename in the
// current working directory.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char name1[L_tmpnam_s];
   errno_t err;
   int i;

   for (i = 0; i < 15; i++)
   {
      err = tmpnam_s( name1, L_tmpnam_s );
      if (err)
      {
         printf("Error occurred creating unique filename.\n");
         exit(1);
      }
      else
      {
         printf( "%s is safe to use as a temporary file.\n", name1 );
      }
   }
}
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>

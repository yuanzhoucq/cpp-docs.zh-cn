---
title: gets_s、_getws_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getws_s
- gets_s
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
- _getws_s
- gets_s
dev_langs:
- C++
helpviewer_keywords:
- getws_s function
- _getws_s function
- lines, getting
- streams, getting lines
- buffers, avoiding overruns
- buffer overruns
- buffers, buffer overruns
- gets_s function
- standard input, reading from
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3a5047871937d96288798768e17618ab791c75e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="getss-getwss"></a>gets_s、_getws_s

获取从行**stdin**流。 这些版本的 [gets、_getws](../../c-runtime-library/gets-getws.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

## <a name="syntax"></a>语法

```C
char *gets_s(
   char *buffer,
   size_t sizeInCharacters
);
wchar_t *_getws_s(
   wchar_t *buffer,
   size_t sizeInCharacters
);
```

```cpp
template <size_t size>
char *gets_s( char (&buffer)[size] ); // C++ only

template <size_t size>
wchar_t *_getws_s( wchar_t (&buffer)[size] ); // C++ only
```

### <a name="parameters"></a>参数

*buffer*<br/>
输入字符串的存储位置。

*sizeInCharacters*<br/>
缓冲区的大小。

## <a name="return-value"></a>返回值

返回*缓冲区*如果成功。 A **NULL**指针指示错误或文件尾条件。 使用 [ferror](ferror.md) 或 [feof](feof.md) 确定已发生哪种情况。

## <a name="remarks"></a>备注

**Gets_s**函数从标准输入流中读取一行**stdin**和将其存储在*缓冲区*。 该行由第一个换行符(“\n”)之前的所有字符和该换行符构成。 **gets_s**然后换行符替换 null 字符 (\0') 返回行之前。 与此相反， **fgets_s**函数将保留换行符。

如果读取的第一个字符，文件尾字符开头的存储 null 字符*缓冲区*和**NULL**返回。

**_getws_s**是宽字符版本的**gets_s**; 其自变量和返回值都是宽字符字符串。

如果*缓冲区*是**NULL**或*sizeInCharacters*小于或等于零，或如果缓冲区太小，无法包含的输入的行和 null 终止符，这些函数将调用一个无效的参数处理程序中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将返回**NULL**并将 errno 设置为**ERANGE**。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_getts_s**|**gets_s**|**gets_s**|**_getws_s**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**gets_s**|\<stdio.h>|
|**_getws_s**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 控制台中，与关联的标准流句柄**stdin**， **stdout**，和**stderr**，必须将 C 运行时函数才能使用它们在 UWP 应用重定向. 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_gets_s.c
// This program retrieves a string from the stdin and
// prints the same string to the console.

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets_s( line, 20 );
   printf( "The line entered was: %s\n", line );
}
```

```Input
Hello there!
```

```Output
The line entered was: Hello there!
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[gets、_getws](../../c-runtime-library/gets-getws.md)<br/>
[fgets、fgetws](fgets-fgetws.md)<br/>
[fputs、fputws](fputs-fputws.md)<br/>
[puts、_putws](puts-putws.md)<br/>

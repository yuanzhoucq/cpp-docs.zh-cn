---
title: _tempnam、_wtempnam、tmpnam、_wtmpnam
ms.date: 11/04/2016
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
ms.openlocfilehash: 0e8e11182948e9bccf1c55685cc7c3d55ff697c8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500768"
---
# <a name="_tempnam-_wtempnam-tmpnam-_wtmpnam"></a>_tempnam、_wtempnam、tmpnam、_wtmpnam

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
将预先挂起到 **_tempnam**返回的名称的字符串。

*目录*<br/>
文件名中使用的路径（如果不存在 TMP 环境变量或 TMP 不是有效的目录）。

*str*<br/>
指针将保留生成的名称，该名称将与函数所返回的名称相同。 这是保存生成的名称的简便方法。

## <a name="return-value"></a>返回值

其中每个函数均返回一个指向生成的名称的指针, 如果出现错误, 则返回**NULL** 。 如果尝试超过**TMP_MAX** , 则可能会失败 (请参阅 stdio.h。H) 使用**tmpnam**调用, 或者, 如果使用的是 **_tempnam** , 并且在 TMP 环境变量和*dir*参数中指定了无效的目录名称。

> [!NOTE]
> **Tmpnam**和 **_wtmpnam**所返回的指针指向内部静态缓冲区。 不应调用 [free](free.md) 来释放这些指针。 需要为 **_tempnam**和 **_wtempnam**所分配的指针调用**free** 。

## <a name="remarks"></a>备注

这些函数返回的文件名当前不存在。 **tmpnam**返回由[GetTempPathW](/windows/win32/api/fileapi/nf-fileapi-gettemppathw)返回的指定 Windows 临时目录中唯一的名称。 tempnam 在指定的目录以外的目录中生成唯一名称。  **\_** 请注意，如果一个文件名称使用反斜杠作为前缀（如 \fname21），表示该名称对当前工作目录有效。

对于**tmpnam**, 你可以将生成的文件名存储在*str*中。 如果*str*为**NULL**, 则**tmpnam**将结果保留在内部静态缓冲区中。 因此，任何后续调用都会破坏该值。 由**tmpnam**生成的名称包含程序生成的文件名, 并在第一次调用 tmpnam 后, 在第 32 (. 1-, TMP_MAX 中的**stdio.h**时, 为的文件扩展名。H 为 32767)。

**_tempnam**将为以下规则所选择的目录生成唯一的文件名:

- 如果定义了 TMP 环境变量并将其设置为有效的目录名称，则 TMP 所指定的目录将生成唯一文件名。

- 如果未定义 TMP 环境变量, 或者未将其设置为不存在的目录的名称, 则 **_tempnam**将使用*dir*参数作为其将生成唯一名称的路径。

- 如果未定义 TMP 环境变量, 或将其设置为不存在的目录的名称, 并且*dir*为**空**或设置为不存在的目录的名称, 则 **_tempnam**将使用当前工作目录基因为唯一名称打分。 目前, 如果 TMP 和*目录*均指定不存在的目录的名称, 则 **_tempnam**函数调用将失败。

**_Tempnam**返回的名称将是*前缀*和序列号的串联, 这将组合起来为指定目录创建唯一的文件名。 **_tempnam**生成无扩展名的文件名。 **_tempnam**使用[malloc](malloc.md)为文件名分配空间;程序负责在不再需要此空间时将其释放。

**_tempnam**和**tmpnam**会根据需要自动处理多字节字符串参数, 根据从操作系统获取的 OEM 代码页识别多字节字符序列。 **_wtempnam**是 **_tempnam**的宽字符版本; **_wtempnam**的参数和返回值是宽字符字符串。 **_wtempnam**和 **_tempnam**的行为相同, 只不过 **_wtempnam**不处理多字节字符字符串。 **_wtmpnam**是**tmpnam**的宽字符版本; **_wtmpnam**的参数和返回值是宽字符字符串。 **_wtmpnam**和**tmpnam**的行为相同, 只不过 **_wtmpnam**不处理多字节字符字符串。

如果定义了 **_debug**和 **_CRTDBG_MAP_ALLOC** , 则 **_tempnam**和 **_wtempnam**将被调用[_tempnam_dbg 和 _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_tempnam**|\<stdio.h>|
|**_wtempnam**、 **_wtmpnam**|\<stdio.h> 或 \<wchar.h>|
|**tmpnam**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_tempnam.c
// compile with: /W3
// This program uses tmpnam to create a unique filename in the
// temporary directory, and _tempname to create a unique filename
// in C:\\tmp.

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
   char * name1 = NULL;
   char * name2 = NULL;
   char * name3 = NULL;

   // Create a temporary filename for the current working directory:
   if ((name1 = tmpnam(NULL)) != NULL) { // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf("%s is safe to use as a temporary file.\n", name1);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if ((name2 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name2);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // When name2 is no longer needed:
   if (name2) {
      free(name2);
   }

   // Unset TMP environment variable, then create a temporary filename in C:\tmp.
   if (_putenv("TMP=") != 0) {
      printf("Could not remove TMP environment variable.\n");
   }

   // With TMP unset, we will use C:\tmp as the temporary directory.
   // Create a temporary filename in C:\tmp with prefix "stq".
   if ((name3 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name3);
   }
   else {
      printf("Cannot create a unique filename\n");
   }

   // When name3 is no longer needed:
   if (name3) {
      free(name3);
   }

   return 0;
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\sriw.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\stq2 is safe to use as a temporary file.
c:\tmp\stq3 is safe to use as a temporary file.
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>

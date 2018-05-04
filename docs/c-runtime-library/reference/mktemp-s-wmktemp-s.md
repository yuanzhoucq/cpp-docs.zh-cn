---
title: _mktemp_s、_wmktemp_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mktemp_s
- _wmktemp_s
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
apitype: DLLExport
f1_keywords:
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
dev_langs:
- C++
helpviewer_keywords:
- _tmktemp_s function
- mktemp_s function
- _wmktemp_s function
- _mktemp_s function
- files [C++], temporary
- tmktemp_s function
- wmktemp_s function
- temporary files [C++]
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0ed525f44150943496cddde57699035d8b62b6d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="mktemps-wmktemps"></a>_mktemp_s、_wmktemp_s

创建唯一的文件名。 如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述，这些版本的 [_mktemp、_wmktemp](mktemp-wmktemp.md) 具有安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t _mktemp_s(
   char *nameTemplate,
   size_t sizeInChars
);
errno_t _wmktemp_s(
   wchar_t *nameTemplate,
   size_t sizeInChars
);
template <size_t size>
errno_t _mktemp_s(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
errno_t _wmktemp_s(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>参数

*nameTemplate*<br/>
文件名模式。

*sizeInChars*<br/>
在中的单字节字符的缓冲区大小 **_mktemp_s**; 宽字符在 **_wmktemp_s**，包括 null 终止符。

## <a name="return-value"></a>返回值

如果成功，这两个函数返回零；如果失败，则返回错误代码。

### <a name="error-conditions"></a>错误条件

|*nameTemplate*|*sizeInChars*|返回值|中的新值*nameTemplate*|
|----------------|-------------------|----------------------|-------------------------------|
|**NULL**|任何|**EINVAL**|**NULL**|
|格式不正确 (请参阅备注部分以了解正确的格式)|任何|**EINVAL**|空字符串|
|任何|<= X 的数量|**EINVAL**|空字符串|

如果发生上述错误情况中的任何一个，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则**errno**设置为**EINVAL**和函数返回**EINVAL**。

## <a name="remarks"></a>备注

**_Mktemp_s**函数通过修改创建唯一的文件名*nameTemplate*自变量，以便在调用后， *nameTemplate*指针指向一个字符串包含新的文件名称。 **_mktemp_s**自动处理多字节字符字符串自变量，根据需要，识别运行时系统根据当前正在使用的多字节代码页的多字节字符序列。 **_wmktemp_s**是宽字符版本的 **_mktemp_s**; 的自变量 **_wmktemp_s**是宽字符字符串。 **_wmktemp_s**和 **_mktemp_s**行为方式相同，只不过 **_wmktemp_s**不处理多字节字符字符串。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

*NameTemplate*自变量具有窗体**baseXXXXXX**，其中*基*是你提供的新文件名的部分，而每个 X 是一个占位符，供提供的字符 **_mktemp_s**。 中的每个占位符字符*nameTemplate*必须是大写 X **_mktemp_s**保留*基*，将第一个尾随 X 替换为字母字符。 **_mktemp_s**后面的尾随 X 替换为五位数值; 此值是标识调用进程，或在多线程程序中，调用线程的唯一编号。

每次成功调用 **_mktemp_s**修改*nameTemplate*。 中的相同进程或具有相同的线程从每个后续调用*nameTemplate*自变量， **_mktemp_s**检查返回的名称匹配的文件名称 **_mktemp_s**在以前的调用。 如果给定名称的文件不存在 **_mktemp_s**返回该名称。 如果文件存在之前返回的所有名称， **_mktemp_s**通过将它与下一个可用小写字母，按顺序，从 a 到 z 的之前返回名称中使用的字母字符创建一个新名称。 例如，如果*基*是：

> **fn**

和提供的五位数值 **_mktemp_s**为 12345，返回的第一个名称为：

> **fna12345**

如果此名称用于创建文件 FNA12345 并且此文件仍存在下, 一步的名称的调用返回的相同进程或具有相同的线程从*基*为*nameTemplate*是：

> **fnb12345**

如果 FNA12345 不存在，则返回的下一个名称又是：

> **fna12345**

**_mktemp_s** 26 唯一的文件名的任意给定组合最多可以创建*基*和*nameTemplate*值。 因此，FNZ12345 是最后一个唯一文件名 **_mktemp_s**可以为创建*基*和*nameTemplate*此示例中使用的值。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mktemp_s**|\<io.h>|
|**_wmktemp_s**|\<io.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```cpp
// crt_mktemp_s.cpp
/* The program uses _mktemp to create
* five unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>

char *fnTemplate = "fnXXXXXX";
char names[5][9];

int main()
{
   int i, err, sizeInChars;
   FILE *fp;

   for( i = 0; i < 5; i++ )
   {
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );
      /* Get the size of the string and add one for the null terminator.*/
      sizeInChars = strnlen(names[i], 9) + 1;
      /* Attempt to find a unique filename: */
      err = _mktemp_s( names[i], sizeInChars );
      if( err != 0 )
         printf( "Problem creating the template" );
      else
      {
         if( fopen_s( &fp, names[i], "w" ) == 0 )
            printf( "Unique filename is %s\n", names[i] );
         else
            printf( "Cannot open %s\n", names[i] );
         fclose( fp );
      }
   }

   return 0;
}
```

### <a name="sample-output"></a>示例输出

```Output
Unique filename is fna03188
Unique filename is fnb03188
Unique filename is fnc03188
Unique filename is fnd03188
Unique filename is fne03188
```

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>

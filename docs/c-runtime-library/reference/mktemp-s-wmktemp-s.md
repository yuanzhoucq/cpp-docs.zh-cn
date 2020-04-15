---
title: _mktemp_s、_wmktemp_s
ms.date: 4/2/2020
api_name:
- _mktemp_s
- _wmktemp_s
- _o__mktemp_s
- _o__wmktemp_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
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
ms.openlocfilehash: 061c5647b2c5a5e79b017cf93989f62ad19cfc0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338756"
---
# <a name="_mktemp_s-_wmktemp_s"></a>_mktemp_s、_wmktemp_s

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

*名称模板*<br/>
文件名模式。

*大小在查尔斯*<br/>
**_mktemp_s**中以单字节字符表示缓冲区的大小;**_wmktemp_s**中的宽字符，包括空终止符。

## <a name="return-value"></a>返回值

如果成功，这两个函数返回零；如果失败，则返回错误代码。

### <a name="error-conditions"></a>错误条件

|*名称模板*|*大小在查尔斯*|返回值|*名称模板*中的新值|
|----------------|-------------------|----------------------|-------------------------------|
|**空**|any|**埃因瓦尔**|**空**|
|格式不正确（有关正确格式，请参阅备注部分）|any|**埃因瓦尔**|空字符串|
|any|<= X 的数量|**埃因瓦尔**|空字符串|

如果发生上述错误情况中的任何一个，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续 **，errno**设置为**EINVAL，** 函数返回**EINVAL**。

## <a name="remarks"></a>备注

**_mktemp_s**函数通过修改*nameTemplate*参数创建唯一的文件名，以便在调用后 *，nameTemplate*指针指向包含新文件名的字符串。 **_mktemp_s**根据需要自动处理多字节字符串参数，根据运行时系统当前使用的多字节代码页识别多字节字符序列。 **_wmktemp_s**是 **_mktemp_s**的宽字符版本;**_wmktemp_s**的参数是宽字符字符串。 **_wmktemp_s**和 **_mktemp_s**行为相同，除非 **_wmktemp_s**不处理多字节字符串。

这些函数的调试库版本首先用 0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

*nameTemplate*参数具有窗体**baseXXXXXX，** 其中*base*是您提供的新文件名的一部分，每个 X 是 **_mktemp_s**提供的字符的占位符。 *名称模板*中的每个占位符字符都必须是大写**X，_mktemp_s**保留*基，* 并将第一个尾随 X 替换为字母字符。 **_mktemp_s**将以下尾随 X 替换为五位值;此值是标识调用过程的唯一编号，或在多线程程序中标识调用线程。

每次成功调用 **_mktemp_s**修改*名称模板*。 在来自具有相同*名称Template*参数的同一进程或线程的每个后续调用中 **，_mktemp_s**检查与 **_mktemp_s**在以前的调用中返回的名称匹配的文件名。 如果给定名称不存在文件 **，_mktemp_s**返回该名称。 如果以前返回的所有名称都有文件 **，_mktemp_s**通过将以前返回的名称中使用的字母字符替换为下一个可用小写字母（按顺序从"a"到"z"）来创建新名称。 例如，如果*基为*：

> **Fn**

**_mktemp_s**提供的五位值为 12345，返回的第一个名称是：

> **fna12345**

如果此名称用于创建文件 FNA12345，并且此文件仍然存在，则从具有相同*名称模板**基础*的同一进程或线程调用时返回的下一个名称是：

> **fnb12345**

如果 FNA12345 不存在，则返回的下一个名称又是：

> **fna12345**

**_mktemp_s**最多可以为*基本*值和*nameTemplate*值的任意给定组合创建 26 个唯一文件名。 因此，FNZ12345 是最后一个唯一的文件名 **_mktemp_s**可以为本示例中使用*的基础*和*名称模板*值创建。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mktemp_s**|\<io.h>|
|**_wmktemp_s**|\<io.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>

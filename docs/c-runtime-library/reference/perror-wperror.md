---
title: perror、_wperror
ms.date: 4/2/2020
api_name:
- _wperror
- perror
- _o__wperror
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wperror
- _tperror
- perror
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
ms.openlocfilehash: 0c50e77863b4b136ac59b6f79d8e529691032609
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338532"
---
# <a name="perror-_wperror"></a>perror、_wperror

打印错误消息。

## <a name="syntax"></a>语法

```C
void perror(
   const char *message
);
void _wperror(
   const wchar_t *message
);
```

### <a name="parameters"></a>参数

*消息*<br/>
要打印的字符串消息。

## <a name="remarks"></a>备注

**perror**函数将错误消息打印到**稳重**。 **_wperror**是 **_perror**的宽字符版本;要 **_wperror***的消息*参数是宽字符字符串。 **_wperror**和 **_perror**行为相同。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**perror**|**perror**|**_wperror**|

*首先打印消息*，后先打印冒号，然后打印生成错误的最后一个库调用的系统错误消息，最后由换行符打印。 如果*消息*是空指针或指向空字符串的指针，则**perror**仅打印系统错误消息。

错误数字存储在变量 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 中（在 ERRNO.H 中定义）。 通过变量 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 访问系统错误消息，该变量是按错误编号排序的消息数组。 **perror**使用**errno**值作为索引来 **_sys_errlist**打印相应的错误消息。 变量[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)的值定义为 **_sys_errlist**数组中元素的最大数量。

为获得准确结果，在库例程返回时立即调用**perror**并出现错误。 否则，后续调用可以覆盖**errno**值。

在 Windows 操作系统中，ERRNO 中列出了一些**错误**值。H 未使用。 这些值将保留以供 UNIX 操作系统使用。 有关 Windows 操作系统使用的**errno**值的列表，请参阅[_doserrno、errno、_sys_errlist 和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) **perror**打印这些平台未使用的任何**errno**值的空字符串。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**perror**|\<stdio.h> 或 \<stdlib.h>|
|**_wperror**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_perror.c
// compile with: /W3
/* This program attempts to open a file named
* NOSUCHF.ILE. Because this file probably doesn't exist,
* an error message is displayed. The same message is
* created using perror, strerror, and _strerror.
*/

#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <share.h>

int main( void )
{
   int  fh;

   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )
   {
      /* Three ways to create error message: */
      perror( "perror says open failed" );
      printf( "strerror says open failed: %s\n",
         strerror( errno ) ); // C4996
      printf( _strerror( "_strerror says open failed" ) ); // C4996
      // Note: strerror and _strerror are deprecated; consider
      // using strerror_s and _strerror_s instead.
   }
   else
   {
      printf( "open succeeded on input file\n" );
      _close( fh );
   }
}
```

```Output
perror says open failed: No such file or directory
strerror says open failed: No such file or directory
_strerror says open failed: No such file or directory
```

## <a name="see-also"></a>另请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[斯特错， _strerror， \__wcserror， _wcserror](strerror-strerror-wcserror-wcserror.md)<br/>

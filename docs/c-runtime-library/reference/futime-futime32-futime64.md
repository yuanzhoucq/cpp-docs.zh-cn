---
title: _futime、_futime32、_futime64 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _futime64
- _futime32
- _futime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- futime
- _futime
- futime64
- _futime64
dev_langs:
- C++
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 864bba5b88c7e52b55bd86a61edaaac2d22b0346
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="futime-futime32-futime64"></a>_futime、_futime32、_futime64

设置打开的文件的修改时间。

## <a name="syntax"></a>语法

```C
int _futime(
   int fd,
   struct _utimbuf *filetime
);
int _futime32(
   int fd,
   struct __utimbuf32 *filetime
);
int _futime64(
   int fd,
   struct __utimbuf64 *filetime
);
```

### <a name="parameters"></a>参数

*fd*<br/>
打开的文件的文件描述符。

*filetime*<br/>
指向包含新修改日期的结构的指针。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 出现错误时，会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，函数将返回-1 和**errno**设置为**EBADF**，指示无效文件描述符或**EINVAL**，指示无效参数。

## <a name="remarks"></a>备注

**_Futime**例程设置上与关联的打开文件修改日期和访问时间*fd*。 **_futime**等同于[_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md)，只不过其自变量是打开的文件的文件描述符而不是文件或文件的路径的名称。 **_Utimbuf**结构包含对新的修改日期和访问时间的字段。 这两个字段必须包含有效的值。 **_utimbuf32**和 **_utimbuf64**相同 **_utimbuf**除分别使用 32 位和 64 位时间类型，以外。 **_futime**和 **_utimbuf**使用 64 位时间类型和 **_futime**等同行为上与 **_futime64**。 如果需要强制这一旧行为，定义 **_USE_32BIT_TIME_T**。 这将导致这样做 **_futime**视为相同的行为到 **_futime32**并导致 **_utimbuf**使用 32 位时间类型，使其等效于结构 **__utimbuf32**。

**_futime64**，它使用 **__utimbuf64**结构，可以读取和修改 23:59:59，3000 年 12 月 31 日，UTC; 的文件日期，而调用 **_futime32**如果该文件的日期失败。晚于 23:59:59 2038 年 1 月 18 日，UTC。 1970 年 1 月 1 日午夜是这些函数的日期范围下限。

## <a name="requirements"></a>要求

|函数|必需的标头|可选标头|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<errno.h>|
|**_futime32**|\<sys/utime.h>|\<errno.h>|
|**_futime64**|\<sys/utime.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_futime.c
// This program uses _futime to set the
// file-modification time to the current time.

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <io.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/utime.h>
#include <share.h>

int main( void )
{
   int hFile;

   // Show file time before and after.
   system( "dir crt_futime.c_input" );

   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );

   if( _futime( hFile, NULL ) == -1 )
      perror( "_futime failed\n" );
   else
      printf( "File time modified\n" );

   _close (hFile);

   system( "dir crt_futime.c_input" );
}
```

### <a name="input-crtfutimecinput"></a>输入：crt_futime.c_input

```Input
Arbitrary file contents.
```

### <a name="sample-output"></a>示例输出

```Output
 Volume in drive Z has no label.
 Volume Serial Number is 5C68-57C1

 Directory of Z:\crt

 03/25/2004  10:40 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
 Volume in drive Z has no label.
 Volume Serial Number is 5C68-57C1

 Directory of Z:\crt

 03/25/2004  10:41 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
File time modified
```

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>

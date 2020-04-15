---
title: _futime、_futime32、_futime64
ms.date: 4/2/2020
api_name:
- _futime64
- _futime32
- _futime
- _o__futime32
- _o__futime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- futime
- _futime
- futime64
- _futime64
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
ms.openlocfilehash: 1f60bb3b366c48e3d53368f81ebc2528694794f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345501"
---
# <a name="_futime-_futime32-_futime64"></a>_futime、_futime32、_futime64

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

*Fd*<br/>
打开的文件的文件描述符。

*文件时间*<br/>
指向包含新修改日期的结构的指针。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 出现错误时，会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数返回 **-1，errno**设置为**EBADF，** 指示无效的文件描述符或**EINVAL**，指示无效参数。

## <a name="remarks"></a>备注

**_futime**例程设置与*fd*关联的打开文件中的修改日期和访问时间。 **_futime**与[_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md)相同，只不过其参数是打开文件的文件描述符，而不是文件的名称或文件的路径。 **_utimbuf**结构包含新修改日期和访问时间的字段。 这两个字段必须包含有效的值。 **_utimbuf32**和 **_utimbuf64**与 **_utimbuf**相同，但分别使用 32 位和 64 位时间类型。 **_futime**和 **_utimbuf**使用 64 位时间类型 **，_futime**的行为与 **_futime64**相同。 如果需要强制旧行为，请定义 **_USE_32BIT_TIME_T**。 这样做会导致 **_futime**行为与 **_futime32**相同，并导致 **_utimbuf**结构使用 32 位时间类型，使其等效于 **__utimbuf32**。

**_futime64**（）使用 **__utimbuf64**结构，可以在 UTC 12 月 31 日 23：59：59 读取和修改文件日期;如果文件上的日期晚于 2038 年 1 月 18 日 23：59：59，UTC，则对 **_futime32**的调用将失败。 1970 年 1 月 1 日午夜是这些函数的日期范围下限。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|可选标头|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<errno.h>|
|**_futime32**|\<sys/utime.h>|\<errno.h>|
|**_futime64**|\<sys/utime.h>|\<errno.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

### <a name="input-crt_futimec_input"></a>输入：crt_futime.c_input

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

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>

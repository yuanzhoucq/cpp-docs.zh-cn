---
title: _utime、_utime32、_utime64、_wutime、_wutime32、_wutime64
ms.date: 11/04/2016
apiname:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
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
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
ms.openlocfilehash: 8e52845a828e272ff3b8458b299c3757b8def748
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524626"
---
# <a name="utime-utime32-utime64-wutime-wutime32-wutime64"></a>_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64

设置文件修改时间。

## <a name="syntax"></a>语法

```C
int _utime(
   const char *filename,
   struct _utimbuf *times
);
int _utime32(
   const char *filename,
   struct __utimbuf32 *times
);
int _utime64(
   const char *filename,
   struct __utimbuf64 *times
);
int _wutime(
   const wchar_t *filename,
   struct _utimbuf *times
);
int _wutime32(
   const wchar_t *filename,
   struct __utimbuf32 *times
);
int _wutime64(
   const wchar_t *filename,
   struct __utimbuf64 *times
);
```

### <a name="parameters"></a>参数

*filename*<br/>
指向包含路径或文件名的字符串的指针。

*时间*<br/>
指向存储时间值的指针。

## <a name="return-value"></a>返回值

如果更改了文件修改时间，则这些函数均将返回 0。 返回值-1 指示错误。 如果传递的参数无效，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，这些函数将返回-1 和**errno**设置为以下值之一：

|errno 值|条件|
|-|-|
| **EACCES** | 路径指定目录或只读文件 |
| **EINVAL** | 无效*时间*参数 |
| **EMFILE** | 打开的文件太多（必须打开文件以更改其修改时间） |
| **ENOENT** | 找不到路径或文件名 |

有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果更改日期在 1970 年 1 月 1 日午夜之后且在所使用的函数的结束日期之前，则可以更改文件的日期。 **_utime**并 **_wutime**使用 64 位时间值，因此结束日期为 23:59:59，3000 年 12 月 31 日，UTC。 如果 **_USE_32BIT_TIME_T**定义若要强制旧行为，结束日期是 23:59:59 2038 年 1 月 18 日，UTC。 **_utime32**或 **_wutime32**使用 32 位时间类型，无论是否 **_USE_32BIT_TIME_T**定义，并且始终具有较早的结束日期。 **_utime64**或 **_wutime64**始终使用 64 位时间类型，因此这些函数始终支持更高版本的结束日期。

## <a name="remarks"></a>备注

**_Utime**函数设置指定的文件的修改时间*filename*。 进程必须拥有文件的写入权限才能更改时间。 在 Windows 操作系统，您可以更改访问时间和修改时间 **_utimbuf**结构。 如果*倍*是**NULL**指针，修改时间设置为当前的本地时间。 否则为*倍*必须指向类型的结构 **_utimbuf**SYS\UTIME 中定义。H.

**_Utimbuf**结构存储使用的文件访问和修改时间 **_utime**用于更改文件修改日期。 此结构中包含以下字段，其均为类型**time_t**:

| 字段 |   |
|-------|---|
| **actime** | 文件访问时间 |
| **modtime** | 文件修改时间 |

特定版本的 **_utimbuf**结构 (**_utimebuf32**并 **__utimbuf64**) 使用 32 位和 64 位版本的时间类型定义。 这些是此函数的 32 位和 64 位特定版本中使用的内容。 **_utimbuf**本身默认情况下使用 64 位时间类型，除非 **_USE_32BIT_TIME_T**定义。

**_utime**等同于 **_futime**只不过*filename*参数 **_utime**是文件名或文件，而不是文件描述符的路径打开文件。

**_wutime**是宽字符版本 **_utime**; *filename*参数 **_wutime**是宽字符字符串。 否则这些函数具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime**|**_utime**|**_utime**|**_wutime**|
|**_tutime32**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>要求

|例程所返回的值|必需标头|可选标头|
|-------------|----------------------|----------------------|
|**_utime**， **_utime32**， **_utime64**|\<sys/utime.h>|\<errno.h>|
|**_utime64**|\<sys/utime.h>|\<errno.h>|
|**_wutime**|\<utime.h> 或 \<wchar.h>|\<errno.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此程序使用 **_utime**要将文件修改时间设置为当前时间。

```C
// crt_utime.c
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/utime.h>
#include <time.h>

int main( void )
{
   struct tm tma = {0}, tmm = {0};
   struct _utimbuf ut;

   // Fill out the accessed time structure
   tma.tm_hour = 12;
   tma.tm_isdst = 0;
   tma.tm_mday = 15;
   tma.tm_min = 0;
   tma.tm_mon = 0;
   tma.tm_sec = 0;
   tma.tm_year = 103;

   // Fill out the modified time structure
   tmm.tm_hour = 12;
   tmm.tm_isdst = 0;
   tmm.tm_mday = 15;
   tmm.tm_min = 0;
   tmm.tm_mon = 0;
   tmm.tm_sec = 0;
   tmm.tm_year = 102;

   // Convert tm to time_t
   ut.actime = mktime(&tma);
   ut.modtime = mktime(&tmm);

   // Show file time before and after
   system( "dir crt_utime.c" );
   if( _utime( "crt_utime.c", &ut ) == -1 )
      perror( "_utime failed\n" );
   else
      printf( "File time modified\n" );
   system( "dir crt_utime.c" );
}
```

### <a name="sample-output"></a>示例输出

```Output
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/09/2003  05:38 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
File time modified
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/15/2002  12:00 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
```

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[_futime、_futime32、_futime64](futime-futime32-futime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[_stat、_wstat 函数](stat-functions.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>

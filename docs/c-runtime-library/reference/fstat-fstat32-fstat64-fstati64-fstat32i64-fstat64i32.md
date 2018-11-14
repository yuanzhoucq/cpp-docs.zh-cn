---
title: _fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32
ms.date: 11/04/2016
apiname:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fstat32i64
- fstat
- fstat64i32
- _fstat64
- _fstati64
- fstat64
- _fstat32
- fstat32i64
- fstati64
- _fstat
- fstat32
- _fstat64i32
helpviewer_keywords:
- _fstat64 function
- fstati64 function
- _fstat64i32 function
- _fstat32i64 function
- _fstat32 function
- file information
- fstat64i32 function
- fstat32 function
- fstat function
- fstat64 function
- _fstat function
- _fstati64 function
- fstat32i64 function
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
ms.openlocfilehash: 36d8b0d6480266f86136119a470fb7af5859a5b8
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331238"
---
# <a name="fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32"></a>_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32

获取有关打开文件的信息。

## <a name="syntax"></a>语法

```C
int _fstat(
   int fd,
   struct _stat *buffer
);
int _fstat32(
   int fd,
   struct __stat32 *buffer
);
int _fstat64(
   int fd,
   struct __stat64 *buffer
);
int _fstati64(
   int fd,
   struct _stati64 *buffer
);
int _fstat32i64(
   int fd,
   struct _stat32i64 *buffer
);
int _fstat64i32(
   int fd,
   struct _stat64i32 *buffer
);
```

### <a name="parameters"></a>参数

*fd*<br/>
打开文件的文件描述符。

*buffer*<br/>
指向存储结果的结构的指针。

## <a name="return-value"></a>返回值

如果获取到文件状态信息，则返回 0。 返回值-1 指示错误。 如果文件描述符无效或*缓冲区*是**NULL**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EBADF**，对于一个无效文件说明符，或设置为**EINVAL**，如果*缓冲区*是**NULL**。

## <a name="remarks"></a>备注

**_Fstat**函数可获取有关与关联的打开文件的信息*fd*并将其存储在由指向的结构*缓冲区*。 **_Stat** SYS\Stat.h 中定义的结构包含以下字段。

|字段|含义|
|-|-|
| **st_atime** | 上次文件访问的时间。 |
| **st_ctime** | 文件的创建时间。 |
| **st_dev** | 如果一台设备， *fd*; 否则为 0。 |
| **st_mode** | 文件模式信息的位掩码。 **_S_IFCHR**如果设置位*fd*指设备。 **_S_IFREG**如果设置位*fd*指的是一个普通的文件。 将根据文件的权限模式设置读/写位。 **_S_IFCHR**和其他常量在 SYS\Stat.h 中定义。 |
| **st_mtime** | 上次进行文件修改的时间。 |
| **st_nlink** | 在非 NTFS 文件系统上始终为 1。 |
| **st_rdev** | 如果一台设备， *fd*; 否则为 0。 |
| **st_size** | 文件的大小（以字节为单位）。 |

如果*fd*设备，是指**st_atime**， **st_ctime**， **st_mtime**，并**st_size**字段无意义。

因为 Stat.h 使用 Types.h 中定义的 [_dev_t](../../c-runtime-library/standard-types.md) 类型，所以必须在代码中的 Stat.h 之前包含 Types.h。

**_fstat64**，使用该 **__stat64**结构，允许文件创建日期最大表示为 23:59:59，3000 年 12 月 31 日，UTC; 而其他函数只能表示截至 23:59:59 年 1 月 18 日，2038，UTC。 1970 年 1 月 1 日午夜是所有这些函数的日期范围下限。

这些函数的变体支持 32 位或 64 位时间类型以及 32 位或 64 位文件长度。 第一个数字后缀 (**32**或**64**) 指示的时间的大小使用的类型; 第二个后缀是**i32**或者**i64**，该值指示是否将文件大小表示为 32 位或 64 位整数。

**_fstat**等效于 **_fstat64i32**，和**结构** **_stat**包含 64 位时间。 这是 true 除非 **_USE_32BIT_TIME_T**定义了，这种情况下旧行为有效;**_fstat**使用 32 位时间，并**结构** **_stat**包含 32 位时间。 同样适用于 **_fstati64**。

### <a name="time-type-and-file-length-type-variations-of-stat"></a>_stat 时间类型和文件长度类型变体

|函数|已定义 _USE_32BIT_TIME_T？|时间类型|文件长度类型|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|未定义|64 位|32 位|
|**_fstat**|已定义|32 位|32 位|
|**_fstat32**|不受宏定义影响|32 位|32 位|
|**_fstat64**|不受宏定义影响|64 位|64 位|
|**_fstati64**|未定义|64 位|64 位|
|**_fstati64**|已定义|32 位|64 位|
|**_fstat32i64**|不受宏定义影响|32 位|64 位|
|**_fstat64i32**|不受宏定义影响|64 位|32 位|

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fstat**|\<sys/stat.h> 和 \<sys/types.h>|
|**_fstat32**|\<sys/stat.h> 和 \<sys/types.h>|
|**_fstat64**|\<sys/stat.h> 和 \<sys/types.h>|
|**_fstati64**|\<sys/stat.h> 和 \<sys/types.h>|
|**_fstat32i64**|\<sys/stat.h> 和 \<sys/types.h>|
|**_fstat64i32**|\<sys/stat.h> 和 \<sys/types.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fstat.c
// This program uses _fstat to report
// the size of a file named F_STAT.OUT.

#include <io.h>
#include <fcntl.h>
#include <time.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>
#include <share.h>

int main( void )
{
   struct _stat buf;
   int fd, result;
   char buffer[] = "A line to output";
   char timebuf[26];
   errno_t err;

   _sopen_s( &fd,
             "f_stat.out",
             _O_CREAT | _O_WRONLY | _O_TRUNC,
             _SH_DENYNO,
             _S_IREAD | _S_IWRITE );
   if( fd != -1 )
      _write( fd, buffer, strlen( buffer ) );

   // Get data associated with "fd":
   result = _fstat( fd, &buf );

   // Check if statistics are valid:
   if( result != 0 )
   {
      if (errno == EBADF)
        printf( "Bad file descriptor.\n" );
      else if (errno == EINVAL)
        printf( "Invalid argument to _fstat.\n" );
   }
   else
   {
      printf( "File size     : %ld\n", buf.st_size );
      err = ctime_s(timebuf, 26, &buf.st_mtime);
      if (err)
      {
         printf("Invalid argument to ctime_s.");
         exit(1);
      }
      printf( "Time modified : %s", timebuf );
   }
   _close( fd );
}
```

```Output
File size     : 16
Time modified : Wed May 07 15:25:11 2003
```

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_access、_waccess](access-waccess.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_filelength、_filelengthi64](filelength-filelengthi64.md)<br/>
[_stat、_wstat 函数](stat-functions.md)<br/>

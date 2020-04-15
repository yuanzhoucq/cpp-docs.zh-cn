---
title: _dup、_dup2
ms.date: 4/2/2020
api_name:
- _dup
- _dup2
- _o__dup
- _o__dup2
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
- _dup2
- _dup
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
ms.openlocfilehash: 239f857bb40c9609cb6f7ff373295a7a1f8523a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348118"
---
# <a name="_dup-_dup2"></a>_dup、_dup2

为打开的文件 **（_dup）** 创建第二个文件描述符，或重新分配文件描述符 **（_dup2**）。

## <a name="syntax"></a>语法

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>参数

*fd*， *fd1*<br/>
引用打开的文件的文件说明符。

*fd2*<br/>
任何文件说明符。

## <a name="return-value"></a>返回值

**_dup**返回新的文件描述符。 **_dup2**返回 0 表示成功。 如果发生错误，每个函数将返回 -1 并将**errno**设置到**EBADF（** 如果文件描述符无效）或**EMFILE（** 如果没有更多的文件描述符）时。 对于无效的文件描述符，函数还调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_dup**和 **_dup2**函数将第二个文件描述符与当前打开的文件相关联。 这些函数可用于将预定义的文件描述符（如**用于 stdout）** 与其他文件相关联。 可以使用任一文件说明符执行针对文件的操作。 文件允许的访问类型不受新说明符创建的影响。 **_dup**返回给定文件的下一个可用文件描述符。 **_dup2**强制*fd2*引用与*fd1*相同的文件。 如果*fd2*在调用时与打开的文件关联，则该文件将关闭。

**_dup**和 **_dup2**都接受文件描述符作为参数。 要将流 （`FILE *`） 传递给这些函数中的任何一个，请使用[_fileno](fileno.md)。 **fileno**例程返回当前与给定流关联的文件描述符。 下面的示例演示如何将**Stderr（** 定义为`FILE *`Stdio.h）与文件描述符相关联：

```C
int cstderr = _dup( _fileno( stderr ));
```

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

通用 Windows 平台 （UWP） 应用中不支持该控制台。 在与控制台 **、stdin、stdout**和**stder**关联的标准流句柄必须重定向，C 运行时函数才能在 UWP 应用中使用它们。 **stdout** 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_dup.c
// This program uses the variable old to save
// the original stdout. It then opens a new file named
// DataFile and forces stdout to refer to it. Finally, it
// restores stdout to its original state.

#include <io.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int old;
   FILE *DataFile;

   old = _dup( 1 );   // "old" now refers to "stdout"
                      // Note:  file descriptor 1 == "stdout"
   if( old == -1 )
   {
      perror( "_dup( 1 ) failure" );
      exit( 1 );
   }
   _write( old, "This goes to stdout first\n", 26 );
   if( fopen_s( &DataFile, "data", "w" ) != 0 )
   {
      puts( "Can't open file 'data'\n" );
      exit( 1 );
   }

   // stdout now refers to file "data"
   if( -1 == _dup2( _fileno( DataFile ), 1 ) )
   {
      perror( "Can't _dup2 stdout" );
      exit( 1 );
   }
   puts( "This goes to file 'data'\n" );

   // Flush stdout stream buffer so it goes to correct file
   fflush( stdout );
   fclose( DataFile );

   // Restore original stdout
   _dup2( old, 1 );
   puts( "This goes to stdout\n" );
   puts( "The file 'data' contains:" );
   _flushall();
   system( "type data" );
}
```

```Output
This goes to stdout first
This goes to stdout

The file 'data' contains:
This goes to file 'data'
```

## <a name="see-also"></a>另请参阅

[低电平 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>

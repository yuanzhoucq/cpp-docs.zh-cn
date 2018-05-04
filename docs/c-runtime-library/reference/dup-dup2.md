---
title: _dup、_dup2 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _dup
- _dup2
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
- _dup2
- _dup
dev_langs:
- C++
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad477dc09ce6c8bee2d69e479f8e1615639cb14d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="dup-dup2"></a>_dup、_dup2

创建打开的文件的第二个文件描述符 (**_dup**)，或重新分配文件描述符 (**_dup2**)。

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

**_dup**返回新的文件描述符。 **_dup2**返回 0 来指示成功。 如果发生错误，每个函数将返回-1 并设置**errno**到**EBADF**如果文件描述符无效或**EMFILE**如果没有其他文件说明符可用。 对于无效的文件描述符，函数还调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Dup**和 **_dup2**函数将第二个文件描述符与当前打开的文件相关联。 这些函数可以用于将一个预定义的文件说明符，例如，对于**stdout**，关联不同的文件。 可以使用任一文件说明符执行针对文件的操作。 文件允许的访问类型不受新说明符创建的影响。 **_dup**返回给定文件的下一个可用的文件描述符。 **_dup2**强制*fd2*来引用同一个文件作为*fd1*。 如果*fd2*关联与打开的文件时调用的则关闭该文件。

同时 **_dup**和 **_dup2**接受文件说明符作为参数。 将流 (**文件\*** ) 到这些函数之一，使用[_fileno](fileno.md)。 **Fileno**例程返回当前与给定流关联的文件描述符。 下面的示例演示如何将相关联**stderr** (定义为**文件\*** 在 Stdio.h 中) 与文件说明符：

```C
int cstderr = _dup( _fileno( stderr ));
```

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 控制台中，与关联的标准流句柄**stdin**， **stdout**，和**stderr**，必须将 C 运行时函数才能使用它们在 UWP 应用重定向. 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[低级别 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>

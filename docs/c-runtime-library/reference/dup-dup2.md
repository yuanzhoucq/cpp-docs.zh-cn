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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 6c635930fdbc8da550a2a32ea614e150fbeb08a8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915216"
---
# <a name="_dup-_dup2"></a>_dup、_dup2

为打开的文件（**_dup**）创建第二个文件描述符，或重新分配文件描述符（**_dup2**）。

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

**_dup**返回一个新的文件说明符。 **_dup2**返回0以指示成功。 如果发生错误，则每个函数将返回-1，并将**errno**设置为**ebadf (** （如果文件描述符无效）或设置为**EMFILE** （如果没有更多的文件描述符可用）。 对于无效的文件描述符，函数还调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Dup**和 **_dup2**函数将另一个文件说明符与当前打开的文件相关联。 这些函数可用于将预定义文件描述符（如用于**stdout**的文件）与其他文件相关联。 可以使用任一文件说明符执行针对文件的操作。 文件允许的访问类型不受新说明符创建的影响。 **_dup**返回给定文件的下一个可用文件说明符。 **_dup2**强制*fd2*引用与*fd1*相同的文件。 如果*fd2*与调用时打开的文件相关联，则关闭该文件。

**_Dup**和 **_dup2**接受文件说明符作为参数。 若要将流（`FILE *`）传递给这些函数中的任何一个，请使用[_fileno](fileno.md)。 **Fileno**例程返回当前与给定流关联的文件描述符。 下面的示例演示如何将**stderr** （在 stdio.h 中`FILE *`定义为）与文件描述符关联：

```C
int cstderr = _dup( _fileno( stderr ));
```

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

通用 Windows 平台（UWP）应用中不支持控制台。 与控制台、 **stdin**、 **stdout**和**stderr**关联的标准流句柄必须重定向，然后 C 运行时函数才能在 UWP 应用中使用它们。 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

[低级别 i/o](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>

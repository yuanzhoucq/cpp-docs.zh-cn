---
title: malloc
ms.date: 11/04/2016
api_name:
- malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- malloc
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
ms.openlocfilehash: 8001726bcc2f1b384d527c6f4edcbf8eb92b0d2a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952822"
---
# <a name="malloc"></a>malloc

分配内存块。

## <a name="syntax"></a>语法

```C
void *malloc(
   size_t size
);
```

### <a name="parameters"></a>参数

*size*<br/>
要分配的字节数。

## <a name="return-value"></a>返回值

**malloc**返回指向已分配空间的 void 指针; 如果可用内存不足，则返回**NULL** 。 若要返回指向**void**之外的类型的指针，请在返回值上使用类型转换。 返回值指向的存储空间确保可以正好与对齐要求小于或等于基本对齐要求的任意对象类型的存储对齐。 （在视觉C++对象中，基本对齐方式是**double**或8字节所需的对齐方式。 在针对 64 位平台的代码中，是 16 个字节。）对于具有较大对齐要求的对象（例如，SSE 类型[__m128](../../cpp/m128.md)和 **__m256**），以及使用`__declspec(align( n ))` **n**大于8的声明的类型，使用[_aligned_malloc](aligned-malloc.md)为其分配存储空间。 如果*size*为0，则**malloc**将在堆中分配一个长度为零的项，并返回指向该项的有效指针。 即使请求的内存量较小，也始终检查**malloc**的返回值。

## <a name="remarks"></a>备注

**Malloc**函数分配的内存块的*大小*至少为个字节。 由于对齐和维护信息所需的空间，块可能大于*大小*字节。

如果内存分配失败或请求的内存量超过 **_HEAP_MAXREQ**， **malloc**会将**errno**设置为**ENOMEM** 。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

启动代码使用**malloc**为 **_environ**、 *envp*和*argv*变量分配存储。 以下函数及其宽字符对应项也调用**malloc**。

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[_exec 函数](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[_spawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[system](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[getchar](getc-getwc.md)|[puts](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[gets](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

C++ [_set_new_mode](set-new-mode.md) 函数将为 **malloc** 设置新的处理程序模式。 新处理程序模式指示在失败时， **malloc**是否调用由[_set_new_handler](set-new-handler.md)设置的新处理程序例程。 默认情况下，在无法分配内存时， **malloc**不会调用新的处理程序例程。 您可以重写此默认行为，以便在**malloc**无法分配内存时， **malloc**会调用新的处理程序例程，其方式与在同一原因下**新**运算符失败时相同。 若要重写默认值`_set_new_mode(1)` ，请在程序的早期调用，或与 newmode.obj 链接。OBJ （请参阅[链接选项](../../c-runtime-library/link-options.md)）。

当应用程序与调试版的 C 运行时库链接时， **malloc**解析为[_malloc_dbg](malloc-dbg.md)。 有关堆在调试过程中如何托管的详细信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。

**malloc**标记`__declspec(noalias)`为和`__declspec(restrict)`; 这意味着函数保证不修改全局变量，并且返回的指针没有化名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**malloc**|\<stdlib.h> 和 \<malloc.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_malloc.c
// This program allocates memory with
// malloc, then frees the memory with free.

#include <stdlib.h>   // For _MAX_PATH definition
#include <stdio.h>
#include <malloc.h>

int main( void )
{
   char *string;

   // Allocate space for a path name
   string = malloc( _MAX_PATH );

   // In a C++ file, explicitly cast malloc's return.  For example,
   // string = (char *)malloc( _MAX_PATH );

   if( string == NULL )
      printf( "Insufficient memory available\n" );
   else
   {
      printf( "Memory space allocated for path name\n" );
      free( string );
      printf( "Memory freed\n" );
   }
}
```

```Output
Memory space allocated for path name
Memory freed
```

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>

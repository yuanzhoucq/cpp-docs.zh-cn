---
title: malloc | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- malloc
dev_langs:
- C++
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 39907fec3e169c4a49380e80b528a4af7fe22476
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
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

**malloc**到分配的空间中，将返回 void 的指针或**NULL**如果没有可用的内存不足。 若要返回一个指向类型而不**void**，使用类型强制转换返回值上。 返回值指向的存储空间确保可以正好与对齐要求小于或等于基本对齐要求的任意对象类型的存储对齐。 (Visual c + + 中的基本的对齐方式是所需的对齐方式**double**，或 8 个字节。 在针对 64 位平台的代码中，是 16 个字节。）使用[_aligned_malloc](aligned-malloc.md)来对具有更大的对齐要求的对象分配存储空间-例如，SSE 类型[__m128](../../cpp/m128.md)和 **__m256**，和类型使用声明`__declspec(align( n ))`其中**n**大于 8。 如果*大小*为 0， **malloc**分配堆中的长度为零项并将有效指针返回到该项目。 始终检查从返回**malloc**，即使请求的内存量很小。

## <a name="remarks"></a>备注

**Malloc**函数分配内存块至少*大小*字节。 块可能会大于*大小*由于具有所需的对齐方式和维护信息的空间的字节。

**malloc**设置**errno**到**ENOMEM**如果内存分配失败或内存量请求超过 **_HEAP_MAXREQ**。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

启动代码使用**malloc**分配用于存储 **_environ**， *envp*，和*argv*变量。 下面的函数，其对应的宽字符还调用**malloc**。

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

C++ [_set_new_mode](set-new-mode.md) 函数将为 **malloc** 设置新的处理程序模式。 新的处理程序模式指示是否在失败时， **malloc**是由设置调用新处理程序例程[_set_new_handler](set-new-handler.md)。 默认情况下， **malloc**不调用新处理程序例程上分配内存失败。 你可以重写此默认行为，以便，当**malloc**无法分配内存， **malloc**调用新处理程序例程中相同的方式**新**就是秒当失败时出于同样的原因。 若要重写默认值，调用`_set_new_mode(1)`早期在你的程序或与 NEWMODE 的链接。OBJ (请参阅[链接选项](../../c-runtime-library/link-options.md))。

当与 C 运行时库的调试版本链接应用程序**malloc**解析为[_malloc_dbg](malloc-dbg.md)。 有关堆在调试过程中如何托管的详细信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。

**malloc**标记`__declspec(noalias)`和`__declspec(restrict)`; 也就是说，保证函数不能修改全局变量，并且指针返回不使用别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
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

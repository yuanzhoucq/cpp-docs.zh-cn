---
title: malloc
ms.date: 4/2/2020
api_name:
- malloc
- _o_malloc
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: afe9264351110bc062d6168ef803fa6fb796538a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341578"
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

*大小*<br/>
要分配的字节数。

## <a name="return-value"></a>返回值

**malloc**返回指向已分配空间的空指针，如果内存不足，则**返回 NULL。** 要返回指向**void**以外的类型的指针，请使用返回值上强制转换的类型。 返回值指向的存储空间确保可以正好与对齐要求小于或等于基本对齐要求的任意对象类型的存储对齐。 （在视觉C++中，基本对齐是**双**字节或 8 个字节所需的对齐方式。 在以 64 位平台为目标的代码中，它是 16 字节。使用[_aligned_malloc](aligned-malloc.md)为具有较大对齐要求的对象分配存储，例如，SSE 类型[__m128](../../cpp/m128.md)和 **__m256**，以及通过使用`__declspec(align( n ))` **n**大于 8 的类型声明的类型。 如果*大小*为**0，malloc**将分配堆中的零长度项，并返回指向该项的有效指针。 始终检查从**malloc**返回，即使请求的内存量很小。

## <a name="remarks"></a>备注

**malloc**函数分配至少*大小*字节的内存块。 由于对齐和维护信息所需的空间，模块可能大于*大小*字节。

如果内存分配失败或请求的内存量超过 **_HEAP_MAXREQ，malloc**会将**errno**设置**到 ENOMEM。** **malloc** 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

启动代码使用**malloc**为 *_environ、envp*和*argv*变量分配存储。 **_environ** 以下函数及其宽字符对应项也称为**malloc。**

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[_exec 函数](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[_spawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[系统](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[getchar](getc-getwc.md)|[puts](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[得到](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

C++ [_set_new_mode](set-new-mode.md) 函数将为 **malloc** 设置新的处理程序模式。 新的处理程序模式指示在发生故障时 **，malloc**是否将调用[由 _set_new_handler](set-new-handler.md)设置的新处理程序例程。 默认情况下 **，malloc**不会在分配内存失败时调用新的处理程序例程。 您可以重写此默认行为，以便在**malloc**无法分配内存时 **，malloc**调用新处理程序例程的方式**与新运算符出于**相同原因失败时相同的方式调用新处理程序例程。 要覆盖默认值，请尽早`_set_new_mode(1)`调用程序，或与 NEWMODE 链接。OBJ（参见[链接选项](../../c-runtime-library/link-options.md)）。

当应用程序链接到 C 运行时库的调试版本时 **，malloc**解析为[_malloc_dbg](malloc-dbg.md)。 有关堆在调试过程中如何托管的详细信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。

**马洛克**被标记`__declspec(noalias)`和`__declspec(restrict)`;这意味着保证函数不修改全局变量，并且返回的指针不会别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**malloc**|\<stdlib.h> 和 \<malloc.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[自由](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>

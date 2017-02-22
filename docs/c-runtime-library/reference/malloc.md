---
title: "malloc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "malloc"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "malloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "malloc 函数"
  - "内存分配"
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# malloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分配内存块。  
  
## 语法  
  
```  
void *malloc(  
   size_t size   
);  
```  
  
#### 参数  
 `size`  
 要分配的字节。  
  
## 返回值  
 如果内存充足，则 `malloc` 返回无效的指针给分配的空间或 `NULL`。  若要返回指向类型的指针而不是 `void`，请对返回值使用类型转换。  返回值指向的存储空间保证适合储存任何类型的对象，该对象有一个相对于基本对齐方式，更少或同样的对齐方式要求。（Visual C\+\+ 中，基础的对齐方式是 `double` 或 8 字节所需的对齐方式。  在面向 64 位平台的代码中，为 16 字节。）使用 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 可为有更严格对齐要求的对象分配存储，例如 SSE 类型 [\_\_m128](../../cpp/m128.md) 和 `__m256`，以及使用 `__declspec(align(``n``))` 进行申明的类型，其中 `n` 大于 8。  如果 `size` 为 0，`malloc` 将在堆中分配长度为零的项，并将有效指针返回到该项中。  即使请求的内存量很小，也要每次都检查 `malloc` 的返回。  
  
## 备注  
 `malloc` 函数至少分配 `size` 位存储区域。  块大于 `size` 字节，这是由于对齐和维护信息需要空间。  
  
 如果内存分配失败，或者请求的内存数量超过 `_HEAP_MAXREQ`，那么 `malloc` 设置 `errno` 为 `ENOMEM`。  有关这和其他错误代码的信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 启动代码使用 `malloc` 将存储分配给 `_environ`、`envp` 和 `argv`。  以下函数及其宽字符副本也调用 `malloc`。  
  
|||||  
|-|-|-|-|  
|[calloc](../../c-runtime-library/reference/calloc.md)|[fscanf](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[\_getw](../../c-runtime-library/reference/getw.md)|[setvbuf](../../c-runtime-library/reference/setvbuf.md)|  
|[\_exec 函数](../../c-runtime-library/exec-wexec-functions.md)|[fseek](../../c-runtime-library/reference/fseek-fseeki64.md)|[\_popen](../../c-runtime-library/reference/popen-wpopen.md)|[\_spawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)|  
|[fgetc](../../c-runtime-library/reference/fgetc-fgetwc.md)|[fsetpos](../../c-runtime-library/reference/fsetpos.md)|[printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[\_strdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)|  
|[\_fgetchar](../../c-runtime-library/reference/fgetc-fgetwc.md)|[\_fullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)|[putc](../../c-runtime-library/reference/putc-putwc.md)|[系统](../../c-runtime-library/reference/system-wsystem.md)|  
|[fgets](../../c-runtime-library/reference/fgets-fgetws.md)|[fwrite](../../c-runtime-library/reference/fwrite.md)|[putchar](../../c-runtime-library/reference/putc-putwc.md)|[\_tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](../../c-runtime-library/reference/getc-getwc.md)|[\_putenv](../../c-runtime-library/reference/putenv-wputenv.md)|[ungetc](../../c-runtime-library/reference/ungetc-ungetwc.md)|  
|[fputc](../../c-runtime-library/reference/fputc-fputwc.md)|[getchar](../../c-runtime-library/reference/getc-getwc.md)|[puts](../../c-runtime-library/reference/puts-putws.md)|[vfprintf](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[\_fputchar](../../c-runtime-library/reference/fputc-fputwc.md)|[\_getcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)|[\_putw](../../c-runtime-library/reference/putw.md)|[vprintf](../../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|  
|[fputs](../../c-runtime-library/reference/fputs-fputws.md)|[\_getdcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)|[scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)||  
|[fread](../../c-runtime-library/reference/fread.md)|[获取](../../c-runtime-library/gets-getws.md)|[\_searchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)||  
  
 C\+\+ [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) 函数为 `malloc` 设置新处理程序模式。  新的处理程序模式指示，在失败时，`malloc` 是否就像 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 设置的那样调用新的处理程序实例。  默认情况下，`malloc` 不调用发生故障的新处理程序例程去分配内存。  您可重写此默认行为，这样一来，当 `malloc` 无法分配内存时， `malloc` 调用新的处理程序例程，其方式与出于相同原因的 `new` 运算符的操作相同。  重写默认值、调用  
  
```cpp  
_set_new_mode(1)  
```  
  
 在您程序的早期，或链接到 NEWMODE.OBJ（请参阅 [链接选项](../../c-runtime-library/link-options.md)）。  
  
 当应用程序与调试版本的 C 运行时库连接时，`malloc` 解析为 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 `malloc` 标记为 `__declspec(noalias)` 和 `__declspec(restrict)`；这意味着函数保证不修改全局变量，和返回的指针不用做别名。  有关更多信息，请参见[noalias](../../cpp/noalias.md)和[restrict](../../cpp/restrict.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`malloc`|\<stdlib.h\> 和 \<malloc.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```c  
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
  
  **分配给路径名称的内存空间**  
**释放的内存**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅 [平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md)
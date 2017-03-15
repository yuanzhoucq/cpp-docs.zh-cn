---
title: "realloc | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- realloc
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
- _brealloc
- _nrealloc
- realloc
- _frealloc
dev_langs:
- C++
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: dd20bf67c0854cf837ff5cf4f22308f977b06734
ms.lasthandoff: 02/24/2017

---
# <a name="realloc"></a>realloc
重新分配内存块。  
  
## <a name="syntax"></a>语法  
  
```  
void *realloc(  
   void *memblock,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>参数  
 `memblock`  
 指向之前已分配内存块的指针。  
  
 `size`  
 新大小（字节）。  
  
## <a name="return-value"></a>返回值  
 `realloc` 将返回指向重新分配的（并且可能已移动的）内存块的 `void` 指针。  
  
 如果没有足够可用的内存将块扩展到给定大小，则原始块将保持不变，并返回 `NULL`。  
  
 如果 `size` 为零，则释放由 `memblock` 指向的块；返回值为 `NULL`，而 `memblock` 仍指向已释放的块。  
  
 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 `void` 的指针，请在返回值中使用类型转换。  
  
## <a name="remarks"></a>备注  
 `realloc` 函数更改已分配内存块的大小。 `memblock` 参数指向内存块的开头。 如果 `memblock` 为 `NULL`，则 `realloc` 与 `malloc` 的行为相同，并分配一个 `size` 字节的新块。 如果 `memblock` 不为 `NULL`，则它应是指向以前调用 `calloc`、`malloc` 或 `realloc` 所返回的指针。  
  
 `size` 参数提供块的新大小（字节）。 块的内容不随其新旧大小而更改，尽管新块可以在不同的位置。 因为新块可以在新的内存位置，所以由 `realloc` 返回的指针并非一定指向通过 `memblock` 参数传递的指针。 `realloc` 在缓冲区增长的情况下不会将新分配的内存清零。  
  
 如果内存分配失败或请求的内存量超过 `_HEAP_MAXREQ`，则 `realloc` 将 `errno` 设置为 `ENOMEM`。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `realloc` 调用 `malloc` 以使用 C++ [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) 函数设置新的处理程序模式。 新的处理程序模式将指示 `malloc` 是否在失败时调用由 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md) 设置的新处理程序例程。 默认情况下，`malloc` 在失败时不调用新的处理程序例程来分配内存。 可以替代此默认行为，以便在 `realloc` 无法分配内存时，`malloc` 将以 `new` 运算符由于相同原因失败时的同一方法调用新的处理程序例程。 若要替代默认值，请在程序的早期调用：  
  
```  
_set_new_mode(1)  
```  
  
 或链接到 NEWMODE.OBJ（请参阅[链接选项](../../c-runtime-library/link-options.md)）。  
  
 当应用程序与调试版的 C 运行时库链接时，`realloc` 将解析为 [_realloc_dbg](../../c-runtime-library/reference/realloc-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。  
  
 `realloc` 被标记为 `__declspec(noalias)` 和 `__declspec(restrict)`，也就是说确保该函数不能修改全局变量，并且返回的指针不使用别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`realloc`|\<stdlib.h> 和 \<malloc.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_realloc.c  
// This program allocates a block of memory for  
// buffer and then uses _msize to display the size of that  
// block. Next, it uses realloc to expand the amount of  
// memory used by buffer and then calls _msize again to  
// display the new amount of memory allocated to buffer.  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   long *buffer, *oldbuffer;  
   size_t size;  
  
   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )  
      exit( 1 );  
  
   size = _msize( buffer );  
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );  
  
   // Reallocate and show new size:  
   oldbuffer = buffer;     // save pointer in case realloc fails  
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))   
        ==  NULL )  
   {  
      free( oldbuffer );  // free original block  
      exit( 1 );  
   }  
   size = _msize( buffer );  
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",   
            size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
```Output  
Size of block after malloc of 1000 longs: 4000  
Size of block after realloc of 1000 more longs: 8000  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)

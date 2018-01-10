---
title: "calloc | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: calloc
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
f1_keywords: calloc
dev_langs: C++
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e660413b3d3a95748432d411e92ef03a8e262409
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="calloc"></a>calloc
使用初始化为 0 的元素分配内存中的数组。  
  
## <a name="syntax"></a>语法  
  
```  
void *calloc(   
   size_t num,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>参数  
 `num`  
 元素数量。  
  
 `size`  
 每个元素的长度（以字节为单位）。  
  
## <a name="return-value"></a>返回值  
 `calloc` 返回指向已分配空间的指针。 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 `void` 的指针，请在返回值中使用类型转换。  
  
## <a name="remarks"></a>备注  
 `calloc` 函数为 `num` 元素的数组分配存储空间，每个长度为 `size` 字节。 将每个元素初始化为 0。  
  
 如果内存分配失败或请求的内存量超过 `_HEAP_MAXREQ`，`calloc` 会将 `errno` 设置为 `ENOMEM`。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `calloc` 调用 `malloc` 以使用 C++ [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) 函数设置新的处理程序模式。 新的处理程序模式将指示 `malloc` 是否在失败时调用由 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md) 设置的新处理程序例程。 默认情况下，`malloc` 在失败时不调用新的处理程序例程来分配内存。 可以替代此默认行为，以便在 `calloc` 无法分配内存时，`malloc` 将以 `new` 运算符由于相同原因失败时的同一方法调用新的处理程序例程。 若要重写默认值，请在程序的早期调用：  
  
```  
_set_new_mode(1)  
```  
  
 或链接到 NEWMODE.OBJ（请参阅[链接选项](../../c-runtime-library/link-options.md)）。  
  
 当应用程序与调试版的 C 运行时库链接时，`calloc` 将解析为 [_calloc_dbg](../../c-runtime-library/reference/calloc-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。  
  
 `calloc` 被标记为 `__declspec(noalias)` 和 `__declspec(restrict)`，也就是说确保该函数不能修改全局变量，并且返回的指针不使用别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`calloc`|\<stdlib.h> 和 \<malloc.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_calloc.c  
// This program uses calloc to allocate space for  
// 40 long integers. It initializes each element to zero.  
  
#include <stdio.h>  
#include <malloc.h>  
  
int main( void )  
{  
   long *buffer;  
  
   buffer = (long *)calloc( 40, sizeof( long ) );  
   if( buffer != NULL )  
      printf( "Allocated 40 long integers\n" );  
   else  
      printf( "Can't allocate memory\n" );  
   free( buffer );  
}  
```  
  
```Output  
Allocated 40 long integers  
```  
  
## <a name="see-also"></a>请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)
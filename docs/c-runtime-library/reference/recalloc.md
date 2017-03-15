---
title: "_recalloc | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _recalloc
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
- _recalloc
- recalloc
dev_langs:
- C++
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
caps.latest.revision: 9
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
ms.openlocfilehash: 89626019b42a478b2dfe3800e2f732ba6b90d106
ms.lasthandoff: 02/24/2017

---
# <a name="recalloc"></a>_recalloc
`realloc` 和 `calloc` 的组合。 重新分配内存中的数组并将其元素初始化为 0。  
  
## <a name="syntax"></a>语法  
  
```  
void *_recalloc(   
   void *memblock  
   size_t num,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>参数  
 `memblock`  
 指向之前已分配内存块的指针。  
  
 `num`  
 元素数量。  
  
 `size`  
 每个元素的长度（以字节为单位）。  
  
## <a name="return-value"></a>返回值  
 `_recalloc` 将返回指向重新分配的（并且可能已移动的）内存块的 `void` 指针。  
  
 如果没有足够可用的内存将块扩展到给定大小，则原始块将保持不变，并返回 `NULL`。  
  
 如果请求的大小为零，则释放由 `memblock` 指向的块；返回值为 `NULL`，而 `memblock` 仍指向已释放的块。  
  
 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 `void` 的指针，请在返回值中使用类型转换。  
  
## <a name="remarks"></a>备注  
 _`recalloc` 函数更改已分配内存块的大小。 `memblock` 参数指向内存块的开头。 如果 `memblock` 为 `NULL`，则 \_`recalloc` 的行为与 [calloc](../../c-runtime-library/reference/calloc.md) 相同，并分配一个 `num` * `size` 字节的新块。 将每个元素初始化为 0。 如果 `memblock` 不为 `NULL`，则它应是指向以前调用 `calloc`、[malloc](../../c-runtime-library/reference/malloc.md) 或 [realloc](../../c-runtime-library/reference/realloc.md) 所返回的指针。  
  
 因为新块可以在新的内存位置，所以由 _`recalloc` 返回的指针并非一定是指向通过 `memblock` 参数传递的指针。  
  
 如果内存分配失败或请求的内存量超过 `_HEAP_MAXREQ`，则 `_recalloc` 将 `errno` 设置为 `ENOMEM`。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `recalloc` 调用 `realloc` 以使用 C++ [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) 函数设置新的处理程序模式。 新的处理程序模式将指示 `realloc` 是否在失败时调用由 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md) 设置的新处理程序例程。 默认情况下，`realloc` 在失败时不调用新的处理程序例程来分配内存。 可以替代此默认行为，以便在 _`recalloc` 无法分配内存时，`realloc` 可以调用新的处理程序例程，方法与 `new` 运算符出于相同原因无法分配内存时所执行的操作一样。 若要替代默认值，请在程序的早期调用：  
  
```  
_set_new_mode(1)  
```  
  
 或链接到 NEWMODE.OBJ。  
  
 当应用程序与调试版的 C 运行时库链接时，_`recalloc` 将解析为 [_recalloc_dbg](../../c-runtime-library/reference/recalloc-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。  
  
 `_recalloc` 被标记为 `__declspec(noalias)` 和 `__declspec(restrict)`，也就是说确保该函数不能修改全局变量，并且返回的指针不使用别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_recalloc`|\<stdlib.h> 和 \<malloc.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [_recalloc_dbg](../../c-runtime-library/reference/recalloc-dbg.md)   
 [_aligned_recalloc](../../c-runtime-library/reference/aligned-recalloc.md)   
 [_aligned_offset_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [链接选项](../../c-runtime-library/link-options.md)

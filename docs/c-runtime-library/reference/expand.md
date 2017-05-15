---
title: "_expand | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: b82bcf0de4f17a718389ef358a11a88e9bd999c1
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="expand"></a>_expand
更改内存块的大小。  
  
## <a name="syntax"></a>语法  
  
```  
void *_expand(   
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
 `_expand` 将返回指向重新分配的内存块的 void 指针。 `_expand` 与 `realloc` 不同，它无法移动块以更改其大小。 因此，如果有足够的可用内存来扩展块而无需移动它，则 `_expand` 的 `memblock` 参数与返回值相同。  
  
 `_expand` 在其操作过程中检测到错误时返回 `NULL`。 例如，如果 `_expand` 用于收缩内存块，它可能会在小块堆或无效的块指针中检测到损坏，并返回 `NULL`。  
  
 如果在不移动块的情况下，没有足够的内存将块扩展到给定大小，则函数返回 `NULL`。 `_expand` 从不返回扩展到小于请求大小的块。 如果出现失败，则 `errno` 指示失败原因。 有关 `errno` 的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要检查项目的新大小，请使用 `_msize`。 若要获取指向类型而非 `void` 的指针，请在返回值中使用类型转换。  
  
## <a name="remarks"></a>备注  
 `_expand` 函数通过尝试扩展或收缩块且不在堆中移动其位置的情况下，更改以前分配的内存块的大小。 `memblock` 参数指向块的开头。 `size` 参数指定块的新大小（以字节为单位）。 根据新大小和旧大小中的较短者，块内容保持不变。 `memblock` 不应是已释放的块。  
  
> [!NOTE]
>  在 64 位平台上，如果块的新大小小于当前大小，则 `_expand` 不能对块进行收缩；尤其是，如果块的大小小于 16K 并在低碎片堆中进行分配，则 `_expand` 保持块不变并返回 `memblock`。  
  
 当应用程序与调试版的 C 运行库链接时，`_expand` 将解析为 [_expand_dbg](../../c-runtime-library/reference/expand-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。  
  
 此函数验证其参数。 如果 `memblock` 为空指针，此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `NULL`。 如果 `size` 大于 `_HEAP_MAXREQ`，则 `errno` 被设置为 `ENOMEM`，且函数返回 `NULL`。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_expand`|\<malloc.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_expand.c  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char *bufchar;  
   printf( "Allocate a 512 element buffer\n" );  
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )  
      exit( 1 );  
   printf( "Allocated %d bytes at %Fp\n",   
         _msize( bufchar ), (void *)bufchar );  
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )  
      printf( "Can't expand" );  
   else  
      printf( "Expanded block to %d bytes at %Fp\n",   
            _msize( bufchar ), (void *)bufchar );  
   // Free memory   
   free( bufchar );  
   exit( 0 );  
}  
```  
  
```Output  
Allocate a 512 element buffer  
Allocated 512 bytes at 002C12BC  
Expanded block to 1024 bytes at 002C12BC  
```  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_msize](../../c-runtime-library/reference/msize.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)

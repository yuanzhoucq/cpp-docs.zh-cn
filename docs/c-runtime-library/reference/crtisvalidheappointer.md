---
title: "_CrtIsValidHeapPointer | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtIsValidHeapPointer
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
apitype: DLLExport
f1_keywords:
- CrtlsValidHeapPointer
- _CrtIsValidHeapPointer
dev_langs:
- C++
helpviewer_keywords:
- _CrtIsValidHeapPointer function
- CrtIsValidHeapPointer function
ms.assetid: caf597ce-1b05-4764-9f37-0197a982bec5
caps.latest.revision: 12
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
ms.openlocfilehash: a046822352800d01fb16ef8ef992dde6eeaf2fc2
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="crtisvalidheappointer"></a>_CrtIsValidHeapPointer
验证确保指定的指针位于某些 C 运行时库分配的堆中，但不一定在由调用方的 CRT 库分配的堆中。 在 Visual Studio 2010 之前的 CRT 版本中，这将验证指定的指针是否位于本地堆（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
  
      int _CrtIsValidHeapPointer(   
   const void *userData   
);  
```  
  
#### <a name="parameters"></a>参数  
 `userData`  
 指向已分配内存块的开头的指针。  
  
## <a name="return-value"></a>返回值  
 如果指定的指针位于所有 CRT 库实例所共享的堆中，则 `_CrtIsValidHeapPointer` 返回 TRUE。 在 Visual Studio 2010 之前的 CRT 版本中，如果指定的指针位于本地堆，则将返回 TRUE。 否则，此函数返回 FALSE。  
  
## <a name="remarks"></a>备注  
 建议你不要使用此函数。 从 Visual Studio 2010 CRT 库开始，所有 CRT 库共享一个操作系统堆 - *进程堆*。 `_CrtIsValidHeapPointer` 函数报告指针是否被分配到 CRT 堆中，但不报告它是否由调用方的 CRT 库进行分配。 例如，存在使用 Visual Studio 2010 版本的 CRT 库分配的块。 如果由 Visual Studio 2012 版本的 CRT 库导出的 `_CrtIsValidHeapPointer` 函数测试指针，则返回 TRUE。 此测试不再有用。 在 Visual Studio 2010 之前版本的 CRT 库中，此函数用于确保特定的内存地址位于本地堆中。 本地堆是指由 C 运行库的特定实例创建和管理的堆。 如果动态链接库 (DLL) 包含到运行时库的静态链接，则它自身具有运行时堆的实例，从而本身具有独立于应用程序本地堆的堆。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，会在预处理过程中删除对 `_CrtIsValidHeapPointer` 的调用。  
  
 因为此函数返回 TRUE 或 FALSE，因此可将它传递到其中一个 [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏，以创建一种简单的调试错误处理机制。 如果本地堆中没有指定的地址，则以下示例将导致断言失败：  
  
```  
_ASSERTE( _CrtIsValidHeapPointer( userData ) );  
```  
  
 有关如何将 `_CrtIsValidHeapPointer` 与其他调试函数和宏一起使用的详细信息，请参阅[用于报告的宏](/visualstudio/debugger/macros-for-reporting)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_CrtIsValidHeapPointer`|\<crtdbg.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="example"></a>示例  
 下面的示例演示如何测试内存在与 Visual Studio 2010 之前的 C 运行时库一起使用时是否有效。 此示例供旧的 CRT 库代码的用户使用。  
  
```  
// crt_isvalid.c  
/*  
 * This program allocates a block of memory using _malloc_dbg  
 * and then tests the validity of this memory by calling   
 * _CrtIsMemoryBlock,_CrtIsValidPointer, and _CrtIsValidHeapPointer.  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
#define  TRUE   1  
#define  FALSE  0  
  
int main( void )  
{  
        char *my_pointer;  
  
        /*   
         * Call _malloc_dbg to include the filename and line number  
         * of our allocation request in the header information  
         */  
        my_pointer = (char *)_malloc_dbg( sizeof(char) * 10,   
        _NORMAL_BLOCK, __FILE__, __LINE__ );  
  
        // Ensure that the memory got allocated correctly  
        _CrtIsMemoryBlock((const void *)my_pointer, sizeof(char) * 10,   
        NULL, NULL, NULL );  
  
         // Test for read/write accessibility  
        if (_CrtIsValidPointer((const void *)my_pointer,   
        sizeof(char) * 10, TRUE))  
                printf("my_pointer has read and write accessibility.\n");  
        else  
                printf("my_pointer only has read access.\n");  
  
        // Make sure my_pointer is within the local heap  
        if (_CrtIsValidHeapPointer((const void *)my_pointer))  
                printf("my_pointer is within the local heap.\n");  
        else  
                printf("my_pointer is not located within the local"  
                       " heap.\n");  
  
        free(my_pointer);  
}  
```  
  
## <a name="output"></a>输出  
  
```  
my_pointer has read and write accessibility.  
my_pointer is within the local heap.  
```  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)

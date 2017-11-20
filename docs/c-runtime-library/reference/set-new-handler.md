---
title: "_set_new_handler | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_new_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_new_handler
- set_new_handler
dev_langs: C++
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5ab5d0da21b7034d1a5ab336854b87ae2d2cc429
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="setnewhandler"></a>_set_new_handler
如果 `new` 运算符无法分配内存，则将控制权传输到错误处理机制。  
  
## <a name="syntax"></a>语法  
  
```  
_PNH _set_new_handler(  
   _PNH pNewHandler   
);  
```  
  
#### <a name="parameters"></a>参数  
 `pNewHandler`  
 指向应用程序提供的内存处理函数的指针。 自变量为 0 会导致新的处理程序被移除。  
  
## <a name="return-value"></a>返回值  
 返回指向由 `_set_new_handler` 注册的上一个异常处理函数的指针，以便稍后能还原上一个函数。 如果之前未设置函数，则可使用返回值还原默认行为；此值可以为 `NULL`。  
  
## <a name="remarks"></a>备注  
 如果 `_set_new_handler` 运算符无法分配内存，则 C++ `new` 函数将指定获取控制权的异常处理函数。 如果 `new` 失败，则运行时系统将自动调用已作为参数传递给 `_set_new_handler` 的异常处理函数。 New.h 中定义的 `_PNH` 是一个指向函数的指针，该函数返回 `int` 类型并采用 `size_t` 类型的参数。 使用 `size_t` 指定要分配的空间量。  
  
 没有默认处理程序。  
  
 `_set_new_handler` 实际上是垃圾回收方案。 如果您的函数返回非零值，则运行时系统会重试分配；如果您的函数返回 0，则将失败。  
  
 程序中的 `_set_new_handler` 函数的匹配项将向运行时系统注册参数列表中指定的异常处理函数：  
  
```  
#include <new.h>  
int handle_program_memory_depletion( size_t )  
{  
   // Your code  
}  
int main( void )  
{  
   _set_new_handler( handle_program_memory_depletion );  
   int *pi = new int[BIG_NUMBER];  
}  
```  
  
 您可以保存最后传递给 `_set_new_handler` 函数的函数地址，并在稍后恢复它：  
  
```  
_PNH old_handler = _set_new_handler( my_handler );  
   // Code that requires my_handler  
   _set_new_handler( old_handler )  
   // Code that requires old_handler  
```  
  
 C++ [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) 函数将为 [malloc](../../c-runtime-library/reference/malloc.md) 设置新的处理程序模式。 新的处理程序模式将指示 `malloc` 是否在失败时调用由 `_set_new_handler` 设置的新处理程序例程。 默认情况下，`malloc` 在失败时不调用新的处理程序例程来分配内存。 可以替代此默认行为，以便在 `malloc` 无法分配内存时，`malloc` 将以 `new` 运算符由于相同原因失败时的同一方法调用新的处理程序例程。 若要重写默认值，请调用：  
  
```  
_set_new_mode(1)  
```  
  
 在您程序的早期，或链接到 Newmode.obj。  
  
 如果用户定义`operator new`提供新的处理程序函数不会自动调用失败。  
  
 有关详细信息，请参阅 *C++ 语言参考*中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md)。  
  
 所有动态链接的 DLL 或可执行文件都有一个 `_set_new_handler` 处理程序；即使您调用 `_set_new_handler`，您的处理程序也可能被另一个处理程序替代，或者将替换由其他 DLL 或可执行文件设置的处理程序。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_set_new_handler`|\<new.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 在此示例中，当分配失败时，控件权将转交给 MyNewHandler。 传递给 MyNewHandler 的参数是请求的字节数。 从 MyNewHandler 返回的值是一个指示是否应重试分配的标志：非零值指示应重试分配，零值指示分配已失败。  
  
```  
// crt_set_new_handler.cpp  
// compile with: /c  
#include <stdio.h>  
#include <new.h>  
#define BIG_NUMBER 0x1fffffff  
  
int coalesced = 0;  
  
int CoalesceHeap()  
{  
   coalesced = 1;  // Flag RecurseAlloc to stop   
   // do some work to free memory  
   return 0;  
}  
// Define a function to be called if new fails to allocate memory.  
int MyNewHandler( size_t size )  
{  
   printf("Allocation failed. Coalescing heap.\n");  
  
   // Call a function to recover some heap space.  
   return CoalesceHeap();  
}  
  
int RecurseAlloc() {  
   int *pi = new int[BIG_NUMBER];  
   if (!coalesced)  
      RecurseAlloc();  
   return 0;  
}  
  
int main()  
{  
   // Set the failure handler for new to be MyNewHandler.  
   _set_new_handler( MyNewHandler );  
   RecurseAlloc();  
}  
```  
  
```Output  
Allocation failed. Coalescing heap.  
  
This application has requested the Runtime to terminate it in an unusual way.  
Please contact the application's support team for more information.  
```  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)
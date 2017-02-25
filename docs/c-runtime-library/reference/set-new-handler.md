---
title: "_set_new_handler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_new_handler"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_set_new_handler"
  - "set_new_handler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_set_new_handler 函数"
  - "错误处理"
  - "set_new_handler 函数"
  - "将控件传输到错误处理程序"
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _set_new_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果 `new` 操作数未能成功分配内存，则将控制权转移给错误处理机制。  
  
## 语法  
  
```  
_PNH _set_new_handler(  
   _PNH pNewHandler   
);  
```  
  
#### 参数  
 `pNewHandler`  
 指向应用程序所提供内存处理函数的指针。  参数为0导致新处理程序被移除。  
  
## 返回值  
 返回指向由 `_set_new_handler` 注册的前异常处理函数，以便前面的函数之后可能还原。  如果以前尚未设置函数，返回值可用于存储默认行为；此值可能为`NULL`。  
  
## 备注  
 如果 `new` 运算符无法分配内存，C\+\+ `_set_new_handler` 函数中指定异常处理函数的控制权。  如果 `new` 失败，则运行时系统自动调用作为参数传递给处理的 `_set_new_handler`异常的函数。  `_PNH`定义在 New.h，是指向函数返回 `int` 类型并采用类型为 `size_t`的参数。  使用 `size_t` 指定要分配的空间。  
  
 没有默认处理程序。  
  
 `_set_new_handler` 实际上是垃圾回收方案。  运行时系统重试分配，每次递归函数将返回非零值并失败，则函数返回 0。  
  
 `_set_new_handler` 函数匹配项中的函数使用异常处理在运行时系统的参数列表指定程序的寄存器：  
  
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
  
 您可以保存一传递给 `_set_new_handler` 函数的地址并在以后恢复它：  
  
```  
_PNH old_handler = _set_new_handler( my_handler );  
   // Code that requires my_handler  
   _set_new_handler( old_handler )  
   // Code that requires old_handler  
```  
  
 C\+\+ [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) 函数为[malloc](../../c-runtime-library/reference/malloc.md)设置新处理程序模式。  新的处理程序模式指示，在失败时，`malloc` 是否就像`_set_new_handler` 设置的那样调用新的处理程序实例。  默认情况下，`malloc` 不调用发生故障的新处理程序例程去分配内存。  您可重写此默认行为，这样一来，当 `malloc` 无法分配内存时， `malloc` 调用新的处理程序例程，其方式与出于相同原因的 `new` 运算符的操作相同。  重写默认值、调用:  
  
```  
_set_new_mode(1)  
```  
  
 在您程序的早期，或链接到 Newmode.obj。  
  
 如果用户提供定义的 `operator new`，则新处理程序函数不是自动对失败。  
  
 有关详细信息，请参阅*《C\+\+ 语言参考》*中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md)。  
  
 所有的动态链接DLLs 或 EXEs 有`_set_new_handler`，即使您调用`_set_new_handler`单处理程序可能会被另一个替代，或者您用另外的DLL 或 EXE替代处理程序。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_set_new_handler`|\<new.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 在此示例中，中，当赋值失败时，将控件传输到 MyNewHandler。  参数传递给 MyNewHandler 是请求的字节数。  从 MyNewHandler 返回的值是一的标志是否应再次尝试分配：非零值指示应重试分配，并且，对于一个值指示分配失败。  
  
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
  
  **失败的任务。  联合堆。**  
**此应用程序已请求运行时以异常方式终止它。**  
**请与应用程序技术支持团队联系，以便获得更多信息。**    
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)
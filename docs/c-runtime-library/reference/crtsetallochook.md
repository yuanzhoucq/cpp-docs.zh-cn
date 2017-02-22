---
title: "_CrtSetAllocHook | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetAllocHook"
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
apitype: "DLLExport"
f1_keywords: 
  - "_CrtSetAllocHook"
  - "CrtSetAllocHook"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtSetAllocHook 函数"
  - "CrtSetAllocHook 函数"
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _CrtSetAllocHook
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过挂接到C运行时调试内存分配程序（仅调试版本）来安装一个客户端自定义分配函数。  
  
## 语法  
  
```  
_CRT_ALLOC_HOOK _CrtSetAllocHook(  
   _CRT_ALLOC_HOOK allocHook   
);  
```  
  
#### 参数  
 `allocHook`  
 新客户端自定义分配函数挂接到 C 运行时调试内存分配进程。  
  
## 返回值  
 如果 `allocHook` 为 `NULL`，则返回之前定义的分配挂钩函数或是 `NULL` 。  
  
## 备注  
 `_CrtSetAllocHook` 允许应用程序挂接自身的分配函数到运行时调试库内存分配程序中。  因此，每调用调试分配函数分配，重新分配或释放内存内存块触发对应用程序的挂钩函数的调用。  `_CrtSetAllocHook` 提供一个应用程序，其使用一个简单的方式测试应用程序如何处理内存不足的情况，检查分配模式的能力和记录分配信息供以后分析的机会。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，在预处理期间移除对 `_CrtSetAllocHook` 的调用。  
  
 `_CrtSetAllocHook` 函数安装在 `allocHook` 指定的新的客户端自定义分配函数，并返回之前自定义的挂钩函数。  下面的示例演示一个客户端自定义的分配挂钩应如何被原型化：  
  
```  
int YourAllocHook( int allocType, void *userData, size_t size, int   
blockType, long requestNumber, const unsigned char *filename, int   
lineNumber);  
```  
  
 `allocType` 自变量指定触发分配的挂钩函数调用的分配操作 `(_HOOK_ALLOC` 、 `_HOOK_REALLOC` 和 `_HOOK_FREE`\) 的类型，  当触发分配的类型为`_HOOK_FREE`， `userData` 是指向即将被释放的内存块的用户数据部分的指针。  然而，当触发分配类型为 `_HOOK_ALLOC` 或 `_HOOK_REALLOC`， 因为还未分配内存块，所以`userData` 为 `NULL`。  
  
 `size` 指定内存块的字节大小， `blockType` 指示内存块的类型，`requestNumber` 是内存块中的对象分配排序号，并且如果可用，`filename` 和 `lineNumber` 指定资源文件名字和启动触发分配操作的行数。  
  
 在挂钩函数完成此过程后，必须返回布尔值，断定主 C 运行时分配进程如何继续。  当挂钩函数想要继续执行主分配进程，就像从未调用挂钩函数，然后挂钩函数返回 `TRUE`。  这会导致执行原始触发的赋值操作。  使用这种实现，钩子函数可以收集并保存配置信息，以供日后分析，而不会干扰在调试堆的当前分配操作或状态。  
  
 当挂钩函数想要继续执行主分配进程，就像调用触发分配操作失败，然后挂钩函数返回 `FALSE`。  使用这种实现，钩子函数可以模拟多种内存状况和调试堆状态来测试应用程序如何处理每种情况。  
  
 要清除挂钩函数，请将 `NULL` 传递给 `_CrtSetAllocHook`。  
  
 有关 `_CrtSetAllocHook` 与其他内存管理函数如何使用，或是如何写入自己的客户端自定义挂钩函数的详细信息，请参阅 [编写调试挂钩函数](../Topic/Debug%20Hook%20Function%20Writing.md)。  
  
> [!NOTE]
>  在`/clr:pure`以下，不支持 `_CrtSetAllocHook` 。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_CrtSetAllocHook`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 示例  
 对于如何使用 `_CrtSetAllocHook` 的例子，请参阅 [crt\_dbg2](http://msdn.microsoft.com/zh-cn/21e1346a-6a17-4f57-b275-c76813089167)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_CrtGetAllocHook](../../c-runtime-library/reference/crtgetallochook.md)
---
title: "longjmp | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "longjmp"
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
  - "longjmp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "longjmp 函数"
  - "还原堆栈环境和执行区域设置"
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# longjmp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

还原堆栈环境和执行区域设置。  
  
## 语法  
  
```  
  
      void longjmp(  
   jmp_buf env,  
   int value   
);  
```  
  
#### 参数  
 `env`  
 存储环境变量。  
  
 *值*  
 将返回的值设置成 `setjmp`。  
  
## 备注  
 `longjmp` 函数将在 `env` 之前保存的堆栈环境以及执行区域设置的 `setjmp`。  `setjmp` and `longjmp` provide a way to execute a nonlocal `goto`它们通常用于将执行控制传递给之前调用的例程中的错误处理或恢复代码，而不使用标准调用或返回约定。  
  
 对 `setjmp` 的调用导致 `env`在当前堆栈环境保存。  对`longjmp` 的后续调用应还原保存的环境并返回控件与在对应的 `setjmp` 调用之后的点。  继续执行，就好像这些 *值* 是由 `setjmp` 调用返回。  当调用 `longjmp`时，所有变量 \(除注册变量\) 定期接收控件包含值是可行的 。  寄存器变量值是不可预知的。  `setjmp` 返回值是非零绑定。  如果 *值* 传递为 0，值 1 在实际返回进行替换。  
  
 在调用 `setjmp` 返回的函数之前调用 `longjmp` ;则结果是不可预知的。  
  
 注意以下限制，在使用 `longjmp`时：  
  
-   不要假设，寄存器变量的值将保持不变。  在 `longjmp` 操作后，在定期调用 `setjmp` 的寄存器变量不能恢复为适当的值。  
  
-   除非中断由浮点异常引起的，请不要使用 `longjmp` 来将控制从一中断处理例程。  在这种情况下，程序可能从中断处理程序返回通过 `longjmp`，则通过调用 `_fpreset`首先重新初始化浮点运算包。  
  
     当使用 `setjmp` 和 `longjmp` 在**附注**程序 C\+\+ 时，小心。  由于这些函数不支持 C\+\+ 对象语义，使用异常处理机制。C\+\+ 都更加安全的。  
  
 有关详细信息，请参阅[Using setjmp and longjmp](../../cpp/using-setjmp-longjmp.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`longjmp`|\<setjmp.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
 请参阅 [\_fpreset](../../c-runtime-library/reference/fpreset.md) 示例。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [setjmp](../../c-runtime-library/reference/setjmp.md)
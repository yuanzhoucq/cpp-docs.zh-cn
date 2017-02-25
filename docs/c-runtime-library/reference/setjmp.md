---
title: "setjmp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "setjmp"
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
  - "setjmp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "程序 [C++], 保存状态"
  - "当前状态"
  - "setjmp 函数"
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# setjmp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

保存项目的当前状态。  
  
## 语法  
  
```  
int setjmp(  
   jmp_buf env   
);  
```  
  
#### 参数  
 `env`  
 存储环境变量。  
  
## 返回值  
 在保存栈环境后返回 0。  如果 `setjmp` 返回导致调用 `longjmp`，则返回 `longjmp`的 `value` 参数，或者如果 `longjmp` 的参数 `value` 是 0，则`setjmp` 返回1。  无错误返回。  
  
## 备注  
 `setjmp` 函数保存栈环境， 使用`longjmp`环境，您可以随后还原。  当一起使用时，`setjmp` 和 `longjmp` 提供一种方法执行非本地 `goto`.  它们通常用于将执行控制传递给之前调用的例程中的错误处理或恢复代码，而不使用常用调用或返回约定。  
  
 对 `setjmp` 的调用保存在 `env`的当前堆栈环境中。  对 `longjmp` 的后续调用应还原保存的环境并返回控件与在对应的 `setjmp` 调用之后的点。  当调用 `longjmp` 时，所有变量 \(除注册变量\) 定期接收控件包含值是可行的 。  
  
 使用 `setjmp` 从本机跳到托管代码是不可能的。  
  
 **Note** `setjmp` 和 `longjmp` 不支持 C\+\+ 对象语义。  在 C\+\+ 程序，请使用 C\+\+异常处理机制。  
  
 有关详细信息，请参阅[Using setjmp and longjmp](../../cpp/using-setjmp-longjmp.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`setjmp`|\<setjmp.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [\_fpreset](../../c-runtime-library/reference/fpreset.md) 示例。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [longjmp](../../c-runtime-library/reference/longjmp.md)   
 [\_setjmp3](../../c-runtime-library/setjmp3.md)
---
title: "特定于语言的处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 6503e0cd-2d3a-4330-a925-8bed8c27c2be
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 特定于语言的处理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

只要设置了 UNW\_FLAG\_EHANDLER 或 UNW\_FLAG\_UHANDLER 标志，UNWIND\_INFO 中就存在语言特定处理程序的相对地址。  正如上一节中描述的那样，语言特定处理程序作为异常处理程序搜索的一部分或展开代码的一部分进行调用。  它具有以下原型：  
  
```  
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (  
    IN PEXCEPTION_RECORD ExceptionRecord,  
    IN ULONG64 EstablisherFrame,  
    IN OUT PCONTEXT ContextRecord,  
    IN OUT PDISPATCHER_CONTEXT DispatcherContext  
);  
```  
  
 **ExceptionRecord** 提供指向具有标准 Win64 定义的异常记录的指针。  
  
 **EstablisherFrame** 是此函数的固定堆栈分配的基地址。  
  
 **ContextRecord** 指向引发异常时的异常上下文（在使用异常处理程序时）或当前的“展开”上下文（在使用终止处理程序时）。  
  
 **DispatcherContext** 指向此函数的发送程序上下文。  它具有以下定义：  
  
```  
typedef struct _DISPATCHER_CONTEXT {  
    ULONG64 ControlPc;  
    ULONG64 ImageBase;  
    PRUNTIME_FUNCTION FunctionEntry;  
    ULONG64 EstablisherFrame;  
    ULONG64 TargetIp;  
    PCONTEXT ContextRecord;  
    PEXCEPTION_ROUTINE LanguageHandler;  
    PVOID HandlerData;  
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;  
```  
  
 **ControlPc** 是此函数中 RIP 的值。  这是异常地址或控件将建立函数保留到的地址。  这是用于确定控件是否在此函数的某个被保护构造（例如，\_\_try\/\_\_except 或 \_\_try\/\_\_finally 的 \_\_try 块）中的 RIP。  
  
 **ImageBase** 是包含此函数的模块的映像基（加载地址），该映像基将被添加到函数项和展开信息中使用的 32 位偏移量中以记录相对地址。  
  
 **FunctionEntry** 提供指向 RUNTIME\_FUNCTION 函数项的指针，该函数项包含函数和此函数的展开信息映像基相对地址。  
  
 **EstablisherFrame** 是此函数的固定堆栈分配的基地址。  
  
 **TargetIp** 提供一个可选指令地址，该地址指定展开代码的连续地址。  如果没有指定 **EstablisherFrame**，则忽略此地址。  
  
 **ContextRecord** 指向系统异常调度\/展开代码使用的异常上下文。  
  
 **LanguageHandler** 指向正在被调用的语言特定语言处理程序例程。  
  
 **HandlerData** 指向此函数的语言特定处理程序数据。  
  
## 请参阅  
 [异常处理 \(x64\)](../build/exception-handling-x64.md)
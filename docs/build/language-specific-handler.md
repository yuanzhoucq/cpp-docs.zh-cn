---
title: 语言特定的处理程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6503e0cd-2d3a-4330-a925-8bed8c27c2be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6cbfbe6a9b98828a63fb4a092717bfab583e9a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="language-specific-handler"></a>特定于语言的处理程序
语言特定的处理程序的相对地址中不存在 UNWIND_INFO 只要设置了 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 的标志。 如前一部分中所述，语言特定的处理程序称为作为一部分的异常处理程序搜索或展开代码的一部分。 它具有以下原型：  
  
```  
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (  
    IN PEXCEPTION_RECORD ExceptionRecord,  
    IN ULONG64 EstablisherFrame,  
    IN OUT PCONTEXT ContextRecord,  
    IN OUT PDISPATCHER_CONTEXT DispatcherContext  
);  
```  
  
 **Exception_record**提供指向具有标准 Win64 定义异常记录。  
  
 **EstablisherFrame**是此函数的固定的堆栈分配的基数的地址。  
  
 **ContextRecord**指向 （在异常处理程序的情况下） 在引发异常时的时间或当前的异常上下文"展开"（在终止处理程序的情况下） 的上下文。  
  
 **DispatcherContext**指向此函数的调度程序上下文。 它具有以下定义：  
  
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
  
 **ControlPc**是 RIP 在此函数中的值。 这是一个异常地址或从该处控件离开建立函数的地址。 这是将用于确定控件是否在此函数在某些受保护构造 RIP (例如，一个 __try 适用于块\__finally /\__except 或\__finally /\___identifier)。  
  
 **ImageBase**是映像基映像 （负载地址） 包含此函数，将添加到使用在函数入口的 32 位偏移量和展开以记录相对地址的信息的模块。  
  
 **函数项进行**提供指向 runtime_function 结构的指针函数持有该函数的入口和展开此函数的信息映像基址相对地址。  
  
 **EstablisherFrame**是此函数的固定的堆栈分配的基数的地址。  
  
 **TargetIp**提供指定展开的延续地址可选指令地址。 如果此地址将被忽略**EstablisherFrame**未指定。  
  
 **ContextRecord**指向异常上下文，以供系统异常展开调度/代码。  
  
 **LanguageHandler**指向被调用的特定于语言的语言处理程序例程。  
  
 **HandlerData**指向此函数的特定于语言的处理程序数据。  
  
## <a name="see-also"></a>请参阅  
 [异常处理 (x64)](../build/exception-handling-x64.md)
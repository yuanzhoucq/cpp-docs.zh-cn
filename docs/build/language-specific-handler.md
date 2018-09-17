---
title: 语言特定的处理程序 |Microsoft Docs
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
ms.openlocfilehash: 678f5695523751ebc1ef3c5dba2b63154b21833c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714943"
---
# <a name="language-specific-handler"></a>特定于语言的处理程序

只要设置了标志 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 语言特定的处理程序的相对地址 unwind_info 结构中存在。 如前一部分中所述，语言特定的处理程序称为搜索异常处理程序的一部分或作为展开代码的一部分。 它具有以下原型：

```
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord**提供一个指向具有标准 Win64 定义的异常记录。

**EstablisherFrame**是此函数的固定的堆栈分配的基本地址。

**ContextRecord**指向 （中异常处理程序的情况下） 引发了异常的时间或当前的异常上下文"展开"（在终止处理程序示例） 的上下文。

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

**ControlPc**是 RIP 中此函数的值。 这是异常地址或控制这将建立函数保留的地址。 这是将用于确定控件是否在此函数中的某些受保护构造 RIP (例如，__try 块\__finally /\__except 或\__finally /\___identifier)。

**ImageBase**是映像基映像 （加载地址） 包含此函数中，将添加到函数入口中使用的 32 位偏移量和展开以记录相对地址的信息的模块。

**函数项进行**提供一个指向 runtime_function 结构指针的函数保存该函数的入口和展开此函数的信息基于映像的相对地址。

**EstablisherFrame**是此函数的固定的堆栈分配的基本地址。

**TargetIp**提供了指定展开的继续符地址的可选指令地址。 如果此地址将被忽略**EstablisherFrame**未指定。

**ContextRecord**指向异常上下文，以供系统异常展开调度/代码。

**LanguageHandler**指向被调用的特定于语言的语言处理程序例程。

**HandlerData**指向此函数的特定于语言的处理程序数据。

## <a name="see-also"></a>请参阅

[异常处理 (x64)](../build/exception-handling-x64.md)
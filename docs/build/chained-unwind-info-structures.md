---
title: "链式展开信息结构 | Microsoft Docs"
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
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链式展开信息结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果设置了 UNW\_FLAG\_CHAININFO 标志，则下一个将设置展开信息结构，共享异常处理程序\/链式信息地址字段中包含主展开信息。  下面的代码检索主展开信息，假定 `unwindInfo` 是设置了 UNW\_FLAG\_CHAININFO 标志的结构。  
  
```  
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);  
```  
  
 在两种情况下链式信息十分有用。  首先，它可用于非连续代码段。  由于不需要重复主展开信息中的展开代码数组，因此使用链式信息可减小所需的展开信息的大小。  
  
 还可以使用链接的信息将易失寄存器保存内容分组。  编译器可以延迟保存一些易失寄存器，直到超出函数项 Prolog。  通过在分组代码之前提供函数部分的主展开信息，可对此进行记录，然后通过 Prolog（长度不为零）设置链式信息，其中链式信息中的展开代码反映了非易失寄存器的保存内容。  在这种情况下，展开代码是 UWOP\_SAVE\_NONVOL 的所有实例。  分组是保存非易失寄存器使用推送或修改 RSP 注册通过使用一个额外的内置的堆栈分配不受支持。  
  
 具有 UNW\_FLAG\_CHAININFO 集的 UNWIND\_INFO 项可以包含 RUNTIME\_FUNCTION 项，而 RUNTIME\_FUNCTION 项的 UNWIND\_INFO 项也具有 UNW\_FLAG\_CHAININFO 集（多次紧缩套装）。  最后，链式展开信息指针将到达 UNWIND\_INFO 项（清除了 UNW\_FLAG\_CHAININFO），该项是指向实际过程入口点的主 UNWIND\_INFO 项。  
  
## 请参阅  
 [为异常处理和调试器支持展开数据](../build/unwind-data-for-exception-handling-debugger-support.md)
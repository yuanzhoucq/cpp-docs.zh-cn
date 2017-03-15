---
title: "UNWIND_INFO 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f0aee906-a1b9-44cc-a8ad-463637bd5411
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# UNWIND_INFO 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

展开数据信息结构用于记录函数对堆栈指针的影响以及非易失寄存器在堆栈中的保存位置：  
  
|||  
|-|-|  
|UBYTE: 3|版本|  
|UBYTE: 5|Flags|  
|UBYTE|Prolog 的大小|  
|UBYTE|展开代码的计数|  
|UBYTE: 4|帧寄存器|  
|UBYTE: 4|帧寄存器偏移量（成比例）|  
|USHORT \* n|展开代码数组|  
|variable|可以是下面的形式 \(1\) 或 \(2\)|  
  
 \(1\) 异常处理程序  
  
|||  
|-|-|  
|ULONG|异常处理程序的地址|  
|variable|语言特定处理程序数据（可选）|  
  
 \(2\) 绑定展开信息  
  
|||  
|-|-|  
|ULONG|函数起始地址|  
|ULONG|函数结束地址|  
|ULONG|展开信息地址|  
  
 UNWIND\_INFO 结构在内存中必须按 DWORD 对齐。  每个字段的含义如下：  
  
 **版本**  
 展开数据的版本号，当前为 1。  
  
 **Flags**  
 当前定义了三个标志：  
  
 UNW\_FLAG\_EHANDLER 该函数有应调用，如果找到函数时需要检查异常的异常处理程序。  
  
 UNW\_FLAG\_UHANDLER 该函数有应调用，当展开异常时的一终止处理程序。  
  
 这展开信息结构的 UNW\_FLAG\_CHAININFO 不是主一个程序的。  链式展开信息项是前面的 RUNTIME\_FUNCTION 项的内容。  有关链式展开信息结构的说明，请参见下面的文本。  如果设置了此标志，则必须清除 UNW\_FLAG\_EHANDLER 和 UNW\_FLAG\_UHANDLER 标志。  此外，帧寄存器和固定堆栈分配字段必须与主展开信息中的对应字段具有相同的值。  
  
 **Prolog 的大小**  
 函数 Prolog 的长度（以字节为单位）。  
  
 **展开代码的计数**  
 这是展开代码数组中的槽数。  请注意，有些展开代码（例如 UWOP\_SAVE\_NONVOL）要求数组中有多个槽。  
  
 **帧寄存器**  
 如果为非零值，则函数使用帧指针，并且此字段是作为帧指针使用的非易失寄存器的个数，UNWIND\_CODE 节点的操作信息字段使用相同的编码。  
  
 **帧寄存器偏移量（成比例）**  
 如果帧寄存器字段为非零值，则表示建立 FP reg 时应用于它的距 RSP 的成比例的偏移量。  将实际的 FP reg 设置为“RSP \+ 16 \* 此数字”，并允许偏移量在 0 到 240 之间。  对于动态堆栈帧来说，这一设置使 FP reg 指向本地堆栈分配的中间，从而可以通过较短的指令获得更好的代码密度（多个指令可以使用 8 位有符号偏移量格式）。  
  
 **展开代码数组**  
 这是一个由项组成的数组，它说明 Prolog 对非易失寄存器和 RSP 的影响。  有关各项的含义，请参见 UNWIND\_CODE 的相关章节。  为了对齐，此数组的项数始终是偶数，最后一项可能不使用（在此情况下，数组长度将比展开代码字段的计数所指示的值大 1）。  
  
 **异常处理程序的地址**  
 这是一个与图像相关的指针，指向函数的语言特定异常\/终止处理程序（如果清除了 UNW\_FLAG\_CHAININFO 标志，并设置了 UNW\_FLAG\_EHANDLER 或 UNW\_FLAG\_UHANDLER 两个标志中的一个）。  
  
 **语言特定处理程序数据**  
 这是函数的语言特定异常处理程序数据。  此数据的格式未指定，完全由使用的特定异常处理程序决定。  
  
 **链式展开信息**  
 如果设置了 UNW\_FLAG\_CHAININFO 标志，则 UNWIND\_INFO 结构以三个 UWORD 结束。  这些 UWORD 表示链式展开函数的 RUNTIME\_FUNCTION 信息。  
  
## 请参阅  
 [为异常处理和调试器支持展开数据](../build/unwind-data-for-exception-handling-debugger-support.md)